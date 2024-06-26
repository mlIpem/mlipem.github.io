--- 
title: "Exploring music interactions, with R"
author: "Marc Leman"
date:  '2024-06-26'
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
This is the online home of *Exploring music interactions, with R*, a book on musical data analysis, visualization and modeling.

<a href="https://www.ugent.be"><img src="images/cover.png" width="250" height="375" alt="The book cover" align="right" style="margin: 0 1em 0 1em" /></a>
 

<!-- ```{r, cover, fig.show='hold', echo=FALSE, out.width='50%'} -->
<!-- if(knitr::is_html_output()){ -->
<!--   knitr::include_graphics("images/cover.png") -->
<!-- } -->
<!--  knitr::include_graphics("images/cover.png") -->
<!-- ``` -->


# Preface {-}

## Description {-}



## Goal {-}

Many people experience music as a positive force in their lives. It is probably based on the human ability to use music for creating precarious interaction states of high value. 

In this book, we use statistical modeling to increase our understanding of these interaction states.

While our research focuses on the musical domain, it applies to many other domains of human interactive activity, such as conversations, sports, and teamwork. 
We hope that this book will be of interest to readers both inside and outside the field of music research.

## Limitations {-}

Every book has its limitations, and it is important to be transparent about them from the outset. 

First, we focus exclusively on *behavioral* data. While we recognize the importance of neurobiology, our expertise lies elsewhere. We hope that others will build on our work by incorporating neurobiological data to more fully support our theoretical claims.

Second, in our analysis of behavioral data, we focus primarily on *timing.* Specifically, we examine how people act in time with one another, such as during music playing or dancing. We chose this focus because timing is crucial for building and maintaining interactions, and because music provides an excellent domain for understanding self-augmented interactions.

Third, this book is not a textbook, but rather a *guide* to navigating the space between theory and data. We are exploring music interactions, and we acknowledge that research in this area is still in its infancy. 

Finally, this book is not about applications or biofeedback technologies, but rather about *data*.  While some of our data were collected using technologies such as augmented reality, virtual reality, and exoskeletons, we do not delve deeply into data acquisition.

Given these limitations, and above all, our own limited capacities as musicologists, we offer this book as an open explorative contribution to the field. We welcome suggestions for improvement from our readers.

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
   <td style="text-align:left;"> 1 </td>
   <td style="text-align:left;"> theory </td>
   <td style="text-align:left;"> self-augmentation </td>
   <td style="text-align:left;">  </td>
   <td style="text-align:left;">  </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> 2 </td>
   <td style="text-align:left;"> modelling </td>
   <td style="text-align:left;"> Bayesian </td>
   <td style="text-align:left;">  </td>
   <td style="text-align:left;">  </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> 3 </td>
   <td style="text-align:left;"> listening </td>
   <td style="text-align:left;"> appreciation </td>
   <td style="text-align:left;"> listening </td>
   <td style="text-align:left;"> questions </td>
   <td style="text-align:left;"> structural equation modelling </td>
  </tr>
  <tr>
   <td style="text-align:left;"> 4 </td>
   <td style="text-align:left;"> dancer </td>
   <td style="text-align:left;"> anticipation </td>
   <td style="text-align:left;"> classical ballet </td>
   <td style="text-align:left;"> relative phase </td>
   <td style="text-align:left;"> regression </td>
  </tr>
  <tr>
   <td style="text-align:left;"> 5 </td>
   <td style="text-align:left;"> violinst </td>
   <td style="text-align:left;"> parallax </td>
   <td style="text-align:left;"> orchestra playing </td>
   <td style="text-align:left;"> procustus distance </td>
   <td style="text-align:left;"> regression </td>
  </tr>
  <tr>
   <td style="text-align:left;"> 6 </td>
   <td style="text-align:left;"> exoskeletons </td>
   <td style="text-align:left;"> modalities </td>
   <td style="text-align:left;"> dyad violin playing </td>
   <td style="text-align:left;"> relative phase </td>
   <td style="text-align:left;"> regression </td>
  </tr>
  <tr>
   <td style="text-align:left;"> 7 </td>
   <td style="text-align:left;"> tappers (1) </td>
   <td style="text-align:left;"> entrainment </td>
   <td style="text-align:left;"> simulation </td>
   <td style="text-align:left;"> phase-functions </td>
   <td style="text-align:left;"> regression with a dynamic system </td>
  </tr>
  <tr>
   <td style="text-align:left;"> 8 </td>
   <td style="text-align:left;"> tappers (2) </td>
   <td style="text-align:left;"> entrainment </td>
   <td style="text-align:left;"> dyad finger tapping </td>
   <td style="text-align:left;"> phase-functions </td>
   <td style="text-align:left;"> regression with a dynamic system </td>
  </tr>
</tbody>
</table>
Table \@ref(tab:IndexChapterOverview) gives an overview of the chapters.

- The first two chapters are about theory and methodology. Chapter \@ref(chapTheory) introduces the theory of *self-augmented interactions* and the Bayesian perspective that will be developed in subsequent chapters. 
Chapter \@ref(chapModelling) introduces *regression* modelling as our main tool for the analysis of data about timing. 

- Chapter \@ref(chapListener) accesses the listener's music appreciation using questionnaires. The chapter shows how questionnaires are used in a *structural equation model* for validating a theory of appreciation. This is the only chapter that is not about timing. 

- Chapter \@ref(chapDancer) shows that synchronization of movement with music can be influenced by the classical ballet dancing narrative. The chapter applies *circular-linear smooth regression* and an approach to contrast musical phrases selected over time. 

- Chapter \@ref(chapViolinist) is about the effect of parallax, using a 3D versus 2D music play-along system for violin, for training synchronized bowing gestures in an orchestra. It reduces bowing gesture to discrete events and  applies *regression* in a way that is similar to the previous chapter, including an approach to contrast musical phrases. 

- Chapter \@ref(chapExoskeletons) is about the effect of auditory, visual and haptic modalities on synchronized playing of two violinists, connected via *exoskeletons*. We go deeper into the feature extraction and use a *regression* with categorical predictors.

- Chapter \@ref(chapTappers1) prepares a study about synchronized human finger tapping, using simulated data.
In this chapter, we develop a dynamic system described by ordinal differential equations. We use this dynamic system as a predictor in a *regression* to capture entrainment as *coupling strength*. 

- Chapter \@ref(chapTappers2) builds on the previous chapter. It applies the dynamic system to synchronized human finger tapping. This and the previous chapter are a bit more advanced but we show that this type of *non-linear regression* is very powerful and promising for future work in the field.

- A brief concluding chapter \@ref(chapConclusion) offers some perspectives for future work in the field.

## Usage {-}

It is recommended to start with the chapters on theory \@ref(chapTheory) and methodology \@ref(chapModelling) because they offer an overall framework for subsequent chapters. 

Chapter \@ref(chapTappers1) and  chapter \@ref(chapTappers2) are closely related and can best be read in that order.
All other chapters, however, can be read in order of the reader's preference.

The book is organized such that the reader can have easy access to the code in R.
Reference to the code, if any, is given at the start of each chapter.
In each chapter we follow the same logic: first we do data preparation and data plotting, then we do modelling and plotting of modelling outcomes, then we do contrast testing and sometimes plotting of those tests.  We try to maintain this logic as much as possible because it reflects the workflow of statistical modelling as well as the structure of each chapter.

To have easy access to the code we use a file name convention.
Overall, the syntax is `XXX_YYY_ZZZ.R`:
 
 - XXX indicates the shortname of a chapter, such as `chapListener`, `chapDancer`. These names are shortcuts for full chapter names.

- YYY is a sequence number, such as `02`, `O3`, which indicates the order in which the script should be processed. 

- ZZZ is a processing name, such as `Initialization`, `DataPreparation`, `DataPlotting`, `Modelling`, which indicates the kind of processing that is dealt with.

- .R is just an extension to indicate the fact that the file is a pure R-script.

For example, the filename `chapListener_02_DataPreparation.R` is an R-script about data preparation in the chapter on the listener. It's sequence number `02` suggests that it there is a `01`, and even an `00` script which should be executed first. 
The script `chapListener_05_ModelPlotting.R` is about plotting the results of modelling. It should be executed after running the modelling script `script_chapListener_04_Modelling.R`. But that script requires at least that scripts `00`, `01`,  `02` and `03` have been considered.

The scripts that should be run in all chapters are called: `chapAll_00_Initialization.R` and `chapAll_01_Functions.R`.


## Level {-}

This book is written for MA-students, PhD-students, and interested researchers. 
Some level of statistics knowledge might be required in order to be able to read this book.
However, motivation is essential and self-learning can profit from explorations with the code provided.

Much of our statistical inspiration came McElreath (2020), but also from Kruschke (2015) and Gelman et al. (2014) are to be recommended. Moreover, it can be useful to consult books on regression, for example, Roback and Legler (2021), Singer and Willet (2003), or Dunn and Smyth (2018). 

## Setting up your computational environment {-}

As computational tool for statistical analysis, we use R and several R-packages in RStudio that get initialized in : `chapAll_00_Initialization.R`. Be sure that all those packages are installed on your system when you try to re-calculate from the scripts.

Some statistical modelling can be computational intensive.
We had a server and used parallel processing.
The server runs R version 4.2.3 (2023-03-15) and R-Studio Server 2023.03.0 build 386 on Ubuntu 22.04.2 LTS. The hardware consists of a dual AMD Epyc 74F3 CPU (48 cores total, 96 threads), 128 GB (8x16GB) ECC DDR4 RAM and Nvidia RTX 3090TI graphics card.

We offer fitted models when computation is intensive.

## Finding sources {-}

Sources are found in `Data`, `Code`, `Figures`, `Fitted`.

## About the author {-}

Marc Leman is Methusalem research professor at Ghent University, specialized in the epistemology and methodology of music research, and founder of [ASIL](https://asil.ugent.be). 

## Acknowledgements {-}
This work was supported by my [Methusalem](https://www.ugent.be/en/research/funding/bof/methusalem) grant at Ghent University, grant number 01M00208, BOF UGent.

