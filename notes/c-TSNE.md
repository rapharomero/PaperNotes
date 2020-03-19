# Conditional t-SNE: Complementary t-SNE embeddings through factoring out prior information

### Goal of the paper
t-SNE is a widely used visualization tool that allows mapping high dimensional data into a low-dimensional space (typically 2).
This paper introduces conditional t-SNE, a generalization of t-SNE that factors out prior information in order to capture complementary information in the embeddings.

### t-SNE
In t-SNE, two distribution over the pairs of data points are defined: one using high dimensional representations and one using the low dimensional representations. Then the Kullback-Leibler divergence is minimized with respect to the low dimensional coordinates.  
*The two distributions can represent two ways of drawing a pair of points in the dataset at random.*

### Conditional t-SNE
Conditional t-SNE works the same way as t-SNE, but by taking into account prior information on the data points. This prior information is supposed to be categorical and is stored in a square binary matrix, representing whether or not two data points have the same label or not.  
Then the KL divergence between the distribution derived from high dimensional embeddings and the distribution derived from the low-dimensional embedding *conditioned* on the label matrix is minimized.  
Doing this ensures relieves the embedding from the task of ensuring that points in the same class have close representations.  
Indeed, using Bayes Rule this information can be captured in another factor, which is the likelihood of the label matrix given the pair of points that was drawn according to the distribution derived from the low-dimensional representations.  
An exponential model is used to model this conditional likelihood term. Its sufficient statistic is the element of the label matrix which coordinates correspond to the pair of points that was drawn randomly.

### Optimization
The resulting objective function that must be minimized can be written as the sum of attractive forces and repelling forces.  
It can be seen that the prior label information affects the repelling forces: if two points have the same label, we don't want them to be close to one another.  
In order to make the gradient evaluation feasable for big datasets, an approach derived from the Barnes-Hut tree algorithm is adopted.
It allows a final complexity in O(L . n . log(n)), L being the number of labels and n the number of data points.


Remarks:
- In the computation of the label conditional distribution, one must remind that the number of elements within each class is fixed by the label matrix given as input. Else the coefficients would have been found by counting the number of upper triangular binary matrix with the diagonal + 1 element fixed to 1.
- Even if the terms prior information is used in this approach, the method cannot be considered as Bayesian since we still try to estimate the precise locations of the low dimensional points, and not a distribution over all the possible sets of n 2-d data points.
