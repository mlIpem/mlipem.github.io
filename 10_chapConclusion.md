# Conclusion {#chapConclusion}

In this book, two parallel pathways mutually support each other: theory and modelling.
We briefly overview our main findings.

## Contribution to theory

Music interaction was primarily studied from the viewpoint of timing, in dancers, violin players and finger tappers.
Timing clearly involves subconscious processing, such as *sensorimotor adaptation* to structure in dancing, *sensorimotor feedback* based on parallax and modality effectiveness, and last but not least, *entrainment* or mutual adaptation in finger tapping interactions. 

While these phenomena can be related to predictive processing, embodiment and expression in individual subjects, it seems that reductionist understanding is insufficient. In order understand music interaction, we also need a holistic understanding at the level of a dynamic system of multiple interacting units. We showed that timing-related emerging effects of these interacting units can be based on phase flow among interacting units.  

However, we also assume that states emerging from the embodied interactions, affect brain processing, plausibly related to dynamic interactions between brain regions. We didn't address it in this book but it's a super-cool assumption, albeit speculative, that in fact the brain itself engages interactions among neurons that augment each other. Another super-cool assumption is that certain interaction states have an empowering effect on the individual. 

Our main hypothesis about self-augmented interaction states is in fact an overall dynamic concept that covers these assumptions. At the end of this book, we cannot claim to have proven it, but evidence from our explorations is not against the hypothesis. In fact, evidence from our explorations support the hypothesis. For example, entrainment indeed facilitates collaboration and makes it easier to co-regulate actions in view of a common goal.

However, a major difficulty in studying self-augmented interaction states is concerned with generating these states in a laboratory setting. This is a challenge for future research and clever paradigms are needed to generate those interaction states under controlled conditions. 

## Contribution to modelling

While we focused on behavior and timing,  we explored the use of different modelling techniques based on regression, under the umbrella of a global Bayesian epistemologic paradigm. 

We showed that *curve fitting* is an interesting modelling technique for capturing an assumed underlying process. In regression based on smooths, the data are expanded into a larger space that is defined by functions (splines) and the modelling fits the data to combinations of these functions, to obtain the weights of these functions. In regression based on a dynamic system, we fit the data with functions generated by a dynamic system, to obtain parameters that represent the functions. This approach is more powerful because the parameters express causal components of understanding. 

A word should be said about datasets in modern musicology.
Datasets contain data from *multiple modalities*, such as auditory, visual, tactile, haptic sensing, as well as from body movement, brain activity, and questionnaires.
The data come from *different media*, such
as from recording devices for audio and video, from motion capture systems, from EEG or other brain scan devices.

Furthermore, the data are *high-dimensional*. Apart from having a high *resolution* in time and space -- we speak about milliseconds and millimeter ranges -- a modality may involve different markers or sensors: a full-body motion tracking requires easily >30 markers.  A EEG cap may have 64 electrodes. Audio can be measured with multiple microphones and so on. The fine-resolution spatiotemporal data thus get multiplied by the number of markers and/or sensors. And they require perfect *synchronization* over the different measuring devices involved. 

## Our limitations

This book is a modest attempt to explore music interactions. Having reached the end, we feel that we just started understanding little pieces, and even those little pieces of understanding suffer from limitations.

Firstly, as our focus primarily revolved around behavioral data analysis using regression techniques, we neglected the promising advancements in neurobiology and neuroscience, as well as the availability of more high-dimensional data (including EEG and all types of body sensing). 

Secondly, by controlling variables during data collection, we potentially compromised the ecological validity of music interactions. While the use of specific technologies for augmented reality (e.g. hololens), and haptic connection (e.g. exoskeletons) allow for unique control of the action-perception loops governing interactions, we have been confronted with the question who self-augmented interaction states can be controlled, and even more important, perhaps, how we can be sure that a human is really experiencing a self-augmented interaction state. Apparently, there is a lot of variability in how humans engage in mutual interactions, as facilitated by music.

Lastly, we did not provide an exhaustive account of statistical modeling techniques. Rather, we focused on a selected range of methods, primarily regression-based, that are deemed relevant for understanding data from music interactions. We hope that listeners can appreciate the fact that music research deals with small datasets, subtle effect sizes, and considerable uncertainty stemming from the complexities of natural music interaction contexts.


## Outlook

Our exploration of music interaction with R, mainly based on regression modelling, turned out to be a useful for connecting theory with data. 
Overall, the insights obtained from these explorations suggest that timing is a key feature in music interaction. As we draw this discourse to a close, it is worth reiterating the immense challenge in better understanding the dynamics that underlies music-based transformative powers.