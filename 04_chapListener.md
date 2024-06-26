# Listener {#chapListener}

In this chapter^[This chapter is devoted to the late ir. Henk Jacobs (1953, 2024) who was my PhD-student in musicology. He applied his expertise in marketing to musicology and this chapter is highly inspired by his insight and feedback.], we delve into the question what music does to people. 
The chapter is based on a theory of music appreciation, which is used for developing the questionnaire for a survey, as well as for developing a statistical model. The modelling aims at connecting theory and data via refinement and, possibly, an updated theory. Ultimately, the goal is a theory of how people reflect on what music does to people. In that sense, the viewpoint is static, akin to a reflection about self-augmented interactions after this interaction has been completed.

This chapter depends on the following scripts for data preparation, plotting, modelling and model plotting:


```r
source("Code/chapAll_00_Initialization.R")
source("Code/chapAll_01_Functions.R")
source("Code/chapListener/chapListener_02_DataPreparation.R")
source("Code/chapListener/chapListener_03_DataPlotting.R")
source("Code/chapListener/chapListener_04_Modelling.R")
source("Code/chapListener/chapListener_05_ModelPlotting.R")
```



## Workflow

The theory-driven modelling applies the Bayesian epistemology outlined in figure \@ref(fig:chapTheoryBayesianModel1). The *subject* is the listener, who interacts with music as sonic moving form. In this chapter, we probe the listener with questions about appreciation and motivation. 
The answers are *indicators* of the listener's appreciation.

To fully grasp the stucture of this chapter, it is instructive to consider the workflow of figure \@ref(fig:chapListenerWorkflow), which also applies this Bayesian epistemology.

<div class="figure" style="text-align: center">
<img src="Figures/chapListener_Workflow.jpg" alt="Overview of theory and statistical modelling" width="100%" />
<p class="caption">(\#fig:chapListenerWorkflow)Overview of theory and statistical modelling</p>
</div>

The starting point is a theory of music appreciation.
Based on this theory, a questionnaire and a statistical model is generated.
The questionnaire is launched in a survey, and the answers to this questionnaire, the data, are processed and transmitted to the statistical model. 
The statistical modelling then serves as feedback to the theory.

In what follows, we hook our wagon to an acceptable stage of this iteration, and we'll try to further refine the results obtained.

## Theory

Our approach draws from the fields of *neurobiology*, *marketing*, and *musicology.* This framework enables us to conceptualize music appreciation as the rating assigned by listeners to the gratification they experience while engaging with music.

- *Neurobiology* suggests that gratification or reward arises from the brain's release of dopamine, a neurotransmitter that diffuses throughout the brain, eliciting a pleasurable sensation and triggering a desire for more —- a behavioral pattern akin to seeking out further stimuli that induce this reward, reminiscent of addiction.

- In the realm of *marketing*, the concept of wanting is linked to the perceived value of a product, which reflects an overall appreciation indicative of customer satisfaction regarding the product's functionalities and qualities. These qualities can be assessed through a series of questionnaires designed to probe various aspects.

- Finally, in the domain of *musicology*, it is proposed that music profoundly influences the listener's experience, which can be analyzed in terms of embodiment, anticipation, and expression -- as discussed in chapter \@ref(chapTheory).


Combining insights from neurobiology, marketing, and musicology, a theory of music appreciation can be outlined as follows:
When a listener engages with music, a dynamic anticipation-reward-motivation loop is initiated, leading to experiences such as being emotionally moved, deeply absorbed, or profoundly touched, which the listener can subsequently reflect upon. These experiences often culminate in a pleasurable bodily reward, which is positively evaluated.
Upon reflection, the listener may discern the specific qualities of the music that contributed to these pleasurable experiences.

Indeed, any comprehensive theory of music appreciation must also consider the influence of context. Factors such as the setting in which the music is heard (e.g., live concert versus radio broadcast), the listener's mood, demographic background, and other environmental variables can significantly impact how listeners perceive and interpret their musical experiences. Therefore, when conducting surveys or assessments, it is essential to account for these contextual factors to ensure clarity and accuracy in participants' responses, thus avoiding potential confusion or misinterpretation.

It's important to note that the concept of appreciation remains independent of the specific type of music being listened to. For example, even sad music can evoke high appreciation scores despite its melancholic nature, as it may trigger intense embodied experiences that are highly valued by listeners. Conversely, happy music may not always receive high appreciation if it fails to engage the listener with a compelling rhythm or groove.

Furthermore, the theory of appreciation is agnostic to factors such as gender or age. What truly matters is the activation of reward, pleasure, and wanting experiences by the music. Global appreciation reflects both an inward reflection, focusing on the nature and evaluation of the experience itself, and an outward reflection, directed towards the quality of the music. These reflections are influenced by various contextual factors such as background, gender, and setting.

## Causal model

The above theory can be further clarified as a network of variables and relationships between variables.

### Directed acyclic graph (DAG) {-}
<div class="figure" style="text-align: center">
<img src="Figures/chapListener_Dagitty1c.jpg" alt="Causal model of appreciation" width="100%" />
<p class="caption">(\#fig:chapListenerDAG1)Causal model of appreciation</p>
</div>

Figure \@ref(fig:chapListenerDAG1) shows a directed acyclic graph (DAG) in which the theory is defined as a network of variables and causal relationships. Note that the use of the term *causal* has a very specific meaning in this context. A cause-effect relationship among two variables means (i) that the information flow has a *direction*, in the sense that the cause precedes the effect in time, (ii) that there is an *association* (correlation) between the variables, and (iii) that *no potential confounding variables* could account for the observed association. The latter can be tested by considering the logic of the relations (see below).

In this DAG, `Kind_of_Experience` is what is affected by the musical qualities, and the other variables are exposed to this variable, with `Global_Appreciation` as outcome.
The rationale is that musical qualities (`Quality`) affect the listener, causing experiences in the listener (`Kind_of_Experience`), including for instance, an increase in dopamine level generating pleasurable feelings and a wanting urge.
These experiences set the scene for an assessment (`Evaluation`), which then cause the scoring for `Global_Appreciation`. 

Be aware that the ellipses marked with X are associated with questions. 
They all have an incoming arrow because the answers to questions are generated by latent variables.

Additionally, it's important to note that `Quality` is a determinant of `Kind_of_Experience`. Essentially, `Quality` represents the musical attributes identified by the participant as contributing to the type of experience they had.

### Confounding variables {-}
While the causal direction and the plausible association are clear concepts, it might require careful logical reasoning in order to prevent confounding variables in such a network.
Fortunately, a DAG can be tested using the tool [Daggity](https://dagitty.net/dags.html). It involves evaluating whether the assumed causal structure is consistent, that is, whether certain sets of variables are conditionally independent given other sets of variables, as predicted by the DAG. We are lucky, our DAG is safe. No adjustment is necessary to estimate the total effect of `Kind_of_experience` on `Global_Appreciation`, meaning that there are no confounding paths between the variable `Kind_of_experience` and the outcome variable `Global_Appreciation`.

We can test different interpretations of the model, for example, by drawing an arrow from `Kind_of_experience` to `Quality`, assuming that the `Kind_of_experience` is the cause of the quality recognized in the music. 
However, one should be careful about possible open biasing paths, where confounding variable would bias the estimation of the causal effect between `Kind_of_experience` and `Global_Appreciation`.

## Questionnaire

Based on the above DAG for music appreciation, it is possible to define the questions that allow us to measure the variables:

- `Global_appreciation` is estimated with a single question, scored on a scale from 1 to 10. It reflects how eager the listener would want this music.

- `Quality` is based on six yes/no questions that probe different aspects of the musical quality, such as "The music has qualities which I like (Y/N)". The assessment of quality is a subjective assessment about the music, influenced by the kind of experience. 

- `Evaluation` is based on questions that probe the value of the experience, such as "I was touched in a positive sense" or "I enjoyed the experience," rated on scales from 1 to 5. 
The assessment is influenced by the kind of experience and it is about ourselves, as listener.

- `Kind_of_experience` is based on questions addressing the three subcategories of immersive, embodied, and emotional experiences, such as "I was absorbed by the music," "I moved along with the music," "I experienced emotions". These questions probe the kind of experience that was generated by the music.

There are some additional questions about demography such as listener's age, gender, and education.
Finally, there are two questions about arousal and valence effects of the music. In particular:
"In the music, I heard energy, excitement" (rated on a scale from 1 to 5).
"In the music, I heard joy, optimism, positive emotions" (rated on a scale from 1 to 5).

By utilizing this questionnaire, researchers can effectively gather data to understand and analyze the components of music appreciation outlined in the theory.

In what follows, we don't go into the questionnaire's specific questions.
Unsless specified otherwise, we use the question labels Q1, Q2 ..., and focus mainly on how questions are structured, as pointed at in figure \@ref(fig:chapListenerDAG1).

## Survey

Using the questionnaire, a survey was conducted in collaboration with the Flemish Radio for classical music, VRT-Klara. In the edition of the Klara-Top100 in 2023, listeners were invited to participate in a survey, using a redirect to a survey platform (Qualtrix). Approximately 1200 listeners responded to the survey and about 800 listeners completed the entire questionnaire.

The questionnaire consisted of two parts. The first part investigated the factors contributing to high appreciation, coded as *Liking* in Q57, while the second part, using identical questions, explored factors contributing to low appreciation, coded as *Disliking* in Q57. Overall, the questionnaire comprised 66 questions. 
In the current analysis, only questions with score-based responses are included, while open-ended questions requiring verbal descriptions (e.g. of quality, kind of experience, evaluation) are excluded. The dataset used in this analysis is sourced from Jacobs et al. (in preparation).





## Inspect the data

Exploration of the data via plotting is always useful. 

### Appreciation {-}
Here we show the global appreciation (labelled in the dataset as: Q1) on a scale from 1 to 10, per category *Liking* or *Disliking.* 
The highest appreciated music gets a mean of 9.42, and standard deviation of 0.88.
The lowest appreciated music gets a mean of 2.89 and standard deviation of 1.66.
Apparently, the highest appreciated music is somewhat better defined than the lowest appreciated music which, in some case still gets an overall appreciation of 5/10 and in rare cases even 6/10.

<div class="figure">
<img src="Figures/chapListening_Plot1.png" alt="Distribution of scorings for global appreciation (Q1) for music qualified as Liking and Disliking (Q57), with mean and standard deviation indicated." width="80%" />
<p class="caption">(\#fig:chapListeningPlot1)Distribution of scorings for global appreciation (Q1) for music qualified as Liking and Disliking (Q57), with mean and standard deviation indicated.</p>
</div>

### Participants {-}
A quick view on participants shows some striking facts. About 43% is 61-70 years old and only 17% is younger than 50 years old. There are about twice as many females compared to men. The majority has a low level of music education. Their main interaction with music is listening, not playing.
The profile might be representative for a classical music radio.

<div class="figure">
<img src="Figures/chapListening_Plot2.png" alt="Some info about the listeners" width="100%" />
<p class="caption">(\#fig:chapListeningPlot2)Some info about the listeners</p>
</div>

### Affect attribution {-}
The listeners' attribution of arousal and valence was probed with a Likert scale from 1 to 5. 
These scores can be interpreted as coordinates in so-called circumplex model of affect, as shown in figure \@ref(fig:chapListenerArousalValenceLikeDislike). 
We use it here to identify four different attributed affect categories of music.

- High-arousal high-valence is defined as `happy`

- high-arousal low-valence is defined as `aggressive`

- low-arousal high-valence is defined as `relaxing`

- low-arousal low-valence is defined as `sad`.

The  horizontal and vertical band in the middle show the neutral zone where listeners gave a score of 3 to either question.
Interestingly, relaxing music is liked a lot, while aggressive music is mostly disliked, although sometimes liked.
Likewise, happy music is mostly liked, but sometimes disliked.
And sad music, it seems, is often disliked, but often also liked.

<div class="figure">
<img src="Figures/chapListening_Plot4.png" alt="Liked and disliked music categorized by arousal and valence on a 5-point scale. Jitter is used to show the distributions" width="100%" />
<p class="caption">(\#fig:chapListenerArousalValenceLikeDislike)Liked and disliked music categorized by arousal and valence on a 5-point scale. Jitter is used to show the distributions</p>
</div>


Overall, there seems to be quite some structure in the dataset.
Cronbach's alpha gives a value of 0.84, which is considered good or excellent, meaning that the internal consistency of the dataset is high. The mean value of all correlations among all subjects is 0.54.
More can be said about the data but we restrict ourselves to the minimum needed for modelling.


<table class="table table-striped" style="font-size: 11px; margin-left: auto; margin-right: auto;">
<caption style="font-size: initial !important;">(\#tab:chapListenerExplore2)Cronbach alpha and mean</caption>
 <thead>
  <tr>
   <th style="text-align:right;"> Cronbach.s.alpha </th>
   <th style="text-align:right;"> mean </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;"> 0.8339282 </td>
   <td style="text-align:right;"> 0.5618432 </td>
  </tr>
</tbody>
</table>


## Preparing analysis

The steps that follow can be seen as preparatory work for statistical modelling.
The rationale is that in view of the main question about the global appreciation (Q1), it is possible to
identify the questions that have low correlation with Q1. 
Such questions will anyhow not really affect Q1.

To start with, consider figure \@ref(fig:chapListenerExplore1a).
The left panel shows the correlation among all questions. 

<div class="figure" style="text-align: center">
<img src="Figures/chapListener_Cor1.png" alt="Correlation matrices. (left) original, (right) pruned" width="49%" /><img src="Figures/chapListener_Cor2.png" alt="Correlation matrices. (left) original, (right) pruned" width="49%" />
<p class="caption">(\#fig:chapListenerExplore1a)Correlation matrices. (left) original, (right) pruned</p>
</div>

To check contributes to Q1, it may suffice to look at the first vertical column (with Q1 as label). 
The important questions have high correlation values. 
Questions having a correlation value less then $.5$ can be deleted -- or, as we did, set to zero.
The leftovers are shown in the right panel.
These are: Q2, Q31, Q33, Q35, Q37, Q39, Q41, Q43, Q47, Q48, Q49, and Quality:

- Quality is the weighted sum of six yes/no questions^[This isbased on yes/no questions and the weightings defined by the Kano model, see https://www.interaction-design.org/literature/article/the-kano-model-a-tool-to-prioritize-the-users-wants-and-desire.]. 
Figure \@ref(fig:chapListeningPlot3) suggest that Quality is indeed correlated with Q1.

<div class="figure">
<img src="Figures/chapListening_Plot3.png" alt="Quality versus the product value, coded as Q1 (jitter added), fitted by a straight line and smoothing curve" width="100%" />
<p class="caption">(\#fig:chapListeningPlot3)Quality versus the product value, coded as Q1 (jitter added), fitted by a straight line and smoothing curve</p>
</div>
- Indicators of the latent variable `Kind_of_experience` are:

    - Q31, Q33 and Q35, which probe the listeners' immersive experience in terms of attention to, absorption in and engagement with the music.

    - Q37, Q39, Q41, which probe the listeners' embodied experiences in terms of moving, participating, having physical sensation.

    - Q43, probing the listeners' emotional experience. 

    - Q2, probing the listeners' connection with the music. 


- Finally, Q47, Q48, and Q49 probe whether listeners' evaluation of their experience in terms of enjoying the music, and whether they were touched and annoyed by the music. These questions are indicators of the latent variable `Evaluation.` 

In short, based on a simple correlation threshold, a pruned version of our questionnaire has been obtained.
The questions that pass the threshold, the leftovers are candidates for a model.

## Structural equation modelling

A structural equation model (SEM) implements the structure shown in figure \@ref(fig:chapListenerDAG1). Here we use the question labels as used in the questionnaire.
The SEM estimates the strength and significance of the association between the variables.
Then, we can assess the fit of the model to the observed data, and evaluate the overall model's explanatory power. 

### Model {-}


```r
  model_1 <- '
Evaluation =~ Q47 + Q48  + Q49
Immersion =~ Q33 + Q35 + Q31 
Embodiment =~ Q37 + Q39 + Q41
Emotion =~ Q43
Kind_of_experience =~ Immersion + Embodiment + Emotion
Kind_of_experience ~ Quality 
Evaluation ~ Kind_of_experience
Q1 ~ Evaluation + Q2'
```

The SEM follows the syntax from the R-package `lavaan.` 
The operator `=~` defines a confirmatory factor analysis, which is used to created a latent variable.
For example, `Evaluation` is constructed from Q47, Q48 and Q49.
Similarly, `Immerson`, `Embodiment` and `Emotion` are latent variables, and they all define `Kind_of_experience`.
The operator `~` defines a regression, which is used to relate a response variable to predictor variables. 
Quality (as indicator) has a link to `Kind_of_experience` and `Kind_of_experience` to `Evaluation`.
Then, `Evaluation` and Q2 are predictors for `Q1`, which was called `Global_appreciation` in our DAG of figure \@ref(fig:chapListenerDAG1).

### Covariance matrix {-}

Mathematically speaking, SEM fits a covariance matrix $\Sigma(\theta)$ of a model, with a covariance matrix $\Sigma$ of the data. In optimal fitting:
$$
\Sigma = \Sigma(\theta),
$$
where $\theta$ are the parameters of the model.

Our pruned questionnaire contains 12 questions of about 800 respondents who answered the questions. That gives us a 12x12 covariance matrix of questions ($\Sigma$), and a 12x12 covariance matrix of questions embedded in a model with parameters, $\Sigma(\theta)$. 
Then, this $\Sigma(\theta)$ will be optimized to approach $\Sigma$.
When optimization is successful, then we obtained insight in the data from the viewpoint of our theory of music appreciation.

Thus, rather than just putting all data unrelated in a box, our theory suggests that data are structured.
The data come from measurements using questions that relate to a theory.
Hence, it can be tested if that theory is justified by the data.

### CFA and regression {-}
Let us just recall what we just said.
Structure among variables, as specified by the DAG, is defined by *confirmatory factor analysis (CFA)* and *regression.*
The *CFA* generates a new latent variable from a weighted sum of variables. 
For example, the latent variable `Immersion` is generated from indicators Q33, Q35, Q31.
The *regression* associates a given variable with a weighted sum of given variables.
For example,  Q1 (the response) is associated with `Evaluation` and Q2 (the predictors).
Recall that Quality is not really a latent variable anymore in this model because it was obtained by combining yes/no questions in a pre-processing stage. In contrast, `Kind_of_experience` and `Evaluation` can be considered genuine latent variables.


## Dataset and SEM

Let's now fit the SEM with our data. Recall that the goal of doing this fitting is to see whether there is indeed structure in our data, as defined in the model.


```r
semfit1 <- lavaan::sem(model_1, data = Data, 
                       group = "Q57",  meanstructure = TRUE)
```

`Lavaan` has a lot of bells and whistles but we will limit ourselves here to a simple fitting in which we use Q57 to divide the database in two parts, based on *Liking* and *Disliking*.
The two parts of our database reflect the fact that listeners filled in the same questionnaire twice. First for their preferred music, and then for a piece that they did not like.
When fitting the models, we obtain weights for the parameters that associate the variables. 
However, whether the fitted model is acceptable depends on some tests that check the discrepancy between $\Sigma$ and $\Sigma(\theta)$.

### Measurement invariance {-}

We use a technique called called  *measurement invariance* to check the consistency across different groups or conditions simply by comparing the fit of several nested models that impose increasingly restrictive constraints on the parameters of the measurement model across groups. If measurement invariance is not established, differences in the observed scores between groups may be due to measurement bias rather than true differences in the underlying construct. Here we have a summary of the measurmement invariance.




 \small


```
## ####################### Model Fit Indices ###########################
##             chisq  df pvalue rmsea   cfi   tli  srmr        aic        bic
## semfit1  902.093† 122   .000 .089  .849† .810  .083† 40633.042† 41042.366 
## semfit2  956.857  130   .000 .089† .840  .811† .085  40671.807  41038.044†
## semfit3 1125.185  136   .000 .095  .809  .783  .093  40828.134  41162.057
```

 \normalsize

Comparing the results of different models (semfit1, semfit2, and semfit3), we can see the following trends:

- Chi-square: All models have significant chi-square values (p < .05), indicating that the models do not perfectly fit the data. However, this is often the case with large sample sizes, where even minor deviations from the model can lead to significant chi-square values.

- RMSEA: All models have RMSEA values around .089-.095, which are within an acceptable range (typically below .08 for good fit), indicating reasonable fit.
 
- CFI and TLI: All models have CFI values around .81-.85 and TLI values around .79-.81, suggesting a reasonable fit.

- SRMR: Model semfit1 has the lowest SRMR (.083), indicating better fit in terms of standardized root mean square residual.

- AIC and BIC: Model semfit1 has the lowest AIC value among the three models, indicating better parsimony.

Based on these results, the conclusion might be that model semfit1 provides the best overall fit to the data among the three models tested. However, given the minor differences among the three models, measurement invariance can be assumed.

### Parameters {-}

Here we inspect the estimated parameters for the latent variables and the regression:


 \tiny


```r
s <- summary(semfit1, standardized = TRUE, rsquare = TRUE, ci = T)
reg <- '
Group 1 [Liking]:

Latent Variables:
                        Estimate  Std.Err  z-value  P(>|z|) ci.lower ci.upper   Std.lv  Std.all
  Evaluation =~                                                                                
    Q47                    1.000                               1.000    1.000    0.315    0.674
    Q48                    0.848    0.114    7.422    0.000    0.624    1.072    0.267    0.383
    Q49                   -0.368    0.054   -6.756    0.000   -0.474   -0.261   -0.116   -0.337
  Immersion =~                                                                                 
    Q33                    1.000                               1.000    1.000    0.671    0.783
    Q35                    0.702    0.050   13.968    0.000    0.604    0.801    0.471    0.600
    Q31                    0.856    0.058   14.747    0.000    0.742    0.969    0.574    0.649
  Embodiment =~                                                                                
    Q37                    1.000                               1.000    1.000    0.896    0.727
    Q39                    0.957    0.104    9.205    0.000    0.753    1.161    0.857    0.672
    Q41                    0.408    0.052    7.860    0.000    0.306    0.509    0.365    0.381
  Emotion =~                                                                                   
    Q43                    1.000                               1.000    1.000    0.681    1.000
  Kind_of_experience =~                                                                        
    Immersion              1.000                               1.000    1.000    0.870    0.870
    Embodiment             0.602    0.094    6.412    0.000    0.418    0.786    0.393    0.393
    Emotion                0.688    0.075    9.156    0.000    0.540    0.835    0.589    0.589

Regressions:
                       Estimate  Std.Err  z-value  P(>|z|) ci.lower ci.upper   Std.lv  Std.all
  Evaluation ~                                                                                
    Kind_of_exprnc        0.322    0.040    8.028    0.000    0.244    0.401    0.597    0.597
  Kind_of_experience ~                                                                        
    Quality               0.089    0.027    3.300    0.001    0.036    0.142    0.152    0.141
  Q1 ~                                                                                        
    Evaluation            1.382    0.160    8.630    0.000    1.068    1.696    0.435    0.497
    Q2                   -0.015    0.046   -0.318    0.750   -0.105    0.075   -0.015   -0.010
'
```

 \normalsize
All latent variables, except Q2, fit well.
This can be seen in the P(>|z|) or Std.all columns.
When looking at the regression we see that Q2 doesn't play any role for the specification of Q1.


 \tiny


```r
 # summary(semfit1, standardized = TRUE, rsquare = TRUE, ci = T)
reg <- '
Group 2 [Disliking]:

Latent Variables:
                        Estimate  Std.Err  z-value  P(>|z|) ci.lower ci.upper   Std.lv  Std.all
  Evaluation =~                                                                                
    Q47                    1.000                               1.000    1.000    0.568    0.787
    Q48                    0.988    0.049   20.044    0.000    0.892    1.085    0.561    0.761
    Q49                   -0.742    0.067  -11.033    0.000   -0.874   -0.610   -0.421   -0.420
  Immersion =~                                                                                 
    Q33                    1.000                               1.000    1.000    0.617    0.837
    Q35                    1.027    0.040   25.803    0.000    0.949    1.105    0.633    0.854
    Q31                    0.775    0.059   13.041    0.000    0.659    0.892    0.478    0.467
  Embodiment =~                                                                                
    Q37                    1.000                               1.000    1.000    0.766    0.901
    Q39                    0.904    0.044   20.712    0.000    0.818    0.989    0.692    0.800
    Q41                    0.413    0.059    6.989    0.000    0.298    0.529    0.317    0.261
  Emotion =~                                                                                   
    Q43                    1.000                               1.000    1.000    1.287    1.000
  Kind_of_experience =~                                                                        
    Immersion              1.000                               1.000    1.000    0.940    0.940
    Embodiment             0.917    0.058   15.852    0.000    0.804    1.031    0.694    0.694
    Emotion                0.664    0.086    7.766    0.000    0.497    0.832    0.299    0.299

Regressions:
                       Estimate  Std.Err  z-value  P(>|z|) ci.lower ci.upper   Std.lv  Std.all
  Evaluation ~                                                                                
    Kind_of_exprnc        0.840    0.051   16.573    0.000    0.740    0.939    0.857    0.857
  Kind_of_experience ~                                                                        
    Quality               0.205    0.017   12.108    0.000    0.172    0.238    0.354    0.453
  Q1 ~                                                                                        
    Evaluation            1.517    0.109   13.914    0.000    1.303    1.731    0.861    0.523
    Q2                   -0.142    0.044   -3.190    0.001   -0.229   -0.055   -0.142   -0.098
'
```

 \normalsize

As far as the second part of our dataset is concerned, all latent variables fit well. 
Again, Q2 doesn't contribute much to the global result.

Overall, the model suggests that `Evaluation` is a relevant predictor for Q1. 
Moreover, `Evaluation` is predicted by `Kind_of_experience` and
`Immersion` is the strongest contributor in Liking and Disliking groups. 

In the Liking group, `Emotion` contributes more than `Embodiment`, while in Disliking, `Embodiment` contributes more than `Emotion.`
Quality has less an impact in the Liking group, compared to the Disliking group. 

Overall, in the Liking group `Immersion` and `Emotion` are strong predictors, while in the Disliking group, `Immersion` and `Embodiment` and `Quality` are strong. When they like the music, subjects are more emotionally touched. When they dislike the music, subjects seem to be overall less emotionally touched. They refer more consistently to the quality of the music as source of disliking.


## Predictions

In this and the following sections, we show that the model can be used for predictions.

### J.S. Bach {-}
In a first example, we'll predict the listeners' overall appreciation (Q1) of Bach pieces.
Can we predict Q1 for Bach pieces, given a SEM trained with a dataset where Bach pieces have not been included? 
This can only happen if the SEM captures necessary information from other pieces, so that it can predict the Q1 for new pieces using the indicators Q47, Q48, Q33, Q35, Q31 and Quality. In other words, SEM has to generalize its input to Q1 so that it applies to Bach.

To figure that out, a distinction is made between *training-data* and *test-data*.
The training-data contain all data except the answers of 157 listeners who said something about Bach.
The test-data contain only Bach pieces. 
Then, a SEM is trained with the training-data, and predictions are regenerated.

<table class="table table-striped" style="font-size: 11px; margin-left: auto; margin-right: auto;">
<caption style="font-size: initial !important;">(\#tab:chapListenerBachPrediction)Prediction of Bach pieces, versus original data</caption>
 <thead>
  <tr>
   <th style="text-align:right;"> Q1_predict </th>
   <th style="text-align:right;"> Q1_data </th>
   <th style="text-align:left;"> LD </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;"> 11.86 </td>
   <td style="text-align:right;"> 9 </td>
   <td style="text-align:left;"> Liking </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 12.04 </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> Liking </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 12.55 </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> Liking </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 10.67 </td>
   <td style="text-align:right;"> 9 </td>
   <td style="text-align:left;"> Liking </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 12.84 </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> Liking </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 13.54 </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> Liking </td>
  </tr>
</tbody>
</table>



Figure \@ref(fig:chapListenerBachpred1) shows the prediction of Bach appreciation in `Q1_prediction` and the original Bach appreciation data in `Q1_data` (cor =.95).

<div class="figure">
<img src="Figures/chapListener_Bach_pred1_nonscaled.png" alt="Prediction of global appreciation of Bach pieces" width="100%" />
<p class="caption">(\#fig:chapListenerBachpred1)Prediction of global appreciation of Bach pieces</p>
</div>

The model gives an accurate prediction of the global appreciation of Bach's pieces.
Apparently, Bach's pieces are not always liked. 
A more in depth analysis would be needed to figure out whether this depends on particular music pieces.

### Attributed affects {-}

In a second example, we look at the latent variables from the viewpoint of sad, relaxing, aggressive and happy music. 
These categories were introduced in figure \@ref(fig:chapListenerArousalValenceLikeDislike).
After prediction, figure \@ref(fig:chapListenerArousalValencepred) is created.
It shows the distribution of 50 dots per latent variable and these latent variables are scaled from -2 to 2.
The distributions reflect what each latent variable contributes to Q1 for sad, relaxing, aggressive and happy music.
`Evaluation` and `Experience` display similar distributions, meaning that the appraisal about experiences depends on whether experiences have a high degree of immersion.

The figure reveals that the distribution of relaxing, aggressive, and happy tends towards an unipolar scoring, with 96%, 82% and 78% of the counted dots at one side of `Evaluation.` This scoring is in agreement with the valence.
High valence (relaxing and happy) get high scores, low valence (aggressive) gets low scores.
However, the distribution of sad tends to be bi-polar with a balance of 62% having a negative evaluation.
That means that 38% of the listeners, with a decisive opinion about the arousal-valence questions, had attributed high `Evaluation` to sad music and thus a high overall appreciation (Q1) because both are strongly correlated.


<div class="figure">
<img src="Figures/chapListener_ArousalValence_pred.png" alt="Latent variables from SEM modelling and distributions for the category of happy,  aggressive, relaxing, and sad, as attributed by listeners" width="100%" />
<p class="caption">(\#fig:chapListenerArousalValencepred)Latent variables from SEM modelling and distributions for the category of happy,  aggressive, relaxing, and sad, as attributed by listeners</p>
</div>

## Discussion

Overall, the model supports the theory of music appreciation.
Music appreciation rest mainly on the evaluation of pleasurable experiences and 
the attribution of quality plays a role depending on whether music is liked or disliked.

The main findings are:

- When a listener likes the music, then quality scores low, compared to the situation when a listener dislikes the music. This can be explained by the fact that the listener had anticipated certain qualities in the music. In liked music, the qualities agree with the anticipation and therefore, their role is less prominent than when the qualities do not agree with the anticipation. State otherwise, when people dislike the music, it is attributed to the musical qualities, and not to their anticipation.

- The causes of appreciation are experiences. Immersion appears to be the most important consistent predictor, while embodiment and emotion have different roles depending on whether music is liked or not. This is somewhat surprising because the literature puts quite a lot of emphasis on emotion. Here we show that the experience of unity and absorption are more consistent and strong predictors, compared to felt emotions.  

The connection between quality and experience/evaluation may be intricate.
A listener may find that the music is of high quality, for example due to its composition, its performance, and so on, but that the music doesn't appeal to a pleasant feeling when played over the radio. Probably, it would get a low rating for appreciation. 

Interestingly, in our dataset we don't have examples of dis-accordance between attributed quality and experience/evaluation.
This may be due to the fact that listeners were asked to give an example of music they dislike when hearing over the radio, and then finding a rationale for the disliking. 

If listeners would have been asked to select a piece with high quality, and then rationalize whether that piece would be pleased when hearing over the radio, the situation might have been different.
The reason why somebody doesn't like to hear music over the radio may not be due to intrinsic musical qualities, but to context. This aspect probably needs further clarification in follow-up studies.

Finally, what happens when listeners hear the same music repeatedly? Can they still experience reward when the anticipation-reward-motivation mechanism becomes saturated? The theory suggests an affirmative answer. 
Listeners may become entrained by the music. Similar to a locomotive pulling wagons, music propels the listener to a point where reward can be consistently experienced. The crux lies in its dynamic binding structure, known as *sonic moving forms* and their ability to dynamically shape anticipation through the melodic line, harmonic progression, rhythmic flow, tension, and resolution. Being entrained by the music, embodied experiences are anticipative. This feeling is potent, fostering a sense of control that is rewarding and, thus, pleasurable (see the illusion of reversed causality explained in chapter \@ref(chapTheory)).

## Conclusion

In this chapter, we probed listeners to reflect on what music does to them. Using a questionnaire, we refined a theory of music appreciation. Based on neurobiology, marketing and musicology, a causal model was tested in a structural equation modelling approach using data from this questionnaire. 

The model suggests that music can cause experiences in listeners and that immersion is an important experience contributing to appreciation. 
Can it be linked with our dynamic concept of self-augmented interactions?
The latter indeed suggests that experiences occur during the interaction with music, rather than after the interaction with music.
It's likely that immersion fits with that dynamic idea but the challenge is how it can be measured. 
Anyhow, in the chapters that follow, we focus less on experiences and look at music interactions from the viewpoint of timing.
Moreover, we put more emphasis on encoders (dancers, musicians) than on decoders (listeners).

<!-- ## References -->
<!-- Jacobs et al. (in preparation) -->
