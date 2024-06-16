--- 
title: "Exploring music interactions, with R"
author: "Marc Leman"
date:  '2024-06-14'
site: bookdown::bookdown_site
output: bookdown::bs4_book
documentclass: krantz
monofont: "Source Code Pro"
monofontoptions: "Scale=0.7"
bibliography: [book.bib, packages.bib]
biblio-style: apalike
link-citations: yes
colorlinks: yes
# url: your book url like https://bookdown.org/yihui/bookdown
# cover-image: path to the social sharing image like images/cover.jpg
graphics: yes
cover-image: "images/cover.png"
description:
 "*Exploring music interaction with R* is about understanding the complex dynamic behind values, created with music, that affect humans in a positive way. It is based on R (and Stan), a statistical programming language that has powerful data processing and visualization capabilities. The book focuses on timing aspects of these interactions. It will interest readers interested in extending their knowledge in human interaction and skills in statistical modelling."
github-repo: mleman/ExporingMusicInteractionWithR
url: https://www.ugent.be/
---



# Welcome {-}
This is the online home of *Exploring music interactins, with R*, a book on musical data analysis, visualization and modeling.

<a href="https://www.ugent.be"><img src="images/cover.png" width="250" height="375" alt="The book cover" align="right" style="margin: 0 1em 0 1em" /></a>
 

<!-- ```{r, cover, fig.show='hold', echo=FALSE, out.width='50%'} -->
<!-- if(knitr::is_html_output()){ -->
<!--   knitr::include_graphics("images/cover.png") -->
<!-- } -->
<!--  knitr::include_graphics("images/cover.png") -->
<!-- ``` -->


# Preface {-}

## Description {-}


```r
source("Code/chapAll_00_Initialization.R")
```

## Goal {-}

Many people experience music as a positive power affecting them. 
But what do people do with music, and how does music affect them?
We believe that people use music to create precarious interaction states of high value (therefore: augmented), which affect them in a positive way.
Understanding the underlying mechanisms is the goal of our research.

With this book, we want to go deeper into the *how* and *why*.
Basically, we use a theory to model the data, and develop this theory in view of the modelled data.

In this book we show how our understanding of the underlying mechanisms can increase, using statistical modelling. 
Readers from outside the field of music research may be interested to learn about this theory of *self-augmented interactions*. Possibly, it applies to many domains of human activity outside the musical domain, such as conversations, sports, and activities where one works in a team.
Luckily for us, music is an rich domain where many registers of *self-augmented interactions* are deployed and many registers of statistical modelling can be used as a tool for understanding.

However, every book comes with limitations.

## Limitations {-}

Firtsly, we restrict ourselves here to behavioral data. Brain activity, hormones and neurotransmitters should be added in order to fully support the theoretical claims but others should help us with doing that. 

Secondly, in studying behavioral data, we limit ourselves mostly to timing, that is, acting in time with one another, such as during music playing, dancing, verbal communication, and sports activities.
We do this for obvious reasons. 
Timing is crucial for building up an interaction and maintain it for a while. 
Timing in music is an ideal candidate for understanding self-augmented interactions.

Thirdly, the book is not a textbook but rather a guide to navigate in a space between theory and data. We've titled it *Exploring music interactions* because the research is still in its infancy, especially concerning the broader goal of understanding the mechanisms that energize and affect individuals through these *self-augmented interactions*.

Fourthly, the book is not about applications, nor about technologies, despite the fact that timing leads to interesting applications and technologies such as using augmented reality, virtual reality and exoskeletons, offer new windows for studying timing.

Last but not least, our contribution to statistical modelling will be mainly restricted to *regression analysis*, with a scope that ranges from structural equation models, over hierarchical and distributional regression models, to circular-linear smooth regression, and models based on ordinal differential equations and Kalman filters. 

Given all these and other limitations, and above all, my own limited capacities as musicologist, this book should be considered as an open contribution to the field. Reader having suggestions for improvement can leave a note on the forum associated with this book.

## Overview {-}

<table class="table table-striped" style="font-size: 11px; margin-left: auto; margin-right: auto;">
<caption style="font-size: initial !important;">(\#tab:IndexChapterOverview)Overview of chapters</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> # </th>
   <th style="text-align:left;"> chapter </th>
   <th style="text-align:left;"> theory </th>
   <th style="text-align:left;"> performance </th>
   <th style="text-align:left;"> measure </th>
   <th style="text-align:left;"> modelling </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> 2 </td>
   <td style="text-align:left;"> theory </td>
   <td style="text-align:left;"> self-augmentation </td>
   <td style="text-align:left;">  </td>
   <td style="text-align:left;">  </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> 3 </td>
   <td style="text-align:left;"> modelling </td>
   <td style="text-align:left;"> Bayesian </td>
   <td style="text-align:left;">  </td>
   <td style="text-align:left;">  </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> 4 </td>
   <td style="text-align:left;"> listening </td>
   <td style="text-align:left;"> appreciation </td>
   <td style="text-align:left;"> listening </td>
   <td style="text-align:left;"> questions </td>
   <td style="text-align:left;"> structural equation modelling (SEM) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> 5 </td>
   <td style="text-align:left;"> dancer </td>
   <td style="text-align:left;"> anticipation </td>
   <td style="text-align:left;"> classical ballet </td>
   <td style="text-align:left;"> relative phase (discrete) </td>
   <td style="text-align:left;"> regression </td>
  </tr>
  <tr>
   <td style="text-align:left;"> 6 </td>
   <td style="text-align:left;"> violinst </td>
   <td style="text-align:left;"> parallax </td>
   <td style="text-align:left;"> orchestra playing </td>
   <td style="text-align:left;"> procustus distance </td>
   <td style="text-align:left;"> regression </td>
  </tr>
  <tr>
   <td style="text-align:left;"> 7 </td>
   <td style="text-align:left;"> exoskeletons </td>
   <td style="text-align:left;"> modalities </td>
   <td style="text-align:left;"> dyad violin playing </td>
   <td style="text-align:left;"> relative phase (continuous) </td>
   <td style="text-align:left;"> regression </td>
  </tr>
  <tr>
   <td style="text-align:left;"> 8 &amp; 9 </td>
   <td style="text-align:left;"> tappers </td>
   <td style="text-align:left;"> entrainment </td>
   <td style="text-align:left;"> dyad finger tapping </td>
   <td style="text-align:left;"> relative phase (discrete) </td>
   <td style="text-align:left;"> ODE-regression </td>
  </tr>
  <tr>
   <td style="text-align:left;"> 10 </td>
   <td style="text-align:left;"> drummers </td>
   <td style="text-align:left;"> co-regulation </td>
   <td style="text-align:left;"> dyad drumming </td>
   <td style="text-align:left;"> joint prediction </td>
   <td style="text-align:left;"> Kalman filter </td>
  </tr>
</tbody>
</table>
Table \@ref(tab:IndexChapterOverview) gives an overview of the chapters.

- The first two chapters are about theory and methodology. Chapter \@ref(chapTheory) introduces the general theory; its methodology is based on a Bayesian perspective that will be further refined in subsequent chapters. 
Chapter \@ref(chapModelling) introduces *regression* modelling as our main tool for the analysis of data about timing. Using a metronome as reference for finger tapping, it is shown how timing can be captured as relative phase represented and modelled with a *circular-linear smooth regression*.

- Chapter \@ref(chapListener) accesses the listener's music appreciation using questionnaires as measuring instrument and *structural equation modelling (SEM)* as analysis tool. The chapter shows how theory can be represented as a causal model in a graph (a DAG) and how that DAG translates to a SEM that allows for the validation of the theory with data from a questionnaire. This is the only chapter that is not about timing but we need it to substantiate the idea that music does something with people. 

- Chapter \@ref(chapDancer) is about the effect of repeated musical phrases on sensorimotor anticipation in classical ballet dancing. It uses foot taps and musical beats as markers of timing and relative phase. The chapter applies *circular-linear smooth regression* and an approach to contrast musical phrases selected over time. 

- Chapter \@ref(chapViolinist)  is about the effect of parallax using a 3D versus 2D music play-along system for violin, for training synchronized bowing gestures in an orchestra. It reduces bowing gesture to discrete events and  applies *regression* in a way that is similar to the previous chapter, including an approach to contrast musical phrases. 

- Chapter \@ref(chapExoskeletons) is about the effect of auditory, visual and haptic modality on synchronized playing of two violinists, connected via *exoskeletons* for haptic information exchange. It uses bowing as a measure for capturing continuous relative phase. We go deeper into the feature extraction and use a *regression* with categorical predictors.

- Chapters \@ref(chapTappers1) and \@ref(chapTappers2) are about *rhythmic entrainment*.
In the first chapter, we develop a predictor based on the notion of *coupling strength*, using system of ordinal differential equations (ODE-system). We use this predictor in a *regression* to chapter entrainment as coupling strength. These chapters are a bit more advanced. We show that *ODE regression* is a very powerful and promizing modelling approach.

- Chapter \@ref(chapDrummers) is about playing drums together, using a *Kalman filter* approach to track multiple duration objects played under different conditions, including conditions where players see each other in virutal reality.

- A concluding chapter \@ref(chapConclusions) offers some perspectives for future work in the field.

## Usage {-}

Each chapter can be read independently but it is recommended to start with the chapters on theory and methodology because they offer an overall theoretical and methodological framework for the subsequent chapters.

The book is organized such that the reader can have easy access to the code in R.
The references to the code, if any, is given at the start of each chapter.
In each chapter we follow the same logic: first we do data preparation and data plotting, then we do modelling and plotting of modelling outcomes, then we do contrast testing and plotting of those tests.  We try to maintain this logic as much as possible.

To have easy access to the code we use particular file names.
Overall, the syntax is `XXX_YYY_ZZZ.R`:
 
 - XXX indicates the shortname of a chapter, such as `chapListener`, `chapDancer`. These names are shortcuts for full chapter names.

- YYY is a sequence number, such as `02`, `O3`, which indicates the order in which the script should be processed. 

- ZZZ is a processing name, such as `Initialization`, `DataPreparation`, `DataPlotting`, `Modelling`, which indicates the kind of processing that is dealt with.

- .R is just an extension to indicate the fact that the file is a pure R-script.

For example, the filename `chapListener_02_DataPreparation.R` is an R-script about data preparation in the chapter on the listener. It's sequence number `02` suggests that it there is a `01`, and even an `00` script which should be executed first. 
The script `chapListener_05_ModelPlotting.R` is about plotting the results of modelling. It should be executed after running the modelling script `script_chapListener_04_Modelling.R`. But that script requires at least that scripts `00`, `01`,  `02` and `03` have been considered.
The scripts that should be run in each chapter are called: `chapAll_00_Initialization.R` and `script_chapAll_01_Functions.R`.

## Setting up your computational environment {-}

As computational tool for statistical analysis, we use R and several R-packages in RStudio that get initialized in : `chapAll_00_Initialization.R`. Be sure that all those packages are installed on your system.
We draw mainly `brms`, and our own coding in Stan.
All models have been implemented in Stan 2.26.1.

Some statistical modelling can be computational intensive and we were lucky to have a server at our disposal that allows for parallel processing.
This server runs R version 4.2.3 (2023-03-15) and R-Studio Server 2023.03.0 build 386 on Ubuntu 22.04.2 LTS. The hardware consists of a dual AMD Epyc 74F3 CPU (48 cores total, 96 threads), 128 GB (8x16GB) ECC DDR4 RAM and Nvidia RTX 3090TI graphics card.

To avoid intensive calculations that would take several hours, sometimes several days on a laptop, we offer calculated models.

## Acknowledgements {-}
This work was supported by my [Methusalem](https://www.ugent.be/en/research/funding/bof/methusalem) grant at Ghent University, grant number 01M00208, BOF UGent.

