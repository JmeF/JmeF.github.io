---
layout: project
type: Masters paper

images:
    - title: main
      image: "accessing-data-log-figure.png"
      image-description: "Number of contributors to the forum by the number of contributions they made, both on a log-transformed axis.
                          The diagonal straight line indicates there is a power-law distribution of contributions by different contributors."
    - title: secondary
      image: "accessing-data-hist-figure.png"
      image-description: "Histogram of contributors to the forum by the number of contributions they made."

descriptive-title: "Scraping the OpenStreetMap forum to understand participation"
description: "A short methods paper using automated web-scraping of the OpenStreetMap online forum to understand whether
the majority of posts come from a selective community of contributors or 'crowds' of interested individuals."

tools:
  - Python
  - HTML
  - RSS
methods:
  - web-scraping

report: 'True'
gdocs-link: "https://docs.google.com/document/d/1ZZvyY366r5glFlgblz3Sf2mJO8DrmmfNOvVCcaETHnQ/"
code: 'True'
github-link: "masters-accessing"

---
## Summary
This is a short project I did during my MSc to produce a methods paper that would demonstrate my ability to apply the skills we had been taught around collecting structured and unstructured data from the web to social science questions.  

I chose to focus on [OpenStreetMap (OSM)](https://openstreetmap.org/) and in particular the nature of communication and collaboration around the project. Looking at the [OSM Forum](https://forum.openstreetmap.org/), I aimed to understand whether communication among OSM Forum users demonstrated similar characteristics to previous observations around the distribution of effort among contributors to the OSM database and similar initiatives. Namely, I wanted to find out whether there were similarly substantial inequalities between the amount of posts made by different users.

To do this I used Python to systematically scrape data from the HTML and RSS feeds available on the forum. I then created visualisations and performed statistical analysis to compare the results to previous findings.

## Background
OSM is a global project which aims to create a free, openly licensed database of geographic information through mass collaboration, often described as the ‘social production of knowledge’. Previous research has frequently identified that OSM and similar projects tend to rely heavily on a small number of highly active contributors to produce the majority of work (community model), rather than a very large number of casual contributors (crowd). In many cases, the distribution of work/effort can exhibit power-law characteristics.

## Research question
Does the OpenStreetMap Forum reflect a crowd or community model of participation?

## Findings
1) The results appear to show that communication levels are highly unequal between users of the forum, clearly mirroring previous findings.

2) Just over 90% of users provide less than the mean number (39) of contributions (posts) suggesting the forum is strongly centred on a community model of participation.

3) Further evidencing this inequality, the top 10% of users account for almost 90% of total posts.

## Methods and limitations
The basic approach was to navigate through all the pages on the site from the index page, through each sub-forum to identify all the topics and then collect data on each post (at first from the RSS feed and then using HTML scraping if posts on popular topics were not collected).

I used Python in a Jupyter Notebook, using the following libraries:
- [requests](https://github.com/kennethreitz/requests ) to access webpages.
- [BeautifulSoup4](https://pypi.org/project/beautifulsoup4/) to parse HTML.
- [feedparser](https://github.com/kurtmckee/feedparser) to parse RSS feeds.
- [Pandas](https://pandas.pydata.org/index.html) to store and manipulate data.
- [seaborn](https://seaborn.pydata.org/) to visualise data.

There were many issues with this approach, given the short timeframe of the module (4 weeks) and the project (1 week). One of the key issues I faced was failing to check how many records were served by the RSS feeds and then realised that it only provided the most recent 15 records. Where topics had more posts, I quickly had to develop an HTML scraping approach to collecting the same data (which I had never done before and was not taught to us). I also faced limitations with efficiency in the collection process, particularly in storing the scraped data in limited laptop memory and handling errors. Each of these were later addressed in my thesis where I repeated the data collection process using an HTML only approach, writing the data to a csv object in memory and handling errors better.  

## Lessons
- The most important lesson learned during this project was to get to know the site I was scraping, check the data being collected throughout the process and quickly adapting to issues.
- Also emphasised throughout this project was a need to carefully consider what data was relevant to collect, not only from a technical standpoint but also from an ethical direction.
- I also learned the importance of effective error catching approaches (although I did not manage to implement a fully effective design during this process).
