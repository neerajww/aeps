# Capturing and Pre-processing EEG signals
I have analyzed speech and audio signals in my research. They are interesting as - you can quickly record them with a mic, transport to a computer, start processing using different coding languages, and play them back to understand how the mathematical operations altered the physical perception of the original signal. Further, these things apart, speech and audio signals have a time-varying spectrum, and it is amazing how the human brain detects, perceives and responds to this spectrum - like, in a converstation, and enjoying music. Analyzing time-varying spectrum is mathematically active area of research and has engineering applications waiting to be solved, and somehow our brain seems to be good at this problem. How brain does this is a mystery and electro-enchephalo-graphy (EEG) is one few other possible techniques to analyze this.

## How is EEG Captured?
Enchephalo means "relating to brain" and graphy means "descriptive science". EEG refers to describing the electrical activity in brain. Unlike speech signal which comes out through the mouth and hence, a single sensor (the microphone) is often enough to record it, the electrical activity in brain is ditributed over a volume (shown in the below figure).
<img src="https://github.com/neerajww/aeps/blob/master/media/images/illstration_brain_areas.png" width="40%">

Hence, it makes sense to use multiple sensors to record EEG. These sensors are clipped to a cap worn by the subject. A key feature of EEG technique is the non-invasiveness, the electrodes need to only have a electrical conductivity with the scalp and not pierce into the scalp. Hairs on the scalp may inhibit the conductivity and to avoid this layer of conducting gel is put between a localized region of the scalp and each electrode. To see the EEG caps [click here](https://www.google.com/search?q=eeg+cap&source=lnms&tbm=isch&sa=X&ved=0ahUKEwjI376Y0vPhAhXMmuAKHamOCm4Q_AUIDygC&biw=2133&bih=1032#imgrc=_). These caps come in different configurations of N (number of electrodes), such as 32, 64 128, and 256 etc. More number of electrodes help in better capture of spatial distribution of brain activity. In addition to the N electrodes, the cap also houses 1 (or a comination of two) electrode which serve as reference to measure the potential variations in the rest of the N electrodes. An experimental recording setup is shown below.

<img src="https://github.com/neerajww/aeps/blob/master/media/images/illustration_eeg_expt.png" width="60%">
The recorded signal is composed of

- N channels containing time-series data 
- Sampled at Fs Hz (usually between 512-2048 Hz)
- Label information of each channel
- One event-trigger channel specifying the stimulus onset instants

This is bundled in a single file, with an extension such as .bdf for data recorded using Biosemi system.

## Example Experimental Setup
Here, I will present EEG data corresponding to a listening experiment of duration close to 114 mins. The pre-processing steps ares often independent of the underlying experiment. For now, we will go ahead without getting into the details of the task in the experiment. The only details we need is that the experiment has several trials, and the event-trigger channel contains the information about each trial (like trigger instant and task label/code corresponding to each trigger instant).

## Pre-processing pipeline
I will describe a sample processing pipeline. The coding language is Matlab based and I will be using the [EEGLAB library package](https://sccn.ucsd.edu/eeglab/index.php) to avoid re-creating some of the widely used function routines. There is no rocket science in any of these steps and this tutorial is designed to get things started! once you have the EEG recordings with you.

1. Download the EEGLAB package: [click here](https://github.com/sccn/eeglab)
2. Load data
```
bdf_fname = ['sub_01_eeg32.bdf']; 
EEG = pop_biosig(bdf_fname);
```
This file contain 32 EEG Cap channels + 2 mastoids channel + 2 EOG channels. The 4 non-cap channels are named EX1, EX2, EX3, and EX4, respectively.

3. Load the channel location data
```
EEG_proc = pop_editset(EEG_proc, 'chanlocs','biosemi_cap_32_MAS_2_EOG_2.locs');
EEG = eeg_checkset( EEG );
```
4. Re-sample
```
EEG = pop_resample( EEG, 256);
EEG = eeg_checkset( EEG );
```    
5. Filter the data
```
EEG = pop_eegfiltnew(EEG, 2,45,8448,0,[],1);
```
5. Copy data to contain only the cap electrode channels
```
EEG_proc = pop_select( EEG,'nochannel',{'EXG1','EXG2','EXG3','EXG4'});
```
6. Detect and remove bad time segments and bad channels. I am using the clean_raw data plugin from [click here](https://github.com/sccn/clean_rawdata).
```
EEGorig = EEG_proc;
EEG_proc = clean_rawdata(EEG_proc, 5, -1, 0.85, 4, 20, 0.25);
```
7. Re-create data in bad channels by interpolating data from nearby channels
```
EEG_proc = pop_interp(EEG_proc, EEGorig.chanlocs, 'spherical');
```
8. Reference each channel to an all channel average reference
```
EEG_proc = pop_reref(EEG_proc, []);
```
9. Append the 2 EOG channels to the dataset after removing the bad time segments using the time mask from Step 6
```
EEG_proc.nbchan = EEG_proc.nbchan+2;
EEG_proc.data(EEG_proc.nbchan-1,:) = EEG.data(35,EEG_proc.etc.clean_sample_mask==1);
EEG_proc.data(EEG_proc.nbchan,:) = EEG.data(36,EEG_proc.etc.clean_sample_mask==1);
EEG_proc.chanlocs(1,EEG_proc.nbchan-1).labels = 'EXG3';
EEG_proc.chanlocs(1,EEG_proc.nbchan).labels = 'EXG4';
EEG_proc = eeg_checkset( EEG_proc );
EEG_proc = pop_editset(EEG_proc, 'chanlocs','biosemi_cap_32_EOG_2.locs');
EEG_proc = eeg_checkset( EEG_proc );
```
10. Extract epochs by specifying event labels, time-window around onset of each event, and removing baseline using an average obtained from a time-window prior to event onset. 
```
EEG_proc = pop_epoch( EEG_proc, {  '11'  '12'}, [-0.5 2]);
EEG_proc = eeg_checkset( EEG_proc );
EEG_proc = pop_rmbase( EEG_proc, [-500    0]);
EEG_proc = eeg_checkset( EEG_proc );
```
11. Apply ICA to EEG_proc: The commonly used ICA implementation is the runica. However, this is very slow. There is binary file available for the same technique which is 12x fatser. It can be obtained from [click here](https://sccn.ucsd.edu/wiki/Binica) and the instruction there will do the needful to make it running.
```
EEG_proc = pop_runica(EEG_proc,'binica');
EEG_proc.setname = 01;
EEG_proc = pop_saveset(EEG_proc, 'filename', [EEG_proc.setname '.set'], 'filepath', './');
```
It will output and store two files: 01.set and 01.ftd. The eeglab keeps everything packed in the EEG structure (the .set file; the eeg signal is usually kept as float32 in a separate .fdt file). 

12. Visualize the contributions of the estimated ICA components: The number of ICA components, L, can be less than number of channels. This happens when some of the channels are highly correlated. 
```
EEG = pop_loadset('filename','01.set','filepath','./');
EEG = eeg_checkset( EEG );
pop_selectcomps(EEG, [1:L] );
```

13. Remove the components corresponding to artifact inducing sources

14. Project the data back to obtain the artifact removed channel data

15. Visualize the ERPs
