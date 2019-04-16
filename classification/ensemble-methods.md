# Ensemble Methods

Rather than training just one model on to predict the data with low error, try learning multiple models, on subsets of the data, and combine them to get overall lower error than possible form a single model.

This acts as a regularizer because it forces the model to learn a more general solution.

### General Essemble Methods

A **bootstrap** data set is create by randomly selecting n points from the training set X of size n with replacement.
There will usually be some duplicates. This is repeated B times with independent draws each time.


##### Bagging (bootstrap aggregation)

Draw multiple subsamples of the data of size, learn a component classifier on using each bagged sample, final classification decision based on vote from each component classifier

Usually use same classifier for each component, but they could be different

The **advantage** is reduces instability (i.e. sensitivity of classifier performance to small changes in data)


##### Boosting

A meta-algorithm that allows us to create an ensemble of classifier with arbitrarily high accuracy

Train mutiple classifiers as in **bagging** but each bootstrap sample is chosen to **maximize the information gain conditioned on the previously trained classifiers**.

This classifier could be a **weak learner**: only guaranteed to be better than chance.


##### Adaboost

We assume the sign of the weak learner gives the class, and the magnitude of the value gives the confidence in the classificaiton. It essentially classifies the datapoints using a weighted majority vot of different classifiers, each trained to perform well where all previous classifiers are doing badly.

