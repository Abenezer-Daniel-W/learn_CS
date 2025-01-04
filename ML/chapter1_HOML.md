# Chapter 1 Machine learning landscape

> [!note] Definition of Machine learning
> A computer program is said to learn from experience E with respect to some task T and some performance measure P, if it's performance on T as measured by P improves with experience E

problems machine learning excel at are:

- where a solution require fine tuning or a list of rules
- complex problems such as voice recognition
- fluctuating environments
- getting insight on complex problems form large amounts of data

One simple classification between ML systems are the following:

- supervised vs unsupervised
- online versus batch learning
- instance based vs model based learning

## Training supervision

### supervised learning

Supervised learning is learning where the data feed into the model has labels and the model uses those labels to learn to predict labeled data. A good example is a spam filter that learns what spam is by the emails labeled spam from the user.

### unsupervised learning

The data give to the model is not labeled and the model is often tasked with classifying that data. Good examples of this are classification models used for anomaly detection or dimension reduction.

### semi-supervised learning

I learning on data that is partially unlabeled data, they are often a combination of supervised and unsupervised learning method.

### self-supervised learning

I when a model produces labeled data from a set of fully unlabeled data, example of this can be a model that labels animal species. (don't fully understand this)

### Reinforcement learning

Reinforcement learning has an agent in an environment that can perform action and these actions result in a reward and the goal of the agent is to find a policy that results in the most amount of reward.

### online and batch learning

**Batch** learning is when the model is train at one using the data you currently have. This method has it's issues called model root, which is the the slow decay of your models performance due to the world changing. To combat this you can retrain your model within a certain time period.
**Online** learning is when the model adapts to recently provided data, similar to batch learning this also has its issues. The main issue with batch learning is that it might become biased to recently added data.

## Instance based vs Model based learning

**Instance-based** learning, also known as memory-based learning, is a type of machine learning that classifies new data by comparing it to previously stored instances from training data. It does not create a generalized model but instead relies on the specific examples it has learned from, making it adaptable to new data.

**Model-based** learning is when you pic to represent the data is some kind of model, one such example is using linear model to represent the relationship between GDP per capita and Happiness.

The workflow often follows this pattern:

- you studied the data
- you selected a model
- You trained it on the training data (i.e., the learning algorithm searched for the model parameter values that minimize a cost function).
- Finally, you applied the model to make predictions on new cases (this is called *inference*), hoping that this model will generalize well.

## Main challenges of ML

### Insufficient Quantity or training data

Various research papers have showed that often time data is more valuable than the learning algorithm. This means more high quality data with less complex algorithm might outperform a more complex algorithm working with small amounts of data.

### Poor-Quality data

Often time the data you have at your disposal will have missing filed, errors, outliers and a whole host of other issues that if not taken care of will hinder the performance of your model.

### Irrelevant features

- *Feature selection* (selecting the most useful features to train on among existing features)
- *Feature extraction* (combining existing features to produce a more useful one⁠—as we saw earlier, dimensionality reduction algorithms can help)
- Creating new features by gathering new data

### Overfitting the training Data

- Overfitting is when a ML model preforms well on the training data but does not generalize well, one example is using 4th degree polynomial to fit a linear relationship.
- Constraining a model to make it simpler and reduce the risk of overfitting is called regularization.
- The amount of regularization to apply to a model is a hyperparameter, a hyperparameter is a parameter the is not part of the learning process and is not affect by it.

### Underfitting the Training Data

underfitting is when your model is to simplistic to learn the underlying structure in the data. Example of this is using a linear model to model happiness among citizen, the linear model is to simple to represent such complex reality.
ways you can solve this are

- use a more complex model
- have better feature selection
- reduce the constraints of the model by changing regularization

## Testing and Validating

### training and testing

Evaluating whether a model is performing well prior to launching it to users is important and one way to check you models performance before deploying it is to split the data into two. Testing and validation, you train on the training set then measure your performance on the testing set and if you are satisfied you release this model.
One issues with this approach is that once you have launched the model it might not perform well in the real world. This happens because you are testing and training on a small set of data that may not completely represent the entire reality to get around this we use hyper parameter tuning and model selection.

### Hyperparameter Tunning and Model Selection

![[Pasted image 20250101134254.png]]

The way to get around this is to

1. train multiple models with differing hyperparameters on the training set
2. evaluate each model on the dev set then pick the best
3. Retrain the best model with it associated hyperparameters on the entire training set(training set + Dev set)
4. Finally test the model on the test set to get generalization errors

Some issues with this is that splitting the entire training set into dev set and training set there are tradeoffs where if dev set is really small it will be hard to evaluate the models performance and on the other had if dev set is large it and training set is small the evaluation will also be wrong in that case.

## Data Mismatch

When training a model it might be the case that the data used to train it is not representative of the data it will see when user use the model. One such example is a flower species identifying model that was trained on pictures of flowers from the web and used to recognize flowers species from phone pictures. The process of fixing this involves determining whether the issue with the model is from overfitting or data mismatch. The solution to this is to split the training set into two and check whether and train on the train-set and test is against the train dev and if it performs well then the issue is not over fitting.
![[Pasted image 20250101135544.png]]

1. train on **Train**
2. test against **Train-dev**
   1. if preforms well it is not overfitting
   2. else it is over fitting, either change model or change hyperparameters
3. test against **Dev**
4. train on **Train + Dev+ Train-dev**
5. test against **Test** to get generalization error

## Exercises

1. How would you define machine learning?
   Machine Learning is about building systems that can learn from data. Learning means getting better at some task, given some performance measure
2. Can you name four types of applications where it shines?
   1. image recognition
   2. prediction of values
   3. speech recognition
   4. closed loop games, i.e. chess
3. What is a labeled training set?
   A labeled training set is a training set that contains the desired solution (a.k.a. a label) for each instance.
4. What are the two most common supervised tasks?
   regressing and classification.
5. Can you name four common unsupervised tasks?
   Common supervised tasks include clustering, visualization, dimensionality reduction, and association rule learning.
6. What type of algorithm would you use to allow a robot to walk in various unknown terrains?
   reinforcement learning
7. What type of algorithm would you use to segment your customers into multiple groups?
   clustering
8. Would you frame the problem of spam detection as a supervised learning problem or an unsupervised learning problem?
   supervised
9. What is an online learning system?
   is a learning system that learns with each new peace of data
10. What is out-of-core learning?
    when you train on data that does not fit into the memory of a computer and use mini batches of data with online learning to learn
11. What type of algorithm relies on a similarity measure to make predictions?
    instance based learning
12. What is the difference between a model parameter and a model hyperparameter?
    a model hyperparameter is a parameter that is set prior to the learning process and does not change as a result of the learning process
13. What do model-based algorithms search for? What is the most common strategy they use to succeed? How do they make predictions?
    They search for patterns in the data, the strategy to succeed is to reduce there error in training.
14. Can you name four of the main challenges in machine learning?
    1. overfitting
    2. underfitting
    3. data mismatch
    4. Poor quality data
15. If your model performs great on the training data but generalizes poorly to new instances, what is happening? Can you name three possible solutions?
    you model is overfitting
    1. retrain with simpler model
    2. regularize the model
    3. reduce number of features
16. What is a test set, and why would you want to use it?
    A test set is a sub set of the entire data available used for checking a models ability to generalize
17. What is the purpose of a validation set?
    A validation set is used to check which model performs best
18. What is the train-dev set, when do you need it, and how do you use it?
    you use train-dev set for checking whether or not you are overfitting in the case where you want to know if you have a data mismatch issue
19. What can go wrong if you tune hyperparameters using the test set?
    overfitting on the test set
