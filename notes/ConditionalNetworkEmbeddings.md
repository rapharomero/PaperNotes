# Conditional Network Embedding

### Network embeddings
A network embedding is a mapping from the set of nodes from a graph to a d-dimensional Euclidian space.
Embedding methods available at the moment usually try to find an embedding such that two similar nodes in the graph will be represented closeby in the embedding space.
They usually rely on three steps:
- Definition of the notion of similarity between two nodes of the graph
- Definition of the distance between points in the embedding space
- Definition of a cost function that will penalize large distance in the embedding space for similar points and small distances for dissimilar points.

### Limitations of previous methods
The current methods often fail to capture some structural information naturally present in graphs.

### Proposed method
CNE tries to incorporate this prior information by using a Bayesian approach:
- Definition of a prior distribution on the set of possible graphs.
- Definition of a distribution in the embedding space conditioned on the network.
- Maximization of the posterior distribution of networks conditioned on the embedding with respect to the pair-wise distances between embedding points, which form a set of sufficient statistics.

### Optimization
The optimization problem is non-convex, is solved using block stochastic gradient descent.

### Evaluation and Results
The method is evaluated on two problems: link prediction and multi-label node classification.
- On link prediction, CNE with uniform prior outperforms the other methods on 4/6 of the datasets tested, while with the degree prior it outperforms them all.
- For multi-label classification, the CNE used as an input to a logistic regression (CNE-LR) performs relatively well, while casting the classification into a link prediction problem leads to results outperforming almost all the other tested methods, apart from LINE which gives a better micro-F1 score on the Wikipedia dataset.

CNE is also evaluated qualitatively through the visualization of multi-relational data. It is shown that a suitable prior (e.g degree prior) will conduct to a more informative embedding on the prof/course/student dataset compared to a uniform prior.
