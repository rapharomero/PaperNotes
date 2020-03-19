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
Doing this ensures that the lower dimensional embeddings don't have the burden of ensuring that points in the same class have close representations.  
Indeed, using Bayes Rule this information can be captured in another factor, which is the likelihood of the label matrix given the pair of points that was drawn according to the distribution derived from the low-dimensional representations.
