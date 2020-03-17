# DeBayes: A Bayesian method for debiasing network embeddings

### Goal of the paper
This paper proposes a method that allows finding network embeddings that avoid discrimination based on criteria such as age, gender, race etc...
To do so, a Bayesian method is proposed, using a biased Prior so that the posterior result is significantly less biased with respect to usual fairness metrics.

### Fairness of an embedding
The fairness of an embedding can be assessed through measuring its **obfuscation**, which quantifies the generalization error of a classifier trained on a subset of the nodes using the embedding.

### Fairness in the context of link prediction
In the context of link prediction, we model sensitive attributes as a function from the set of nodes to a set of possible attributes (e.g. male/female).
The idea of Fairness is to build models that are the less biased as possible with respect to these sensitive attributes.
For link prediction, the fairness of a classifier can be computed using statistics on the pairs of sensitive attributes.
Here are examples of fairness measures:
- **Demographic parity**: the mass of predicted links should be equally distributed between the sub-groups of population defined by the attribute values.
 On the predicted adjacency matrix, this is equivalent to forcing all the means over each block defined by the sensitive attribute value to be equal. The drawback of this approach is that it can lower the performances of the link prediction.
 - **Equalized opportunity**: Equalized opportunity ensures that the mass of true positive is equally distributed over between the subgroups of the population. On the predicted adjacency matrix, the mean is computed over the coefficients corresponding to edges that were observed in the data.
 - **Acceptance rate parity**: the acceptance rate between two subgroups is the proportion of edges that appear it the top-k% highest prediction scores. The acceptance rate parity is the variance of this quantity over the possible attribute value pairs.

### DeBayes method
DeBayes methods makes use of the CNE framework to compute a debiased network embedding.  
The prior is determined by finding the Maximum Entropy distribution of the possible graphs, under a constraint on the expected number of neighbours having each sensitive attribute. (This expectation must be equal to the observed one).  
Then the embedding is computed using Bayes and by solving the Maximum Likelihood problem.  
The link prediction problem can then be solved since the posterior probability factorizes with respect to the edges, so the edges probabilities can be computed directly using marginalization.

### Evaluation
The model is evaluated on the problem of link prediction on two datasets: DBLP(co-authorship network) and Movielens-100k (recomander system dataset).  
It is compared to Compositional Fairness Contraints, Fairwalk and a uniformly random link predictor.  
The Representation Bias is measured using 2 classifiers : Logistic Regression and SVM with non-linear kernel.  
The DeBayes method yields good results both in terms of high-level fairness measures, as well as on prediction quality.

##### Personal Remarks:
- Visualizing the fairness prior in terms of statistics over blocks of the adjacency matrix can be useful.
- Eq (2): if we sum over Vs, is the conditioning still needed on the left term of the equation?
