# Building a continuous learning system
@author: Anuj Gupta

## Example: spam filter for twitter
- interacting with brands: promotional vs consumer
- twitter is a very noisy medium
- 65% noise in this use case
- model 2.0: handles drift, vocab changes, learns from mistakes

### Process
- binary classification
- feature engineering: handles, hashtags, urls, emoticons, words, chars
- compare algorithms
- train, test, tune
- deploy
... but what happens in production?

## How to recognize need for reevaluation
- non-stationary distributions - standard deviation varies over time
- drift - distribution generating data changes over time
- vocabulary of text data was changing over time, new words 10% of each month
- this can happen in twitter, monitoring and anomaly detection, adversarial setting, recommendations (user preferences change over time), evolving labels, stock market predictions

## So how to improve?
- model must use signals to change over time, learn from its mistakes
- option 1: frequently retrain model with new data
    - new data may not be reflective of old data, lose the old learnings
- option 2: continuous learning, adaptive models change as the data changes
    - global model: DNN, large corpus, common for all users, batch trained
    - various local models: tailored to user groups, fast learner, instant feedback

## How to develop adaptive models
- preprocess: remove stop words, replace mentions, hashtags, urls, emojis, dates, numbers, currency with relevant constants
    ZIPF's law / fit test for preprocessing validation
- text representation: word2vec to replace words with its embedding, average embedding vectors for constituent words, generate random dimensions for missing words
- global model: DNN, 886% accuracy
- local model: online learner, doesn't forget recent data, incorporates last feedback successfully (as model updates, the same data points will correctly predict class label)
    - online learning: no resources to save data, it comes on the fly one point at a time, no luxury to see the entire dataset at once

## Building a feedback loop
- model is trained, agent tells model if its prediction was right or wrong, label is fed back into model
- approaches:
    - reinforcement learning: not great when the classification levels are small (2 states / binary)
    - mini-batches: works fine if feedback is quick / high velocity
    - instant feedback / tiny-batches: very susceptible to skew based on only 1 data point
- process
    - model feedback point as a datapoint presented to local model
    - feedbacks are incoming data stream
    - online learner in ML: data modeled as a stream, model makes prediction, environment reveals correct label, if they are wrong then the model is updated

## online learners in scikitlearn
stochastic gradient descent, crammers PA-II
using hinge loss to penalize the model when it is wrong, model weights are updated when it is wrong

