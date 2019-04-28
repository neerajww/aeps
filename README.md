# A short tutorial on Auditory Evoked Potentials (AEPs)
This is a write-up to contain and share my understanding of auditory evoked potentials and its application gain understanding of speech perception and cognition.

The **human brain** is a fascinating signal processing system. Signals are relayed into brain regions from various sensory organs, like the eyes, ear, skin, nose etc., and brain has to respond - often, in fraction of a second. It is true that every organ in human body is incredible in its built and operation, and you may ask what's special about the brain which has captured the interest of a large number of 21st century researchers? Well, most of the sensory organs have been anatomically well understood since 18-19th century, and we have been able to argue about "the how" of their working as peripheral signal processing units. Example, we know the internal, physically segregatable structure of ear in a lot detail, like, the basilar membrane, organ of corti, malleus, incus and stapes, and also we know how these structures transform air pressure variations into electrical impulses synapsed to the auditory nerve fibres. Similar insights also exist for eyes. However, what happens when it comes to our understanding of brain? Surprisingly, insights on the anatomical details of brain started to be noticed only in the early 20th century. Further, what was striking is that most of the brain was found to be composed of a lump tissues - gray and white matter, and segregating it further into distict physical hasn't been as straight forward as other organs of human body. It is only in the mid- and late- 20th century that we have been able to figure out the brain's topographical map - linking where the sensory organs of the human body are mapped onto the brain's anatomy. However, the unique contribution of different brain areas to behavior is yet to be elucidated. It is only in 1920s that it was found that -  neurons serrve as discrete processing units in the brain, and these neurons interconnect to form networks in complicated ways which is responsible for behavior. Visualizing and experimenting with neurons, and their networks was not possible in the 20th century. With the development of novel engineering techniques to capture brain signals, it has been possible to now probe the behavioral response of brain.


> Electro-encephalo-graphy (EEG) is one such technique. When it comes to capture brain signals a key requirement is the method should be non-invasive and EEG satisfies that. In EEG, electrodes are embedded on a cap, and on wearing this cap a contact is established between the scalp and the electrodes. On wiring the electrodes to an oscilloscope we can see voltage fluctuations and that's the EEG signal. From where does this arise? The human brain consists of 100 billion nerve cells that are continuously active in communicating with each other. Each nerve cells synapses with 1000 other nerve cells in this communication. This communication is established by flow of ions within and across the cells, resulting in continuous voltage fluctiations across the brain cells. This voltage fluction happens all the time - while you are ready this, or sleeping - as your brain is always doing something - processing/storage/retrieval. The summed up voltage fluctuations (derived from the billions of neurons) across time and its spatial distribution across scalp is what is measured by the EEG electrodes. Capturing EEG signals is not a recent idea (dating back to 1890s) but its usability as a technique to capture brain's response has increased over time. This is due to - i. use of more number of electrodes, ii. better electronics enabling better capture of signals from the scalp, iii. new computational techniques for data analysis, and iv. developments in brain understanding derived from other techniques. 

In this tutorial, I will focus on recording EEG signals from the point-of-view of gaining insight into how brain processes speech. It may be true that recording electrodes placed over temporal lobes, that is, between the ears and halfway up to the midline of the head, are the best position to record changes specific to auditory cortex. However, often the electrodes near the vertex of head are more informative, these pick up activity from both hemispheres, including temporal lobe activity and that from attention centers in the frontal cortex. Activity from deeper brain regions, such as the brainstem, is also recorded, although with much smaller amplitude. AEPs are derived from EEG recordings.

### What are AEPs?
"During stimulation with sound, the EEG undergoes typical changes that are correlated in a time-locked fashion to changes in sound; that is, they occur more or less after a fixed interval and with a similar waveform after the change in sound. These changes are called auditory evoked potentials (AEPs)." - J. Eggermont. Extracting the AEPs from EEG requires presenting the same stimulus over several trials and averaging the EEG waveforms over these trials. The averaging assumes that given the stimulus, AEP is always the same waveform, whereas the background EEG changes more randomly (relatively).
What changes in sound evoke AEPs? 
- for tonal stimuli, change can be in ampltude or frequency
- for complex stimuli, it can be a phoneme, word, or surprise (un-) known word in the context of a sentence
- still open for discovery!

What is the peak latency between change in sound and peak in AEPs?
- ranges between 1 ms to 500 ms.
This implies that even after 500 ms the brain processing is still time-locked to the stimulus. Usually, a change in sound is detected within 50 ms in the peripheral auditory pathways however, detection of changes in complex stimuli (like incorrect word detection in sentence) can take longer duration as this detection requires decision from higher auditory pathways.

> AEPs just don't only capture response of central auditory pathways but the response of the auditory pathway from peripheral to central. The classification of AEPs is done based on latencies. Early peaks in the AEPs are associated with peripheral and brainstem response, and later peaks are associated with cortical response. To see an illustration on the temporal evolution of AEPs and its association with the auditory pathways [click here](https://raw.githubusercontent.com/neerajww/aeps/master/media/images/illustration_aeps.jpg).

### What causes AEPs?
AEPs are a result of a summation of electro-chemical activity in a population of neurons. A neuron functions via two key types of electrical activities:
- Action potentials
- Postsynaptic potentials
> A very good and quick introduction to voltage potentials in neurons is provided in [these videos](https://www.khanacademy.org/science/health-and-medicine/nervous-system-and-sensory-infor) at Khan Academy.

**Action potentials** are discrete voltage spikes that travel along a neuron’s axon to the axon terminals, where they final cause release of neurotransmitters into the external medium. Surface electrodes cannot generally detect action potentials due to two reasons: short timing nature and non-aligned orientation of axons in a population of neurons. Action potentials can only be recorded if individual neurons fire at exactly the same time causing the voltages of the action potentials to sum. However, as neurons rarely fire at exactly the same time and also because axons are relatively random orientated, action potentials generally cancel each other out when it comes to its detection at scalp. Action potentials have a very short duration, about 1 ms and travel very fast, 1-100 m/s.

**Postsynaptic Potentials (PSPs)** arise when neurotransmitters bind to receptors on the membrane of the postsynaptic cell, causing ion channels to open or close and leading to a graded change in potential across the cell membrane. PSPs are longer in duration than action potentials, lasting up to tens or even hundreds of milliseconds. They are generally confined to the dendrites of a neuron and occur instantaneously. As dendrites are oriented in parallel along the cortical sheet, these characteristics of PSPs mean that they can summate and are, thus, thought to largely contribute to the signal measured by EEG.

> AEPs does not measure action potentials, but rather postsynaptic potentials summed from a large population of neurons sharing timing of PSPs and having similar orientation of dendrites. These two features in a population of neurons are shared only at few places in the auditory pathways, namely, around cochlear nucleus and auditory cortex. To see an illustration of this [click here](https://github.com/neerajww/aeps/blob/master/media/images/illustration_auditory_pathways.png). It can be noted that the late peaks in AEPs are higher in amplutude and also low in frequency. The higher amplitude is due to its association with the pyramidal neurons in cortical areas. These neurons are extremely well aligned and huge in number compared to those in brainstem.

### What does AEP peaks signify?
To the least AEP peaks signify detection of "sound change" at the specific center in the auditory pathway.
- This is inspired the usage of early/mid latency AEPs for evaluating hearing impairments in new born babies. The signal is more specifically referred to as the auditory brain stem response. More interestingly, this does not require the baby to be awake and can be obtained quite fast. To know more [click here] (https://en.wikipedia.org/wiki/Auditory_brainstem_response)
- The cortical AEPs (CAEPs) have inspired analysing behavior. The generally occur between 50-300 ms following stimulus onset; and are referred by P1-N1-P2 complex and the mismatch negativity (MMN). This is an active are of research, and there is an expectation of its application for monitoring attention while listening to natural converstations. While early latency AEPs (like ABRs) help in analyzing threshold responses, CAEPs are useful for analyzing suprathreshold responses (such as descrimination between two sounds). These are also referred to as event-related potential (ERPs) as the are studied with respect to detection of an acoustic event in the stimulus.

### Summary
> After going through the above short-tutorial, I hope to have conveyed the following:
- studying brain at the intersection of biology, electrical engineering, computational modeling, and human behavior (psychology) holds many challenges and fruits.
- AEPs are like signature of neural responses to processing specific changes in sounds. This signature can be extracted by averaging several trials.
- AEPs correspond to a summation of postsynaptic potentials from a large population of neurons.
- AEPs are generated from specific locations in the auditory pathway.

Going beyond this, if you are also interested to know more on processing associated with analyzing EEG data [click here](https://github.com/neerajww/aeps/edit/master/docs/prep_eeg.md).


