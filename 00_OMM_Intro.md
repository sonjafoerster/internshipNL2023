# Of Mice and Men - Or: How I learned to read spikes. An Introduction

</br>

<img src="images/mouse.png"  width="100%"> 

_Image by Robin Haak, Netherlands Institute for Neuroscience (NiN), Amsterdam, NL_  
  
</br>

In spring 2023, I had the opportunity to do my internship as part of the [Resarch Master program Cognitive Neuroscience](https://www.universiteitleiden.nl/en/education/study-programmes/master/psychology-research/cognitive-neuroscience-research "https://www.universiteitleiden.nl/en/education/study-programmes/master/psychology-research/cognitive-neuroscience-research") at Dr Anne Urai’s Cognitive, computational and systems neuroscience - short: [CoCoSys lab](https://anneurai.net/ "https://anneurai.net/") at Leiden University in the Netherlands.
  
Anne is a very skilled and pationate researcher investigating “how the brain transforms sensory information into useful decisions, and how such decisions change with experience and internal states.” (CoCoSys lab). Age could be considered one of those “internal states”, with changes in neural variability, along with changes in other brain features. To investigate age-related neural changes on cellular and population level, Anne recorded electrophysiology data in aged mice during her postdoc times with the [International Brain Laboratory (IBL)](https://internationalbrainlab.com/#home "https://internationalbrainlab.com/#home"). She used Neuropixels probes to record from multiple brain regions at a time while the mice conducted a perceptual decision making task. Most of the preprocessing steps (e.g., spike sorting) were already completed for these data when I started my internship in February 2023. Just one step was missing for some files to make the data ready for anaylsese: the ephys alignments. That is, to align electrophysiology features of a recording to an anatomical histology reference (the [Allen adult mouse brain atlas](http://atlas.brain-map.org/atlas?atlas=602630314#atlas=602630314&structure=8&resolution=16.00&x=5700.845703125&y=4000.3232421875&zoom=-3&plate=576989980 "http://atlas.brain-map.org/atlas?atlas=602630314#atlas=602630314&structure=8&resolution=16.00&x=5700.845703125&y=4000.3232421875&zoom=-3&plate=576989980")) to allow for reasonable alignment of the recording channels along the probe trajectory. This is important since mouse brains might be smaller or larger, or slightly differ in some structural landmarks. Those ephys alignments are therefore a crucial prerequisite to ensure that subsequent analyses compare apples with apples, or, let’s say, spike count variability in a given region of one mouse with the spike count variability in exactly that same region in another mouse.
  
So, this made then the core of my internship: do the ephys alignments for the aged mice sessions recorded from the so-called _repeated site_ (IBL verbiage, referring to the brain regions involved in the [IBL reproducability study](https://www.biorxiv.org/content/10.1101/2022.05.09.491042v3 "https://www.biorxiv.org/content/10.1101/2022.05.09.491042v3")): Visual Area A (VISa); Hippocampal Field CA1; Dentate Gyrus (DG); Lateral Posterior nucleus of the thalamus (LP); Posterior nucleus of the thalamus (PO). 

</br>

_Figure 1. The regions of the mouse brain comprising the IBL repeated site, and probe trajectory projected onto a coronal view of the Allen adult mouse brain atlas. (Source: [IBL reproducability paper](https://www.biorxiv.org/content/10.1101/2022.05.09.491042v3 "https://www.biorxiv.org/content/10.1101/2022.05.09.491042v3"))_  
<img src="images/histmapAllen.png"  width="7%"><img src="images/histsliceAllen.png" width="52%">

</br>

The following sections are a personal reflection on how I dove into the mystery of ephys features and spiking patterns related to the mouse brain anatomy. It consists of three parts:
 
- How I came to terms with the [IBL ephys alignment GUI](https://github.com/sonjafoerster/internshipNL2023/blob/main/01_OMM_Part_I.md)
- A personal account of my biggest learnings in the [Overall approach to ephys alignments](https://github.com/sonjafoerster/internshipNL2023/blob/main/02_OMM_Part_II.md)
- A somewhat more content-focused account of [Common ephys features in the mouse brain (IBL repeated site)](https://github.com/sonjafoerster/internshipNL2023/blob/main/03_OMM_Part_III.md) including my personal logbook of sanity checks and navigating the IBL ephys GUI.

</br>

<<<<<<< HEAD
From October 2023 through January 2024, I continued the above work as a research assistant (RA) at Anne's lab in what we came to call the "non-repeated site"-regions. These are Anne's recordings from aged mice in other regions than those listed above under _repeated site_. Most of these trajectories recorded from more frontal regions as well as several striatal nuclei relevant for integration of visual, motor, and decision-making activity. As part of my RA, I prepared a little introduction to ephys alignments for one of our lab meetings. In case you're interested, here are the [slides](https://docs.google.com/viewer?url=https://github.com/sonjafoerster/internshipNL2023/blob/main/images/Intro_to_ephys_alignments_IBL_GUI_public.pdf).
=======
From October 2023 through January 2024, I continued the above work as a research assistant (RA) at Anne's lab in what we came to call the "non-repeated site"-regions. These are Anne's recordings from aged mice in other regions than those listed above under _repeated site_. Most of these trajectories recorded from more frontal regions as well as several striatal nuclei relevant for integration of visual, motor, and decision-making activity. As part of my RA, I prepared a little introduction to ephys alignments for one of our lab meetings. In case you're interested, here are the [slides](https://github.com/sonjafoerster/internshipNL2023/blob/main/images/Intro_to_ephys_alignments_IBL_GUI_public.pdf#:~:text=images-,Intro_to_ephys_alignments_IBL_GUI_public,-.pdf).
>>>>>>> f7da095332bd3aa75ad7f2ffefcc1477931b42bb

</br>

By the way, if you’re interested in Anne’s research topics and [project ideas, have a look at her wiki page](https://anne-urai.github.io/lab_wiki/ProjectIdeas.html "https://anne-urai.github.io/lab_wiki/ProjectIdeas.html") and get in contact with her!

</br>

* * *
# Documentation of my alignment activities
Access for authorised folks only.
- [Overview spreadsheet](https://docs.google.com/spreadsheets/d/1Z6BIn8-febzvsmEHCao1rWnMz3n8eqJDbe5CdaDBW6Y/edit#gid=0 "https://docs.google.com/spreadsheets/d/1Z6BIn8-febzvsmEHCao1rWnMz3n8eqJDbe5CdaDBW6Y/edit#gid=0") with alignments I worked on
- [Meeting minutes](https://docs.google.com/document/d/1kSeMpFLyE7b1jlhkMHSh6eXPtOSA1Z53BPmDKWNYOgQ/edit#heading=h.3026quwoznbh "https://docs.google.com/document/d/1kSeMpFLyE7b1jlhkMHSh6eXPtOSA1Z53BPmDKWNYOgQ/edit#heading=h.3026quwoznbh") alignment meeting with Anup on 9 May 2023
- All files, including screenshots of tissue damage and potential noise artifacts are stored in this [gdrive folder](https://drive.google.com/drive/folders/1hTUZBVab2xnZGjZVqpY_9uH0P3CpDu8f "https://drive.google.com/drive/folders/1hTUZBVab2xnZGjZVqpY_9uH0P3CpDu8f")
  
</br>

* * *
# References
- [Anne’s github aged mice](https://github.com/anne-urai/mouse_aging "https://github.com/anne-urai/mouse_aging") project
- [CoCoSys lab](https://anneurai.net/ "https://anneurai.net/") home
- [Anne’s project ideas](https://anne-urai.github.io/lab_wiki/ProjectIdeas.html "https://anne-urai.github.io/lab_wiki/ProjectIdeas.html")
- [International Brain Laboratory](https://nationalbrainlab.com/#home "https://nationalbrainlab.com/#home") - IBL
- [IBL ephysatlas](https://atlas.internationalbrainlab.org/ "https://atlas.internationalbrainlab.org/")
- [Allen adult mouse brain atlas](http://atlas.brain-map.org/atlas?atlas=602630314#atlas=602630314&structure=8&resolution=16.00&x=5700.845703125&y=4000.3232421875&zoom=-3&plate=576989980 "http://atlas.brain-map.org/atlas?atlas=602630314#atlas=602630314&structure=8&resolution=16.00&x=5700.845703125&y=4000.3232421875&zoom=-3&plate=576989980")
- IBL paper on the repeated site and reproducability project - focus ephys measures: [Reproducibility of in-vivo electrophysiological measurements in mice (2022)](https://www.biorxiv.org/content/10.1101/2022.05.09.491042v3 "https://www.biorxiv.org/content/10.1101/2022.05.09.491042v3")
- [My slides _Of Mice and Men. A very personal intro to ephys alignments using the IBL GUI_](https://github.com/sonjafoerster/internshipNL2023/blob/main/images/Intro_to_ephys_alignments_IBL_GUI_public.pdf#:~:text=images-,Intro_to_ephys_alignments_IBL_GUI_public,-.pdf)
