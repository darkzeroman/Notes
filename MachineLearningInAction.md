# Machine Learning in Action

## Part 1

### Chapter 1: Machine Learning Basics

Supervised Learning Tasks: kNN, Naive Bayes, SVMs, Decision Trees, Linear, Locally Weight Linear, Ridge, Lasso

Unsupervised Learning Tasks: kMeans, DBSCAN, EM, Parzen Window

### Chapter 2: kNN

* Pros: high accuracy, insensitive to outliers, no assumptions about data
* Cons: Computationally expensive, lots of memory
* Works with: Numeric, Nominal

### Chapter 3: Decision Trees

* Pros: computationally cheap, knowledge representation is easy to understand, missing values are OK, can deal with irrelevant features
* Cons: Prone to overfitting
* Works with: Numeric, Nominal

Information Gain, entropy, Gini impurity
Info(xi) = equation here
Tree Algorithms: CART, C4.5

### Chapter 4: Naive Bayes
* Pros: works well with small amount of data, handles multiple classes
* Cons: sensitive to how the input data is prepared
* Works with: Nominal 

### Chapter 5: Logistic Regression
* Pros: Computationally inexpensive, easy to implement, knowledge representation is interpretable
* Cons: Prove to underfitting, may have low accuracy
* Works with: Numeric, Nominal

Optimations are used to find regression coefficients: [stochastic] gradient ascent

Options to dealing with missing values in data:

* Use feature's mean value from all the available data
* Fill unknowns with special value like -1
* Ignore the instance
* Use mean value from similar items
* Use another ML algorithm to predict the value

### Chapter 6: Support Vector Machines (SVM)
* Pros: Low generalization error, computationally inexpensive, easy to interpret results
* Cons: Sensitive to tuning parameters and kernel choice; natively only handles binary classification
* Works with: Numeric, Nominal

Concerns with SVMs:
* Need to find the maximum margin by solving a quadratic optimization problem
* Optimization can use SMO, or Platt's SMO
* Kernels: transform data onto another space. Examples: RBF (radial bias function)
* Kernels are sensitive of C

SVMs generate a binary decision (but can be changed to support more). Good generatialization error. 

### Chapter 7: Improving Classification with the AdaBoost

* Pros: Low generalization error, easy to code, works with most classifiers, no param- eters to adjust* Cons: Sensitive to outliers* Works with: Numeric values, nominal values

Ensemble methods
Bagging (or Bootstrapping): new data sets are made with random sampling with replacement, take majority vote

Boosting: similar to bagging, but only use one type of classifier, and trained sequentially.
Boosting makes new classifiers focus on data that was previously misclassified. 

AdaBoosting: adaptive boosting

Decision stump: simple decision tree.


Classication Imbalance:
* Precision: TP / (True Positive + False Positive)
* Recall: TP/(TP + FN)
* ROC Curve

Cost Imbalance:
* AdaBoost: adjust error weight vector D
* Naive Bayes: predict the class with lowest expected cost instead of class with highest probability
* SVMS: use different C parameters in the cost function for different classes

Classification Imbalance (Rare events): can resample for better distribution

## Part 2: Forecasting Numeric Values With Regression

### Chapter 8: Predicting Numeric Values: Regression

* Pros: Easy to interpret results, computationally inexpensive 
* Cons: Poorly models nonlinear data* Works with: Numeric values, nominal values
Locally Weighted Linear Regression
* Linear regression tends to underfit the data because 
* LWLR give weight to data points near [Do more]

Shrink: 
Ridge regression: first of two shrinkage methods

pg 168

### Chapter 9: Tree-based 

## Part 3: Unsupervised Learning

### K-Means Clustering

### Apriori Algorithm

### FP-Growth

## Part 4: Additional Tools

### PCA

### SVD

### Big Data and MapReduce(Hadoop)
* Pros: Processes a massive job in a short period of time.* Cons: Algorithms must be rewritten; requires understanding of systems engineering. * Works with: Numeric values, nominal values.

UNIX alternative of MapReduce

`cat inputFile.txt | python mapper.py | sort | python reducer.py > outputFile.txt`






 


