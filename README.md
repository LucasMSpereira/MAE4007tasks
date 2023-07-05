# MAE4007tasks

Solutions of assignments from discipline "Inference in Stochastic Processes".

## Markov chain

A (first order) Markov chain is a stochastic sequence of elements in which the probability of the next element depends on the previous one.

This model is parametrized by the transition matrix Q. Element $q_{ij}$ contains the probability of the transition i -> j: going to j when the current element is i. 'i' and 'j' come from the alphabet: all possibilities of elements.

Inference in this model means determining the transition matrix Q. An empirical approach is the following:

<ul>
  <li>Count the occurrences in the sequence of all possible i -> j transition pairs.</li>
  <li>Arrange into the empirical transition matrix $Q_{ij}$.</li>
  <li>Divide each element in the matrix by the total sum of its row (maximum likelihood estimator).</li>
</ul>

## BIC for context trees

Markov chains can have arbitrary order k, meaning the model may look at the last $k \in N^{*}$ symbols to determine the distribution over the next symbol of the sequence. Variable length Markov chains (a.k.a. context trees) generalize this model even further. Now it's able to examine a variable number of past symbols ("context") to determine the probabilities of the next element.

This rich and efficient model is parameterized by a tree. Its root is empty, and its nodes contain words (sequences of symbols) of lenghts increasing with depth. At the leaves, there are contexts, words used to define the distribution over the next symbol in the sequence. The image below (from the article [Bayesian Context Trees: Modelling and Exact Inference for Discrete Time Series](https://academic.oup.com/jrsssb/article/84/4/1287/7073257)) illustrates a context tree from a process with alphabet `[0, 1, 2]`.

![image](https://github.com/LucasMSpereira/MAE4007tasks/assets/84910559/9aae8b61-38c9-4026-a788-b43a43a15e6d)

This repository includes a notebook (`./notebooks/ContextTreeBIC.ipynb`) which uses the method of Bayesian Information Criterion (BIC) to build the context tree of a sequence, and uses the depth of the pruned tree to determine the order of the Markov chain. BIC for context trees was proposed in the article [Context tree estimation for not necessarily finite memory processes, via BIC and MDL](https://ieeexplore.ieee.org/document/1603768).

## Hawkes processes

Hawkes processes are a class of self-exciting point processes: events occur in random instants in continuous time, and spawn other points with their own processes. The PDF `./HawkesBayesInference.pdf` contains a presentation summarizing the article [Bayesian Inference for Hawkes Processes](https://link.springer.com/article/10.1007/s11009-011-9272-5).
