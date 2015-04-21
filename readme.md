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
  * Wrapping
  * Relevance

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
    on "<s, a, s', r>" tuples.
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
