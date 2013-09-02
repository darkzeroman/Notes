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

Gradient Ascent Pseudo Code:

```
Start with the weights all set to 1 
For each piece of data in the dataset:	Calculate the gradient of one piece of data 	Update the weights vector by alpha*gradient 	Return the weights vector
```

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

SMO Pseudo Code:

```
Create an alphas vector filled with 0sWhile the number of iterations is less than MaxIterations:	For every data vector in the dataset: 
		If the data vector can be optimized:			Select another data vector at random 			Optimize the two vectors together			If the vectors can’t be optimized ➞ break	If no vectors were optimized ➞ increment the iteration count
```

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

CART: Classification And Regression Trees. Pruning. Model Trees.

ID3: splits all possible values of feature and can't be used again (can do a binary split), can't handle continuous features

CART: makes binary splits and handles continuous variables. Can do regression with modification.

* Pros: Fits complex, nonlinear data* Cons: Difficult to interpret results* Works with: Numeric values, nominal value
Pseudo Code for Create Tree```
Find the best feature to split on:	If we can’t split the data, this node becomes a leaf node Make a binary split of the data	Call createTree() on the right split of the data	Call createTree() on the left split of the data
```

## Part 3: Unsupervised Learning

### K-Means Clustering (Unsupervised Classification)

* Pros: Easy to implement* Cons: Can converge at local minima; slow on very large datasets 
* Works with: Numeric values

Pseudo-code:

```
Create k points for starting centroids (often randomly) 
	While any point has changed cluster assignment		for every point in our dataset: for every centroid			calculate the distance between the centroid and point assign the point to the cluster with the lowest distance		for every cluster calculate the mean of the points in that cluster		assign the centroid to the mean
```
The measure of closeness can be changed, use any distance measure as required.

One metric for quality can be: SSE (sum of squared error).

Bisecting K-Means: splits clusters that have high SSE

```
Start with all the points in one cluster 
While the number of clusters is less than k	for every cluster		measure total error		perform k-means clustering with k=2 on the given cluster 		measure total error after k-means has split the cluster in twochoose the cluster split that gives the lowest error and commit this split
```

### Apriori Algorithm

* Pros: Easy to code up* Cons: May be slow on large datasets* Works with: Numeric values, nominal values

Association analysis (association rule learning): looking for hidden relationships in large datasets.
* Frequent item sets: collections of items that frequently occur together
* Association rules: suggest that a strong relationship exists between two items

	
* Support: percentage of the dataset that contains the itemset
* Confidence: association rules, support(two_items)/support(one_item)

Apriori Principle: if an itemset is frequent, then all of its subsets are frequent (or inverse)

Generating Candidate Itemsets:

```
For each transaction in tran the dataset:
For each candidate itemset, can:
	Check to see if can is a subset of tran
	If so increment the count of can
For each candidate itemset:
If the support meets the minimum, keep this item
Return list of frequent itemsets
	
```

```
While the number of items in the set is greater than 0: 
	Create a list of candidate itemsets of length k	Scan the dataset to see if each itemset is frequent	Keep frequent itemsets to create itemsets of length k+1```


### FP-Growth (frequent pattern)

* Pros: Usually faster than Apriori.* Cons: Difficult to implement; certain datasets degrade the performance.* Works with: Nominal values.

Two steps:
* Build FP-tree
* Mine frequent itemsets from the FP-tree




## Part 4: Additional Tools

### PCA

PCA assumes the data to be statically dependent, finds the axises with the most variation.

Factor analysis: we assume some unobservable latent variables are generating the data. Assume data to be a linear combination of the latent variables and some noise. The number of latent variables is possisbly lower than the amount of observed data, so it is dimensionality reduction. Used in social sciences, finance, other areas.

Independent Component Analysis: Assumes data is generated by N sources, a mixture of sources, assumed to be statically independent, so data is uncorrelated.


* Pros: Reduces complexity of data, indentifies most important features 
* Cons: May not be needed, could throw away useful information* Works with: Numerical values

```
Remove the meanCompute the covariance matrixFind the eigenvalues and eigenvectors of the covariance matrixSort the eigenvalues from largest to smallestTake the top N eigenvectorsTransform the data into the new space created by the top N eigenvectors```

### SVD

* Pros: Simplifies data, removes noise, may improve algorithm results. 
* Cons: Transformed data may be difficult to understand.* Works with: Numeric values.
SVD is used in search, IR using latent semantic indexing, recommendation systems.
Latent Semantic Indexing/Analysis (LSI or LSA): constructs a matrix of documents and words which is used to create a set of singular values. Singular values represent concepts or topics contained in the documents. Does not to work with misspellings and synonyms.
Matrix factorization: takes a larger complicated matrix into a few smaller matrices. Assuming most of the matrix is noise.SVD Process: Data = U E V^T
E: only diagonal elements are singular values, correspond to singular values of Data.
Collaborative Filtering-Based Recommendation Engines
Distance Measurements:
* Euclidean* Pearson Correlation (shows how similar two vectors are, ranges from -1 to 1)* Cosine Similarity
Item-based or user-based similarity depends on the situation.
Evaluating recommendation engines: RMSE (root mean squared error)
Challenges: search problem (content-based recommendation) is good for cold-start.


### Big Data and MapReduce(Hadoop)
* Pros: Processes a massive job in a short period of time.* Cons: Algorithms must be rewritten; requires understanding of systems engineering. * Works with: Numeric values, nominal values.

UNIX alternative of MapReduce

`cat inputFile.txt | python mapper.py | sort | python reducer.py > outputFile.txt`


## Appendix

### Appendix B: Linear Algebra

Dot product: how much one vector moves in the direction of another vector. Or find the cosine between two vectors.

Matrix Inverse: XY = I, not all invertible. Has to be square. If not invertible: singular/degenerate. 

Singular: if one column can be represened as a linear combination of other columns.
Norms: ||A||, assigns a positive scalar value to any vector.
* L1 Norm: Manhattan Distance

Can take derivative of matrix wrt to another