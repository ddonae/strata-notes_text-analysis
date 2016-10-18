# Class Imbalances and Adversaries
@author: Brendan Herger, Capital One (Vault 8)

Class imbalance: minority group trying to subvert the system
- Example: spam

## Sampling
Observation weighting: effect cost function
- types: uniform, observation age / staleness, random down-sampling
SMOTE sampling: reduces effect of class imbalance
- downsample majority
- create synthetic points for minority case
    - randomly pick in subset, select neighbor, create copy

## Feature Engineering
outlier detection: create outlier score
- train learner via PCA or neural network
- large distance between input and output
- neural network: bottleneck hidden layer, take only the most interesting inputs and extrapolate back otu to outputs
label propagation: identify networks of bad actors
- using graph for actors and associations, label bad/good actor nodes
low rank models (GLRM): reduce dimensionality through generalized PCA
- works well with categoricals
- model on components as latent factors
LDA topic modeling: reduce dimensionality for variables with many levels
- stolen from NLP
- identify next text with maximum separation

## Modeling
grid search: optimal hyper-parameters
- create permutations of every possible input
neural networks
ensemble modeling: leverage diverse set of algorithms
- train different algs on train data
- produce a score, using logistic regression to see which algs is adding the most weight, feed into meta learner to aggregate
genetic algs and artificial immune systems
- score based onsimilarity and characteristics authorizations

[slides](https://github.com/bjherger/talks/blob/master/strata-ny-2016/Strata-2016-NY.pdf)