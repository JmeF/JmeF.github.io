---
layout: project
type: Master's paper
date: 2019-04-20

images:
    - title: main
      image: "Net-2019-graph.png"
      image-description: "Visualisation of the weighted co-contribution network within the OSM Forum social network for March 2019. Edges connect authors (nodes) if they comment on the same topic, width of the edge represents number of interactions and the colour indicates number of lifetime map edits by the authors connected."
    - title: first
      image: "Net-figure1.png"
      image-description: "Forum participation metrics over time."
    - title: second
      image: "Net-figure2.png"
      image-description: "Interaction inequality metrics over time."
    - title: third
      image: "Net-figure3.png"
      image-description: "Meritocracy metrics over time."
    - title: fourth
      image: "Net-figure4.png"
      image-description: "Decentralisation metrics over time."
    - title: fifth
      image: "Net-figure5.png"
      image-description: "Consistency metrics over time."

title: "Understanding the evolution of informal hierarchies in OpenStreetMap"
description: "A paper using social network analysis of the OpenStreetMap Forum to explore the role of informal hierarchies within the OpenStreetMap community and understand how they change over time."

tools:
  - Python
  - R
  - Gephi
methods:
  - social-network-analysis
  - data-visualisation

report:  'True'
gdocs-link:  "https://docs.google.com/document/d/12grM5MfXpo88YOP7FeABqvumwlrL_wyY9rUpt5oZLD8/"
code: 'True'
github-link:  "masters-social-networks-osm"
---

## Summary
This is a project I did for an option paper during my MSc, the goal of the paper was to apply social network analysis to a relevant social science question.

As with many of my MSc projects, I chose to focus on [OpenStreetMap (OSM)](https://openstreetmap.org/) and in particular how the project is organised given the lack of 'traditional' mechanisms for coordinated action. For this project, I focused on the latent social structures implied from communication patterns on the [OSM Forum](https://forum.openstreetmap.org/). In particular, I focused on understanding whether there was evidence of informal hierarchies among contributors which are implied by previous research into the high levels of inequality between the number of contributions by different contributors.

To do this I used data I had gathered from the forum in a [previous project]({{site.url}}/project/masters-accessing-data) to create manifest social networks between forum users based on common topics they posted on. I created temporally overlapping networks for every 30 day period the forum was active (creating a network every 15 days), and calculated a set of metrics for each network. I then analysed these metrics over time to determine whether centralised hierarchies were active on the forum and how they changed over time.

## Background
The motivation for this project arises from existing theoretical and empirical study of commons-based peer-production projects (e.g. Wikipedia, open source software and OpenStreetMap). Much of this literature observes highly unequal contributions between contributors, with a small proportion of users providing the majority of 'edits'. While this has in many cases been taken to infer that such projects exhibit hierarchical organising and governance behaviours, relatively little work has studied the direct existence of hierarchies.

Previous work that has focused on the existence of hierarchies emphasises the importance of such hierarchies in providing a coordinating function for contributors. It is often emphasised that such structures are based on social norms and rough consensus, and that they are often limited, meritocratic, decentralised and transparent. This project aims to directly interrogate these features of informal dynamic hierarchies through the use of contributor communication patterns.

To understand the role of informal hierarchy, I focused on five key features suggested in previous work:

1) _**Participation**_ -- the proportion of users who are involved in the 'main conversation'.

2) _**Influence inequality**_ -- the inequality between participants in terms of who they interact with and how often.

3) _**Meritocracy**_ -- whether contributors are more likely to be associated with others who demonstrate similar levels of effort.

4) _**Decentralisation**_ -- whether different sub-communities form or whether all conversations involve the same people.

5) _**Persistence**_ -- whether the same people participate in the forum all the time.

## Research question
What is the role of hierarchy in the informal governance of OpenStreetMap?

## Findings
Some of the key findings in from [the paper]({{page.gdocs-link}}edit?usp=sharing) include:

1) The is strong evidence that some hierarchies do exist (top 10% of participants account for 50-60% of all interactions) but these hierarchies are primarily self-selective and participatory in nature (any individual appears to be able to participate in central discussions).

2) There is evidence that hierarchies are to some extent embedded (relatively high level of persistence in the top 10%) and they are to some extent decentralised but it is relatively inconclusive on whether they are organised around meritocratic principles.

3) Examining the evolution of hierarchies, it is possible to identify three distinct periods of development: [1] the rise of influential participants (2008-2011) [2] Rising decentralisation and equality of influence (2012-2016) [3] Stalling of decentralisation and equality (2017-2019). The last period is particularly interesting as it has not been examined in depth across different peer-production projects.

## Methods
The forum data used (from the [previous project]({{site.url}}/project/masters-accessing-data)) included over 700’000 forum posts in over 40’000 topics providing a full historical record of the forum from June 2006 to February 2019. However, data from before 2008 was sparse so only data from January 2008 was actually used in the analysis.

From this data, 18’505 unique OSM display usernames were identified, however, OSM usernames can be changed and records of these changes are not officially stored by the project. Using a [third-party database](https://github.com/Zverik/whosthat) of name changes (tracking username changes through user edits to the OSM database) and [OSM profiles](https://www.openstreetmap.org/user/JamieF1) (which are keyed on current display name), I was able to extract and identify 18’297 unique accounts, along with the number of edits each account provided.

Using this data, I then created a set of weighted, undirected networks representing the existence and strength of interactions between participants in informal governance discussions (covering 30 days of activity, sampled every 15 days). I created these networks by making unweighted bipartite graphs connecting OSM accounts to forum topics and then projecting this network so that any two accounts that post in the same topic are connected with weight determined by how many topics they both post in over those 30 days.

For each constructed network, I derived a set of network measures that aligned to each of the key areas identified and then analysed how these changed over time. The network measures used were:  

1) _**Participation**_ -- percentage of nodes in the largest connected component (LCC). To identify how many participants are actively involved in the main community discussions.

2) _**Influence inequality**_ -- Gini coefficient of the degree and weighted degree distributions. To characterise the level of inequality between contributors in terms of number of connections and number of interactions.

3) _**Meritocracy**_ -- weighted degree assortativity, and assortativity and modularity by number of edits. To identify whether similarity between contributors (in terms of similar levels of demonstrated effort/commitment) influences whether they interact with one another.

4) _**Decentralisation**_ -- modularity, number of communities and Gini coefficient of community size when community partitioning is used (Louvain algorithm). To discover if distinct communities exist (although community detection algorithms can be inexact in identifying ‘true’ sub-communities).

5) _**Persistence**_ -- Jaccard similarity index (which tests the overlap between two sets) for overall participants, LCC and top 10% between sequential non-overlapping 30 day periods. To understand    
turnover in participants over time.

For this analysis I mainly used Python for the data wrangling and network creation (with significant use of the excellent [networkx library](https://networkx.github.io/)). I also used R (mainly ggplot2 as usual) for the analysis and visualisation. All code can be found in this [Github repo](https://github.com/JmeF/{{ page.github-link }}).

## Limitations, improvements and reflections
- Social network analysis is a very interesting, useful and powerful method, however it can be difficult to map metrics onto existing concepts and interpret the outputs. Careful consideration about the context of what you are representing is key to successful analysis.

- One of the main limitations of analysing networks over time is that time-slice approaches are very difficult to analyse using traditional inferential statistics. There are some methods for doing this that are available ([Stochastic Actor-Oriented Models](https://www.stats.ox.ac.uk/~snijders/siena/SAOM_ARStat1.pdf) are particularly exciting to me) but in many cases they have limitations that make them unsuitable for large complex networks (max number of nodes, no change in nodes between time steps etc).

- A key suggested improvement highlighted by reviewers was to engage the community with the findings from the study and interview forum users to understand whether the network findings seemed familiar and also to understand if there were any underlying or precipitating events that lead to the observed evolution in the community. 
