# Random Forests

Random Forest is a very good way to reduce the variance of decision trees, make them more stable to different inputs. 

- Builds on the bagging algorithm, will learn T trees
- For each tree, obtain a bootstrap sampleof the datapoints and a sample of K features to use for training that tree
- Use the standard CART tree learning algorithm for each tree.
- But at each split step, find the optimal split by searching the features and their values.
- The next tree will use a different sample of features and datapoints.

**Note** that training separate trees using different bootstrap samples and features **decorrelates** the individual trees by also randomly choosing the feature set each can choose from.

Each tree focusses on a subset of the features and learns them better, hence outperforms many other methods in terms of accuracy.

**Comments on Random Forests:**

Pros
- Robust to initial data distribution, sampling process (due to bagging and boosting)
- Easily tunable, more treats improves accuracy and reduces variances
- Relatively fast to train for such a flexible model

Cons:
- Harder to interpret than deicision trees, can try to average rules across trees
- Still needs to be trained on batch data, not streaming (same as decision trees), offline

