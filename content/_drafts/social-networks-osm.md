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

To do this I used data I had gathered from the forum in [a previous project]({{site.url}}/masters-accessing-data) to create manifest social networks between forum users based on common topics they posted on. I created temporally overlapping networks for every 30 day period the forum was active (creating a network every 15 days), and calculated a set of metrics for each network. I then analysed these metrics over time to determine whether centralised hierarchies were active on the forum and how they changed over time.

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
(only some from original paper)
1) Hierarchies exist -- but self selective

2) General characteristics - somewhat embedded (relative high persistence in top 10%), decentralised but unclear on meritocratic

3) Three time periods -- rise of influential participants (2008-2011); Rising decentralisation and equality of influence (2012-2016); Stalling of decentralisation and equality (2017-2019) [last period not observed before]


## Methods
- Data from previous paper
700’000 individual records of posts in over 40’000 individual topics + full historical record of posts from June 2006 to February 2019

- Identifying unique authors
 -- From this data, 18’505 unique OSM usernames were identified. However, OSM usernames can be changed but these are not recorded in the data collected, so OSM unique IDs for each username were extracted from a project database to identify 18’297 unique accounts. For each unique account, the number of map edits made was collected
Tools:
Python (Pandas) -- WhosthatAPI and OSM user pages

- building networks -- create a set of weighted, undirected networks representing the existence and strength of interactions between participants in informal governance discussions ( 30 days covered every 15 days)
To create the network -- make unweighted bipartite graph (two sets of nodes – contributor accounts and topics. Edges in this network connect contributor accounts to the topics they have posted in at least once over those 30 days.) - project with weights
Tools:
Python networkx + Pandas

- analysis - network measures + then analyse changes over time

1) _**Participation**_ -- percentage of nodes in the largest connected component (LCC) gives a relative indication of how many participants are actively involved in the ‘community’ which carries out governance and thus how participatory the processes are.

2) _**Influence inequality**_ -- Gini coefficient of the degree and weighted degree distributions. This gives a characterisation of the level of inequality between contributors in terms of the people they are connected to and the overall number of interactions they have.

3) _**Meritocracy**_ -- weighted degree assortativity, and assortativity and modularity by number of edits. This gives an indication of the extent to which participation in the forum and contribution to the map is linked to whether two contributors connect.

4) _**Decentralisation**_ -- Decentralisation is tested through community partitioning using the Louvain algorithm and reporting the resulting level of modularity, number of communities and Gini coefficient of community size. This gives some indication of the extent to which distinct communities exist, although community detection algorithms can be inexact in identifying ‘true’ sub-communities.

5) _**Persistence**_ -- The level of change in participation in informal processes is calculated using a Jaccard similarity index, which tests the overlap between two sets. This gives the proportion of contributors in the LCC for two sequential time windows.

tools:
Python networkx + R ggplot2

## Limitations, improvements and reflections
- power and difficulty of networks - knowing what to measure and how

- Limitations -- time-slice networks don't feel super adequate but many network methods for dealing with time are limited (and limited to set number of nodes etc) - excited by SOAMs

- c
