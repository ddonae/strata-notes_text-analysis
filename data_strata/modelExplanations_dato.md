# Explaining Models: Why Should I Trust You?
@ Dato

Challenges of model explanations
- interpretable models don't always have the best accuracy
- using accuracy is unreliable, can come from misleading features
- A/B testing: expensive to conduct

making models interpretable
- Example: "easily best sushi in seattle" predicts sentiment as positive
    - why? "easily best"
- Example: neural net predicting wolf vs huskey
    - predicts 1 out of 6 wrong, would you trust it?
    - model is using presence of snow to predict wolf

What goes into a good mdoel explanation
- **interpretable**: user understands the reasoning
- ** faithful**: describes how the model actually behaves
- ** model agnostic**: can be used for any machine learning model

In practice --> the LIME (Locally interpretable model explanation) methodology
- look at a sample of predictions to understand predicted features
- example: random forst of 20 newsgroups data set
    - looking at words associated with christian predictions: host, posting, edu
    - clearly these are senseless features, sparse predictions
- example: predicitng if Game of Thrones characters are dead or alive
    - looking at the wrong predictions to udnerstand why the model predicted alive or dead
    - features: winerfell, family name, old/alive, isPopular, isNightsWatch

Evaluating explanations
- train data with senseless features removed to get gold standard
- using mechanical turkers clean data over rounds

How to explain the whole model, not just individual predictions?
- pick k data points that cover diverse outcomes and feature explanations from model
- example: picking between two models, both perform well on training set, only one performs well on test set
    - using LIME helps more often to correctly identify better model (89% vs high 60% of original model)

Explanations with Deep Learning
- Google Inception
- using neural net for predicting guitar type
    - electric guitar looks at arm of guitar
    - acoustic looks at body of guitar
    - dog looks at face

**Explanations lead to better decisions**
- explore predictions to explain why the model is making decisions
- * which features lead to a given predicted outcome?*

Building Trust in models: evaluation + exploration + explanation