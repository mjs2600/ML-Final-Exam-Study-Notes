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
    * 3. find the centers of the points
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
    * ![x_i](http://mathurl.com/2az2c7m.png) is strongly relevant if removing it degrades the Bayes' Optimal
      Classifier
    * ![x_i](http://mathurl.com/2az2c7m.png) is weakly relevant if
      * it is not strongly relevant
      * ![There exists](http://mathurl.com/yhy6gla.png) a subset of features **S** such that adding             ![x_i](http://mathurl.com/2az2c7m.png) to **S** improves Bayes' Optimal Classifier
      * ![x_i](http://mathurl.com/2az2c7m.png)  is otherwise irrelevant
  * Relevance vs. Usefulness
    * **Relevance** measures the effect the variable has on the Bayes' Optimal
      Classifier
    * **Usefulness** measures the effect the variable has on the _error_ of a
      _particular predictor_ (ANN, DT, etc.)

* Feature Transformation
  * PCA: [Good Slides](http://www.cc.gatech.edu/~agray/4245fall10/lecture18.pdf)
    * Example of an eigenproblem
    * Finds direction (eigenvectors) of **maximum variance**
    * All principal components (eigenvectors) are mutually orthogonal
    * Reconstructing data from the principal components is proven to have the
      least possible L2 (squared) error compared to any other reduction
    * Eigenvalues are monotonically non-increasing and are proportional to
      variance along each principal component (eigenvector). **Eigenvalue of 0
      implies zero variance which means the corresponding principal component
      is irrelevant**
    * Finds **"globally"** varying features (image brightness, saturation, etc.)
    * Fast algorithms available
  * ICA
    * Finds new features that are completely **independent** (from each other).
      i.e. they share no mutual information
    * Attempts to maximize the mutual information between the **original**
      and **transformed** data.  This allows original data to be reconstructed
      fairly easily from the transformed data.
    * Blind Source Separation (Cocktail Party Problem)
    * Finds **"locally"** varying features (image edges, facial features)
  * RCA
    * Generates random directions
    * It works! If you want to use it to preprocess classification data...
        * Is able to capture correlations between data, but in order for this to
          be true, you must often reduce to a larger number of components than
          with PCA or ICA.
    * Can't really reconstruct the original data well.
    * Biggest advantage is speed.
  * LDA
    * Requires data labels
    * Finds projections that discriminate based on the labels. i.e. separates
      data based on class.

* Information Theory
  * Entropy: [A characterization of uncertainty about a source of    information](http://en.wikipedia.org/wiki/Entropy_(information_theory))
    * ![Entropy Formula](http://mathurl.com/pdmz66k.png)
  * Joint Entropy: [The entropy contained by the combination of two variables](http://en.wikipedia.org/wiki/Joint_entropy)
    * ![Joint Entropy Formula](http://mathurl.com/l3t2ekl.png)
  * Conditional Entropy: [The entropy of one variable, given another](http://en.wikipedia.org/wiki/Conditional_entropy)
    * ![Conditional Entropy Formula](http://mathurl.com/pvq7nq4.png)
  * Mutual Information: [The reduction of entropy of a variable, given knowledge of another variable](http://en.wikipedia.org/wiki/Mutual_information)
    * ![Mutual Info Formula](http://mathurl.com/o7es4gh.png)
  * KL Divergence: [A non-symmetric measure of the difference between two probability distributions P and Q](http://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence)
    * ![KL Divergence Equation](http://mathurl.com/kld5umv.png)
    * Can be used in supervised learning as an alternative to squared error


###Reinforcement Learning

[Reinforcement Learning: A Survey](http://www.jair.org/media/301/live-301-1562-jair.pdf)

Put an agent into a world (make sure you can describe it with an MDP!), give him
some rewards and penalties and hopefully he will learn.

* Markov Decision Processes
  * Building a MDP
    * States
      * MDP should contain all states that an agent could be in.
    * Actions
      * All actions an agent can perform.  Sometimes this is a function of state,
        but more often it is a list of actions that could be performed in any state
    * Transitions (model)
      * Probability that the agent will arrive in a new state, given that it takes
        a certain action in its current state: P(s'|s, a)
    * Rewards
      * Easiest to think about as a function of state (i.e. when the agent is in a
        state it receives a reward).  However, it is often a function of a
        [s, a] tuple or a [s, a, s'] tuple.
    * Policy
      * A list that contains the action that should be taken by the agent in each
        state.
      * The **optimal policy** is the policy that maximizes the agent's long
        term expected reward.
  * Utility
    * The utility of a state is the reward at that state plus all the (discounted)
      reward that will be received from that state to infinity.
    * Accounts for _delayed_ reward
    * Described by the Bellman Equation
      * ![Bellman Equation](http://mathurl.com/oj75ljf.png)
  * Value Iteration
      * "Solve" (iteratively until convergence, more like hill climb) Bellman
        Equation.
      * When we have maximum utility, the policy which yields that utility can
        be found in a straightforward manner.
  * Policy Iteration
      * Start with random (or not) initial policy.
      * Evaluate the utility of that policy.
      * Update policy (in a hill climbing-ish way) to the neighboring policy that
        maximizes the expected utility.
  * Discount Factor, ![gamma](http://mathurl.com/pbhmxd.png) (typically between 0 and 1),
    describes the value placed on future reward.  The higher ![gamma](http://mathurl.com/pbhmxd.png) is,
    the more emphasis is placed on future reward.

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
