# Capturing and Pre-processing EEG signals
I have analyzed speech and audio signals in my research. They are interesting as - you can quickly record them with a mic, transport to a computer, start processing using different coding languages, and play them back to understand how the mathematical operations altered the physical perception of the original signal. Further, these things apart, speech and audio signals have a time-varying spectrum, and it is amazing how the human brain detects, perceives and responds to this spectrum - like, in a converstation, and enjoying music. Analyzing time-varying spectrum is mathematically active area of research and has engineering applications waiting to be solved, and somehow our brain seems to be good at this problem. How brain does this is a mystery and electro-enchephalo-graphy (EEG) is one few other possible techniques to analyze this.

## How is EEG recorded?
Enchephalo means "relating to brain" and graphy means "descriptive science". EEG refers to describing the electrical activity in brain. Unlike speech signal which comes out through the mouth and hence, a single sensor (the microphone) is often enough to record it, the electrical activity in brain is ditributed over a volume (shown in the below figure).
<img src="https://github.com/neerajww/aeps/blob/master/media/images/illstration_brain_areas.png" width="40%">

Hence, it makes sense to use multiple sensors to record EEG. These sensors are clipped to a cap worn by the subject. A key feature of EEG technique is the non-invasiveness, the electrodes need to only have a electrical conductivity with the scalp and not pierce into the scalp. Hairs on the scalp may inhibit the conductivity and to avoid this layer of conducting gel is put between a localized region of the scalp and each electrode. To see the EEG caps [click here](https://www.google.com/search?q=eeg+cap&source=lnms&tbm=isch&sa=X&ved=0ahUKEwjI376Y0vPhAhXMmuAKHamOCm4Q_AUIDygC&biw=2133&bih=1032#imgrc=_). These caps come in different configurations of N (number of electrodes), such as 32, 64 128, and 256 etc. More number of electrodes help in better capture of spatial distribution of brain activity. In addition to the N electrodes, the cap also houses 1 (or a comination of two) electrode which serve as reference to measure the potential variations in the rest of the N electrodes. An experimental recording setup is shown below.

<img src="https://github.com/neerajww/aeps/blob/master/media/images/illustration_eeg_expt.png" width="60%">
The recorded signal is composed of
- N channels
- Sampled at Fs Hz (usually between 512-2048 Hz)
- One event-trigger channel specifying the stimulus onset instants
All this is bundled in a single file, with an extension such as .bdf for data recorded using Biosemi system.



