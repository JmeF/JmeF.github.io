---
layout: project
type: Masters paper
date: 2019-02-16

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

title: "Assessing bias towards US sources on Wikipedia country articles"
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
This is a short project (one week) I did during my MSc to produce a methods paper that would demonstrate my ability to clean and analyse unstructured text data to answer social science questions.  

Given XML file dumps of all 195 English Wikipedia pages on sovereign states, I chose to assess the bias towards the US in judging “reliable, authoritative" sources. To do this, I extracted all the URLs of the cited sources and use the top-level domains (TLDs) to identify whether the source is US-based/-centric. Because the articles are likely to have grown over those 10 years and will therefore need to cite more sources, I account for the changing length of articles by comparing the number of sentences in each of the years.

## Research question
Judging “reliable, authoritative sources”: Has Wikipedia become more or less biased in citing US sources?

## Background
One of the fundamental principles of Wikipedia is that it is written with a “Neutral Point of View”, underpinned by citations of “reliable, authoritative sources”. But as an open project in which anyone can edit, this principle is not always met, which can lead to systemic biases. These biases have been frequently demonstrated and attempts made to combat them by the community. This paper tests whether there are US-centric biases in the judgement of valid 'authoritative sources' and whether these have become more or less pronounced over time.

## Findings
1) On average, there are significantly more links to US sources in the articles for 2019 (mean = 13.4) than for 2009 (mean = 8.7), (tested using a two-sided paired t-test).

2) However, on average, there are significantly more sentences in the articles for 2019 (480.9) than in 2009 (273.3).

3) Accounting for the difference in number of sentences, there is a significant decrease in the average number of links to US sources per sentence between 2009 (0.035) and 2019 (0.029), suggesting Wikipedia has become less biased.

## Methods
The approach consisted of two main steps; (1) I identified all links to sources in each article, extracted the TLD and classified it based on the [Public Suffix List](https://www.publicsuffix.org/). (2) I identified the main body of the article by stripping away supplementary sections and markup, then I counted the number of sentences using regular expressions (sentence regex = `r"(?:[A-Z][^\.!?]*[\.!?])"`{:.python}).   

I then assessed bias by using simple bivariate statistical analysis to test the difference between means for the two paired year samples (2009, 2019), each containing 190 valid country records.

Key Python modules and libraries used:
- [Pandas](https://pandas.pydata.org/index.html) - for organising and manipulating data.
- [BeautifulSoup4](https://pypi.org/project/beautifulsoup4/ ) - for manipulating XML data.
- [re](https://docs.python.org/2/library/re.html) - for matching text patterns.
- [MediaWikiParserFromHell (MWParser)](https://github.com/earwig/mwparserfromhell) - for parsing MediaWiki markup language used by Wikipedia.
- [tldextract](https://github.com/john-kurkowski/tldextract) - for extracting top level domains.
- [scipy](https://scipy.org/scipylib/index.html) - for statistical analysis.
- [seaborn](https://seaborn.pydata.org/) - for visualisation.

## Limitations and improvements
Given only a short amount of time, there were three main limitations in the project. (1) There was only a relatively weak (~0.45) correlation between number of sentences and number of US sources for both years, which means that other confounding variables may need to be accounted for (e.g. overall number of links). (2) Classification of sources by generic URL TLDs is a very limited approach to identifying whether a source is US-based or not. With more time it would be better to perform better geographic classification based on URLs, for example using IP addresses. (3) With more time and better geographic classification, it would perhaps be better to identify disparities between localised sources (from the country that the page is about) vs all 'foreign' sources (i.e. not just US), this would be particularly interesting looking at global north vs global south dynamics.

## Reflections
I love open source code. For many years I have been a proponent of open approaches (open source, open data, open content etc - see my [publications]({{site.url}}/publications)), however this project was the first time I really came to directly appreciate the practical benefits of these approaches in my work under significant time pressure.

In particular the [MWParser](https://github.com/earwig/mwparserfromhell) and [tldextract](https://github.com/john-kurkowski/tldextract) libraries, the latter based on the Mozilla [Public Suffix List](https://www.publicsuffix.org/) really helped me complete this project without reinventing the wheel. However, I was also cautious about using these random libraries I found on GitHub in an academic context, so I devised several simple tests to ensure they were behaving as expected and better than my own crude attempts at similar functionality. They both excelled in these tests which gave me the confidence and the proof I felt I needed to implement analysis around them.   
