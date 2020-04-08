#Hypergraph models of playlist dialects

## Goal of the paper
A playlist generation model is proposed. It is based on a modelling of playlist dialects using a structure called hypergraphs.
It is shown that the use of category-specific model can yield better accuracy than global playlist models.
## Model
### Playlist generation
Playlist generation is the problem of selecting a sequence of tracks in a finite set of tracks.
Random walk models are often used for this task.  
In these models the playlists are sampled using a random walk on a graph where the edges represent the pairwise affinities between tracks.

### User model
The behavior is modeled as follows:
- He first chooses a track uniformly at random.
- At each step: he chooses one of the subsets (categories such as jazz etc where the current track is), and picks the next track uniformly at random in this subset.  

### Playlist model
#### Hypergraph
A hyper graph is given by (X, E, w) where E is set of edges between subsets of X and w represent weights of these edges.

#### Model
The probability of an observed playlist (x0, ... xT) factors into the likelihood of the first observation and the products of probability transitions between the observed songs.  

The likelihood of the first observation is obtained by marginalizing over all the possible edges.

The transition probabilities are obtained by marginalizing over the edges incident to the current song.

The edges weights are assumed to be iid samples of an iid exponential prior distribution

### Estimation
The (non concave) Maximum a posteriori is maximized using the L-BFGS-B algorithm. The convergence is fast (a few seconds, even for large playlist datasets).

##Dataset

A new dataset is built for evaluation : Art-of-the-mix 2011.
It contains approx. 100k playlists with artist names, timestamps and categorical labels.

A collection of edges features are derived from the Million song Dataset and its add-ons

## Experiments
To assess the quality of the predicted playlists the average log-likelihood is computed, and compared to the uniform shuffle model(where all edges have the same weights).
Improvements in playlists likelihood can be observed, but further Improvements could be made using more realistic model than the markov chain and by a non-uniform track selection in a given subset for instance.
