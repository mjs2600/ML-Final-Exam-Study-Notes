<head>
  <script type="text/javascript"
    src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
  </script>
</head>

##Content Overview/Important Concepts
More detailed info and reading can be found in the repo subdirectories

### Wiki Study Guide
http://wiki.omscs.org/confluence/display/CS7641ML/CS7641.FA14.+Final+exam+prep

###Unsupervised Learning
UL consists of algorithms that are meant to "explore" on their own and provide  
the user with valuable information concerning their dataset/problem  
* Randomized Optimization
* Clustering
  * Single Linkage
  * k-Means
    * 1. Place k centers
    * 2. Claim closest points
    * 3. find the centers of the pioints
    * 4. Move the centers to the clusters of points
    * 5. Unless converged GOTO 2
  * Expectation Maximization
    * Gaussian Means
    * Uses expectation and maximization steps

* Feature Selection
  * Filtering
    * Choose features independent of learner. i.e. "filter" the data before it
      is passed to the learner
    * Faster than wrapping (don't have to pay the cost of the learner)
    * Tends to ignore relationships between features
    * Decision Trees do this naturally (Filter on information gain)
  * Wrapping
    * "Wrap" the learner into the feature selection.  Choose features based on  
      how the learner performs.
    * Takes into account learner bias
    * Good at determining feature relationships (as they pertain to the success
      of the learner)
    * Very slow (have to run the learner for each feature search)
    * Speed Ups
      * Randomized optimization
      * Forward/Backward sequential selection: [good description and
        implementation](http://sebastianraschka.com/Articles/2014_sequential_sel_algos.html)
  * Relevance
    * $x_i$ is strongly relevant if removing it degrades the Bayes' Optimal
      Classifier
    * $x_i$ is weakly relevant if
      * it is not strongly relevant
      * $\exists$ a subset of features $S$ such that adding $x_i$ to $S$
        improves Bayes' Optimal Classifier


* Feature Transformation
  * PCA
  * ICA
  * LDA
  * RCA

* Information Theory
  * Mutual Information
  * ...

###Reinforcement Learning
Put an agent into a world (make sure you can describe it with an MDP!), give him
some rewards and penalties and hopefully he will learn.

* Markov Decision Processes
  * States, Transitions, Rewards
  * Policy Iteration
  * Value Iteration

* Model-Based vs. Model-Free
  * Model-Based requires knowledge of transition probabilities and rewards
    * Policy Iteration
    * Value Iteration
  * Model-Free gets thrown into the world and learns the model on its own based  
    on "[s, a, s', r]" tuples.
    * Q Learning

* Q Learning
  * Learning Rate
  * Exploration vs Exploitation
  * Epsilon Greedy

* Game Theory
  * Zero Sum Games
  * Nash Equilibria
  * Subgame Perfect, Plausible Threats
  * Pavlov
  * Repeated Games
  * Tit-for-tat
  * Minimax, Maximin
  * Feasible Regions
