# UMAP: Uniform Manifold Approximation and Projection for Dimension Reduction

### Goal of the paper
This paper introduces a neighbor graph based dimension reduction method called UMAP.
This methods proves to be competitive with state-of-the-art methods such as t-SNE for visualization. It also has the advantage of preserving more of the global structure of the input data, with superior performances in terms of run time. In particular, the algorithm has no computational restriction on the embedding dimension, and is able to scale on huge data sets.

### Principle of the method
This method makes use of notions from manifold theory and topological data analysis to construct a topological representation of the high dimensional input data.
The same operation is performed on the low dimensional representation.
Then the Cross-Entropy between these two representation is minimized with respect to the layout of the low dimensional representation.
So for each representations, the operation breaks down into two steps:
- Approximation of the manifold on which the data is supposed to lie.
- Construction of a fuzzy topological sets representation of the approximated manifold.


### Manifold Approximation
The goal here is to approximate the manifold where the data lies by a Riemannian manifold such that *the data is approximately uniformly distributed according to the associated metric*.  
A Riemannian metric is defined in the neighborhood of each data point, by normalizing the ambient distance by the distance to the k-th nearest neighbor of the data point. A Lemma proven in the paper justifies this solution.  
Doing this makes the hypothesis that the data is uniformly distributed hold *for the metric that is introduced*.

### Fuzzy topological sets representation
The previous step allows to define a family of metric spaces, each of which having the property that the data is uniformly distributed with respect to their Riemannian metric.  
The problem now is that there are several independent notions of distance, one for each data point, and those can be incompatible. So the metric spaces need to be "glued" together in some sense, that is why fuzzy topology is useful here.  
Each independent metric space is mapped to a fuzzy simplicial set using a functor (the fuzzy singular set functor, defined in the paper).  The metric information is encoded in the fuzzy structure, while the topological information is captured in the topology of the sets.  Then a fuzzy union is performed over all the resulting sets to obtain the final fuzzy set representation of the data.

### Optimizing the low-dimensional layout
The low dimensional layout is obtained by minimizing the cross entropy between the fuzzy set representation of the high dimensional spaces and the low dimensional one.
