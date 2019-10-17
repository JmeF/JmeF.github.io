---
layout: project
type: Masters paper

images:
    - title: main
      image: "wrangling-data-figure1.png"
      image-description: "Number of links to US top-level domains on Wikipedia articles in 2009 and 2019."
    - title: second
      image: "wrangling-data-figure2.png"
      image-description: "Number of sentences in Wikipedia articles in 2009 and 2019."
    - title: third
      image: "wrangling-data-figure3.png"
      image-description: "Number of links to US top-level domains per sentence on Wikipedia articles in 2009 and 2019."

descriptive-title: "Assessing bias towards US sources on Wikipedia country articles"
description: "A short methods paper using text-analysis to determine whether Wikipedia articles have become more or less bias towards US 'authoritative' sources over 10 years."

tools:
  - Python
  - Regex
  - XML
methods:
  - text-analysis
  - data-cleaning

report:  'True'
gdocs-link: "https://docs.google.com/document/d/1GNzx0q5zNwGlTDNueV54sPtBS4ci9-2jtzLNCL1a_9k/"
code: 'True'
github-link: "masters-wrangling"

---
## Summary
This is a short project I did during my MSc to produce a methods paper that would demonstrate my ability to apply the skills we had been taught around cleaning and analysing unstructured text data to answer social science questions.  

Given XML file dumps of all 195 English Wikipedia pages on sovereign states, I chose to assess the bias towards the US in judging “reliable, authoritative" sources. To do this, I extract all the URLs of the cited sources and use the top-level domain to identify whether the source is US-based. Because the articles are likely to have grown over those 10 years and therefore need to cite more sources, I account for the length of the articles using number of sentences.

## Research question
Judging “reliable, authoritative sources”: Has Wikipedia become more or less biased in citing US sources?

## Background
One of the fundamental principles of Wikipedia is that it is written with a “Neutral Point of View”, underpinned by citations of “reliable, authoritative sources”. But as an open project in which anyone can edit, this principle is not always met, which can lead to systemic biases. These biases have been frequently demonstrated and attempts made to combat them by the community. This paper tests whether there are US-centric biases in the judgement of valid 'authoritative sources', and tests whether these have changed between 2009 and 2019.

## Findings
1) On average, there are significantly more links to US sources in the articles for 2019 (mean = 13.4) than for 2009 (mean = 8.7), (tested using a two-sided paired t-test).

2) However, on average, there are significantly more sentences in the articles for 2019 (480.9) than in 2009 (273.3).

3) Accounting for the difference in number of sentences, there is a significant decrease in the average number of links to US sources per sentence between 2009 (0.035) and 2019 (0.029), suggesting Wikipedia has become less biased.

## Methods and limitations


## Reflections
- Looking for open source libraries and test their effectiveness.
- With more time - Use of something other than just top-level domains, would be much better.
-
