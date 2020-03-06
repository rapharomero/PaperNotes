# Conditional Network Embedding

### Network embeddings
A network embedding is a mapping from the set of nodes from a graph to a d-dimensional Euclidian space.
Embedding methods available at the moment usually try to find an embedding such that two similar nodes in the graph will be represented closeby in the embedding space.
They usually rely on three steps:
- Definition of the notion of similarity between two nodes of the graph
- Definition of the distance between points in the embedding space
- Definition of a cost function that will penalize large distance in the embedding space for similar points and small distances for dissimilar points.

### Limitations of previous methods
The current methods often fail to capture some structural information naturally present in the graph.

### Proposed method
CNE tries to incorporate this prior information by using a Bayesian approach:
- Definition of a prior distribution on the set of possible graphs.
- Definition of a distribution in the embedding space conditioned on the network.
- Maximization of the posterior distribution of networks conditioned on the embedding, with respect to the embedding, or equivalently with respect to the pair-wise distances between embedding points, which form a set of sufficient statistics.

### Optimization
The optimization problem is non-convex, is solved using block stochastic gradient descent,
