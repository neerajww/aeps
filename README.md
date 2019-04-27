# Auditory Evoked Potentials (AEPs)
This is a write-up to contain and share my understanding of auditory evoked potentials and its application gain understanding of speech perception and cognition.

The human brain is a fascinating signal processing system. Signals are relayed into brain regions from various sensory organs, like the eyes, ear, skin, nose etc., and brain has to respond - often, in fraction of a second. It is true that every organ in human body is incredible in its built and operation, and you may ask what's special about the brain which has captured the imaginatiton of a large number of 21st century researchers? Well, most of the sensory organs have been anatomically well understood since 18-19th century, and we have been able to argue about "the how" of their working as peripheral signal processing units. Example, we know the internal, physically segregatable structure of ear in a lot detail, like, the basilar membrane, organ of corti, malleus, incus and stapes, and also we know how these structures transform air pressure variations into electrical impulses synapsed to the auditory nerve fibres. Similar insights also exist for eyes. However, what happens when it comes to our understanding of brain? Surprisingly, insights on the anatomical details of brain started to be noticed only in the early 20th century. Further, what was striking is that most of the brain was found to be composed of a lump tissues - gray and white matter, and segregating it further into distict physical hasn't been as straight forward as other organs of human body. It is only in the mid- and late- 20th century that we have been able to figure out the brain's topographical map - linking where the sensory organs of the human body are mapped onto the brain's anatomy. However, the unique contribution of different brain areas to behavior is yet to be elucidated. It is only in 1920s that it was found that -  neurons serrve as discrete processing units in the brain, and these neurons interconnect to form networks in complicated ways which is responsible for behavior. Visualizing and experimenting with neurons, and their networks was not possible in the 20th century. With the development of novel engineering techniques to capture brain signals, it has been possible to now probe the behavioral response of brain.


> Electro-encephalo-graphy (EEG) is one such technique. When it comes to capture brain signals a key requirement is the method should be non-invasive and EEG satisfies that. In EEG, electrodes are embedded on a cap, and on wearing this cap a contact is established between the scalp and the electrodes. On wiring the electrodes to an oscilloscope we can see voltage fluctuations and that's the EEG signal. From where does this arise? The human brain consists of 100 billion nerve cells that are continuously active in communicating with each other. Each nerve cells synapses with 1000 other nerve cells in this communication. This communication is established by flow of ions within and across the cells, resulting in continuous voltage fluctiations across the brain cells. This voltage fluction happens all the time - while you are ready this, or sleeping - as your brain is always doing something - processing/storage/retrieval. The summed up voltage fluctuations (derived from the billions of neurons) across time and its spatial distribution across scalp is what is measured by the EEG electrodes. Capturing EEG signals is not a recent idea (dating back to 1890s) but its usability as a technique to capture brain's response has increased over time. This is due to - i. use of more number of electrodes, ii. better electronics enabling better capture of signals from the scalp, iii. new computational techniques for data analysis, and iv. developments in brain understanding derived from other techniques. 

In this tutorial, I will focus on recording EEG signals from the point-of-view of gaining insight into how brain processes speech. It may be true that recording electrodes placed over temporal lobes, that is, between the ears and halfway up to the midline of the head, are the best position to record changes specific to auditory cortex. However, often the electrodes near the vertex of head are more informative, these pick up activity from both hemispheres, including temporal lobe activity and that from attention centers in the frontal cortex. Activity from deeper brain regions, such as the brainstem, is also recorded, although with much smaller amplitude. Here, I will be using a 32 channel electrode cap for EEG recording. Having, more electrodes gives the flexibility of chosing the most informative electrode post-recording and while data analysis.

### What are AEPs?
"During stimulation with sound, the EEG undergoes typical changes that are correlated in a time-locked fashion to changes in sound; that is, they occur more or less after a fixed interval and with a similar waveform after the change in sound. These changes are called auditory evoked potentials (AEPs)." - J. Eggermont. Extracting the AEPs from EEG requires presenting the same stimulus over several trials and averaging the EEG waveforms over these trials. The averaging assumes that given the stimulus, AEP is always the same waveform, whereas the background EEG changes more randomly (relatively).
What changes in sound evoke AEPs? 
- for tonal stimuli, change can be in ampltude or frequency
- for complex stimuli, it can be a phoneme, word, or surprise (un-) known word in the context of a sentence
- still open for discovery!

What is the peak latency between change in sound and peak in AEPs?
- ranges between 1 ms to 500 ms.
This implies that even after 500 ms the brain processing is still time-locked to the stimulus. Usually, a change in sound is detected within 50 ms in the peripheral auditory pathways however, detection of changes in complex stimuli (like incorrect word detection in sentence) can take longer duration as this detection requires decision from higher auditory pathways.

> AEPs just don't only capture response of central auditory pathways but the response of the auditory pathway from peripheral to central. The classification of AEPs is done based on latencies. Early peaks in the AEPs are associated with peripheral and brainstem response, and later peaks are associated with cortical response. For example, see the below illustration taken from Auditory Evoked Potentials: Basic Principles and clinical application, Burkard, Don, and Eggermont.

![](https://raw.githubusercontent.com/neerajww/aeps/master/media/images/illustration_aeps.jpg =250x500 "Temporal evolution of an AEP signal")

[logo]: https://raw.githubusercontent.com/neerajww/aeps/master/media/images/illustration_aeps.jpg "Logo Title Text 2"





