---
layout: project
type: Masters paper
date: 2019-03-10

images:
    - title: first
      image: "BDA-figure1.png"
      image-description: "Log-linear Probability Density Function and Cumulative Distribution Function of views on individual Forum topics."
    - title: second
      image: "BDA-figure2.png"
      image-description: "Log-log heat plots of topic views against number of replies (left) and number of authors (right)."
    - title: third
      image: "BDA-figure3.png"
      image-description: "Log-log scatter plots with linear regression models fitted to both underlying data and binned data. Number of views against number of replies (top left), number of views against number of unique authors (top right) and number of replies against number of unique authors (bottom)."
    - title: fourth
      image: "BDA-figure4.png"
      image-description: "Log-log heat plots of number of views against conversation length (left) and average time between posts (right)."
    - title: fifth
      image: "BDA-figure5.png"
      image-description: "Log-log scatter plots with linear regression models fitted to both underlying data and binned data. Number of views against conversation length (top left), number of views against average time between posts (top right) and average time between posts against conversation length (bottom)."
    - title: main
      image: "BDA-figure6.png"
      image-description: "Line plots displaying temporal patterns of when topics were created by proportion per time of day (top) and proportion per day of week (bottom)."

title: Exploring discursive quality on the OpenStreetMap Forum  
description: A short methods paper exploring the use of the OpenStreetMap Forum as a tool for communication and as a continuing knowledge base for the project.

tools:
  - R
  - Python
methods:
  - inequality
  - time-series

report:  'True'
gdocs-link:  "https://docs.google.com/document/d/15wM9t4ohcj48Xq343QAOzcZT_5pgbaN-Hj8m81ojr8E/"
code: 'True'
github-link:  "masters-bda"

---
## Summary
This is a short (one week) project I did during my MSc to produce a methods paper that would demonstrate my ability to apply statistical analysis techniques for large non-normally distributed datasets in the context of social science questions.

Using data from the [OpenStreetMap (OSM) Forum](https://forum.openstreetmap.org/), collected for [another paper]({{site.url}}/masters-accessing-data), I explored how the forum is used by the OSM community to communicate and collect knowledge. In particular, I characterise how different conversations (or topics) on the Forum received different levels of engagement in terms of direct responses, number of participants and overall views.

I specifically focused on testing four main hypotheses:
  (H1) Interest will vary substantially between topics.
  (H2) In-depth discussions (with more replies and unique authors) will attract more interest.
  (H3) Short, quick conversations (with short overall length and reply times) will attract less interest.
  (H4) Topics posted when more people are using the platform will attract more interest.

## Background
The OpenStreetMap Forum began as a test of forum software within the project but was quickly picked up and used by the community. Because of these accidental beginnings, the primary purpose of the forum was never fully articulated. As a form of communication, it allows members to engage in broad discussions but also to ask and answer questions. As these conversations are publicly accessible, the forum conversations also serve as a shared knowledge base for the project, enabling any contributor or potential contributor to discover relevant existing queries and discussion. The goal of this paper was to understand what conversations received the most attention and therefore understand how the forum’s primary role as a communication mechanism informs its secondary role as a knowledge base.

## Research question
What makes an interesting topic on the OSM forum?

## Findings
H1) The high Gini coefficient (0.71) of views per topic suggests that relative interest in topics is highly unequal.

H2) There are positive relationships between views and number of replies (sublinear), and between views and unique authors (superlinear). This suggests that more discursive conversations (especially those with more unique authors) attract more attention.

H3) The weaker positive relationships between views and both conversation length and average reply time, lend less evidence to the notion that shallower conversations attract less attention.

H4) There are clear temporal patterns about when topics are created, however there were no significant correlations that suggested this has an effect on the level of interest.

## Methods
The data collected for the [previous paper]({{site.url}}/masters-accessing-data) was first aggregated by topic using Python's [pandas](https://pandas.pydata.org/index.html) library. This data was then exported as a csv file and analysed using R.

In R, I mainly relied upon base R for the analysis and the awesome [ggplot2](https://ggplot2.tidyverse.org/) package for visualisation (with a little help from the [Viridis package](https://cran.r-project.org/web/packages/viridis/vignettes/intro-to-viridis.html) for colour-blind print-friendly colours).    

## Limitations and improvements
- Because I relied on data that I had previously collected (given time limitations), some potentially useful and interesting variables for characterising conversations were ignored (e.g. number of words, sentiment of posts etc). In future, doing textual analysis of the content of conversations may be more interesting.

- I was limited to exploring univariate and bivariate analysis because of time constraints, however the strong correlations between independent variables for hypotheses 2 and 3 suggest that multivariate approaches may be more suitable.

- I also only looked at Forum as a whole, not the potentially interesting dynamics at a sub-forum level (for example comparing country sub-forums).  

## Reflections
- I really enjoyed playing around with ggplot2 again, even if the resulting graphics were limited by academic conventions. I particularly enjoyed the challenge of plotting high density data and getting to use the accessible Viridis colour palette.

- However, because most of the work I did during my master's, including scraping the data used in this paper, was done using Python I fully experienced the switching costs. Although ggplot normally brings me back to R, I think Python is way more useful overall, so I intend to focus on exploring some of the many visualisation libraries and options in future.  

- This module opened a window into the incredibly fascinating but complex world of temporal analysis, which is something I definitely need to look into more in the future.
