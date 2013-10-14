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

SVMs are generally good for problems with lots of data, while DTL is good for small data sets. SVMs need retraining when new data is available.

SVMs are black box like NN.




## k-Nearest Neighbors

Uses instance data to find closest neighbors that are closest to the requested data point. Some distance metrics that can be used are Pearson correlation and Tanimoto score.

### Scaling and Superfluous Variables

Not all dimensions are made the same, which means that certain distances have larger distances than others. Use cross-validation to test how good a certain set of scaling factors is.

### Strengths and Weaknesses

kNN one of the few algorithms that will make numerical predictions in complex functions and still easy to interpret. Scaling the data can only helps, any variable that gets scaled down to 0. kNN is an online technique, but that means all instasnce data must be available.

## Clustering

Hierarchical clustering and K-means clustering are unsupervised learning techniques, so that means no labels are needed.

### Hierarchical Clustering

Hierarchical clustering works by finding the two items that are closest together and merging them into a cluster, repeat until there is only one cluster. The result is a dendogram (tree-like structure that shows which items and groups are closest together).

### K-Means Clustering

K-means clustering separates the data into distinct groups. Getting the right k is difficult.

## Multidimensional Scaling

Multidimensional scaling attempts to understand how different items are related. Basically a 2D representation of multidimensional data set.


## Non-Negative Matrix Factorization

NMF breaks down a set of numerical observations into their component parts. 

The goal of NMF is to find the features and weight matrix. Starts with random matrices for each and updates them according to update rules. Four matrices are generated:

* hn: transposed weights matrix multiplied by the data matrix
* hd: transposed weights matrix multiplied by the weights matrix multiplied by the features matrix
* wn: data matrix multiplied by the transposed features matrix
* wd: weights matrix multiplied by the features matrix multiplied by the transposed features matrix

Some examples of NMF applications are finding news themes and how trading volume of various stocks could be broken down into events that affected individual stocks or multiple stocks at once.

## Optimization

Instead of working straight with a dataset, optimization is concerned with minimizing the output of a cost-function.

### The Cost Function

A cost function is some sort of function which can be evaluated to get a value. The value is high for worse solutions and low for better solutions. Need to worry about local and global minima.

### Simulated Annealing

```
Simulated annealing, which was inspired by alloy cooling in physics, starts with a random guess at a solution. It tries to improve the solution by determining the cost for a similar solution that’s a small distance away and in a random direction from the solution in question. If the cost is lower, this becomes the new solution. If the cost is higher, it becomes the new solution with a certain probability, depending on the cur- rent temperature. The temperature starts high and decreases slowly so that early on the algorithm is much more likely to accept worse solutions in order to avoid getting stuck in a local minimum.When the temperature has reached 0, the algorithm returns the current solution.
```

### Genetic Algorithms

```
Genetic algorithms were inspired by evolutionary theory. A genetic algorithm starts with several random solutions called the population. The strongest members of the population—those with the lowest cost—are chosen and modified either through slight changes (mutation) or through trait combination (crossover or breeding). This creates a new population, known as the next generation, and over successive generations the solutions improve.The process stops when a certain threshold has been reached, when the population has not improved over several generations, or when a maximum number of genera- tions has been reached. The algorithm returns the best solution that has been found in any generation.
```