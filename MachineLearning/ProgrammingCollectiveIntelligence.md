Programming Collective Intelligence

# Algorithm Summary

## Bayesian Classifier

Examples: Document classification system, spam filtering, dividing up a set of documents onan ambiguous keyword search.

Works on a dataset that can be turned into list of features (indicator of absence or presence for a given item). In the previous example, features are words in the document, but can also be characteristics of an unidentified object, symptoms of a disease, or anything that can be said to a present or absent.

### Training

Like all supervised methods, Bayesian classifier is trained with examples (which hold an item's features and the classification for that item). 

The classifier keeps track of all the features it has seen so far, along with numerical probabilities that the features are associated with a particular classification.

Add More

Trained classifier is nothing more than a list of features along with their associated probabilities. So no need to store original data like instance based methods.

### Classifying

` Pr(Cat | Doc) = Pr(Doc | Cat) * Pr(Cat)`
` Pr(Doc | Cat) = Pr(Word1 | Cat) * Pr(Word2 | Cat) * … `

Add More

### Strengths and Weaknesses

Bayesian classifiers can be trained and queried with large datasets since most of the time large data sets have a few number of features of each item.

Training can be incremental, each new piece of training ata can be used to update the probabilitiles without going back over the old data (like DTL and SVM). Good for applications such as spam filter which doesn't need to have deleted email for training.

The model is relatively simple to understand.

Sometimes combinationes of features are necessary to make better decisions.

## Decision Tree Classifier

Makes a decision.

### Training

At each level, a feature is chosen which gives the most information gain.

#### Strengths and Weaknesses

Easy to interpret a trained model and see the most important features.

DTL works with categorical, numerical, and numerical data inputs.

DTL is not as good as making predictions for numerical results. Good for when there are mean values and low variance, otherwise tree can get large.

Main advantage for DTL over Bayesian classifier  is that it can easily cope with interaction of variables. Spam filter sing a DTL would determine that "online" and "pharmacy" are fine in isolation but indicate spam when the words occur together.

Incremental updates are hard with DTL and there are issues with.

## Neural Networks

Example of NN was of ranking of search results based on user clicks history. The NN was able to learn which words in which combinations were important and not. Useful for classificatin and numerical prediction problems.

One type of NN is multilayer perceptron network. Each layer is connected by synapses with associated weights.

### Training 

Train with backpropagation is one method.

### Strengths and Weaknesses

Main strength is that they can handle complex nonlinear functions and discover dependencies between different inputs. Allow for incremental training and doesn't require lots of space to store models. 

Major downside is NN is like a black box. Hard to choose training rate and network size, usually needs experimentation. A high training rate might overgeneralize on noisy data, and too low might never learn.


## Support-Vector Machines

SVMs take datasets with numerical inputs and try to predict which category they fall into. Example might include deciding which positions for a basketball team from a list of people's heights and running speeds.

SVM finds the line that separates the data most cleanly, and the ones that do are known as support vectors. Classification is just plotting the data point with respect to the support vectors.


### Kernel  Trick

SVMs (like other linear classifiers) use vector dot-products. This is where polynomial transformations can be applied to different axes.

### Strengths and Weaknesses

SVMS are powerful once the parameters are correct and easy to classify new data points. SVMs can use categorial (by making them numerical) and numerical data.

SVMs are generally good for problems with lots of data, while DTL is good for small data sets.

SVMs are black box like NN.


## k-Nearest Neighbors
### Scaling and Superfluous Variables
### Strengths and Weaknesses

## Clustering
### Hierarchical Clustering
### K-Means Clustering

## Multidimensional Scaling
## Non-Negative Matrix Factorization

## Optimization
### The Cost Function
### Simulated Annealing
### Genetic Algorithms










