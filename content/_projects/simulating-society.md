---
layout: project
type: Masters paper
date: 2019-03-10

images:
    - title: first
      image: "sim-soc-figure-1.png"
      image-description: "Distribution of different strategies in each market type (for 25 companies)"
    - title: second
      image: "sim-soc-figure-2.png"
      image-description: "Results of Experiment 1 (100 simulations for each of the seven market distributions)."
    - title: main
      image: "sim-soc-figure-3.png"
      image-description: "Results of Experiment 2 (100 simulations for each of the seven market distributions by varying number of companies)."

title: Simulating open source software development in different markets
description: A short methods paper using an Agent-Based Model based on an iterative n-player prisoners dilemma to understand under what conditions private companies contribute to open-source software development.

tools:
  - NetLogo
  - R
methods:
  - agent-based modelling

report:  'True'
gdocs-link:  "https://docs.google.com/document/d/1LT8oJ-fT8fNcZIsCVpLpdIRQ-mkv9yTbqa4-EjcUPgU/"
code: 'True'
github-link:  "agent-based-model-oss-development"

---
## Summary
This is a short (one week) project I did during my MSc to produce a methods paper that would demonstrate my ability to apply Agent-Based Models (ABMs) to social science questions.

[ABMs](https://en.wikipedia.org/wiki/Agent-based_model) enable the simulation of emergent complex systems by ascribing behaviours to individual agents and enabling them to interact in an simulated environment. For this paper, I chose to focus on how different market conditions might lead companies to contribute to the development of open-source software (OSS).

I based my model on an extended iterative version of the [N-player Prisoner’s Dilemma (NPD)](https://cs.stanford.edu/people/eroberts/courses/soco/projects/1998-99/game-theory/npd.html) (see [Power 2009](http://jasss.soc.surrey.ac.uk/12/1/8.html) for more details). In essence, the model simulates the amount of proprietary and OSS development by companies interacting in a market, and the 'value' they derive from this. Individual company behaviour is dictated by a desire to create value, the behaviour of other companies and informed by one of five different company strategies which dictate their attitude to OSS contribution (Idealist, Early adopter, Trend follower, Skeptic, Holdout). To test the impact of market conditions, I established seven different 'market' configurations based on the number of companies adopting each strategy.

Finally, I performed two experiments consisting of 100 simulations for each of the seven markets and monitoring the output in terms of overall market value and overall level of OSS contribution. The first experiment fixed all possible input parameters, while the second varied the number of companies in each market.

## Background
OSS development by companies has all the hallmarks of a [collective action problem](https://en.wikipedia.org/wiki/Collective_action_problem), where collective benefits can be derived from cooperation but individual motivations to cooperate are limited. The key question presented is why would companies engage in the apparently paradoxical activity of developing software their competitors could also use. To answer this question, I focus on how the perception of value from developing open source software might lead companies in some markets to embrace OSS while others may ignore it.

## Research question
In what types of markets do companies develop open source software?

## Findings
1) Best performing markets: D (normally distributed), optimistic (skewed idealistic), S (lots of sceptics and idealists)

2) Worst performing markets: C (skewed towards extremes), pessimistic (skewed sceptical), S-1 (lots of early adopters and holdouts)

3) The model infers that recognising the most collective benefits from OSS development relies more on encouraging companies to follow trends than it does on inspiring idealists or persuading holdouts.

## Methods
The project mainly focused on adapting and extending the NPD, implementing an ABM with relevant parameters and running experiments. The main adaptation of the NPD was to change the agents' (companies') decision from a binary choice cooperation/defection to a sliding scale of how much OSS vs proprietary production could be done in each round. Given a set level of production, each company could allocate some proportion to OSS and the remainder to proprietary production. They could only change it one unit per round depending on previous market payoff.

The payoff function was designed accordingly to take into account both individual proprietary production and total market OSS production. Strategies were then designed that made the decision based on a level of openness to OSS contribution. Experiments consisted of 100 simulations of 200 decision rounds for each possible permutation of the unfixed parameters, for each market. See the [paper]({{ gdocs-link }}) for more details.

The whole model was coded from scratch using [NetLogo](http://ccl.northwestern.edu/netlogo/), a multi-agent programmable modelling environment, in a way that is designed to enable future extendibility. The experiments were each conducted using the BehaviourSpace tool within NetLogo, which enables repeated runs with different sets of fixed parameters. The resulting data was analysed and visualised using [R](https://www.r-project.org/), with significant usage of the [ggplot2](https://ggplot2.tidyverse.org/) visualisation library. All code can be found on [GitHub](https://github.com/JmeF/{{github-link}}).

## Limitations and improvements
There were many limitations to the ABM, mainly due to time constraints, that mean the model is primarily aimed at discovering potential patterns rather than directly represent reality (such models are sometimes referred to as 'toy models'). One of the key issues, is that neither the micro behaviour of companies nor the macro behaviour of markets has been validated against observed data.

There are a number of improvements, beyond validation, that could benefit the model by making it more realistic, including:

1) Varying the size of different companies in each market to study the effects of large organisations attitudes on overall results. For example, what is the effect of one big holdout and what happens if they become an early adopter).  

2) Enabling agents to adopt adaptive strategies that also change based on the behaviour of others. For example, if companies adopt strategies that match their competitors is OSS likely to grow rapidly in some cases and never exist in others.  

## Reflections
- NetLogo is a great tool to start out playing around with ABMs. Although similar results can be relatively easily achieved in general programming languages, the GUI is a lot more accessible for building models you want to share.

- It is **very** easy to go too deep when designing ABMs. Getting a basic functional model and then taking an iterative approach to adding new parameters as they are needed definitely helps.

- The real difficulty with toy ABMs is that it is sometimes difficult to tell whether the results you get are well reasoned or whether they simply present your biases back to you. The only way to counter critique of bias is to ensure your modelling assumptions are transparent, justified and well evidenced.
