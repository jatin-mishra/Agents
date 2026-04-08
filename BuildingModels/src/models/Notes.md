# Classification vs regression
- classification: given set of classes in output
- regression: output is more like real number in d dimensional space

# Classification Scenarios

- Imbalanced vs balanced dataset
    - clss_1: 50, clss_2: 950
        - Undersampling
            - randomly sample clss_2 = 50 
            - new Dataset (clss_1, clss_2 -> 50,50)
        - Over sampling
            - replicate smaller one multiple times
        - Extra polation
            - create synthetic points 
        - use class weight


## Note
- you can get high accuracy even from dumb models (in case of imbalanced data)


# Local Outlier Factor (LOF)
- assume two classes with different density

## Reachability distance (xi, xj)
= max( k_distance(xj), distance(xi, xj) )
-> {
    if xi belongs of neighbor(xj)
        reach-dist(xi, xj) = k-dist(xj)
    else 
        reach-dist(xi, xj) = dist(xi, xj)
}

## Local Reachability density (LRD)
                1
    ---------------------------
    sum{xj belongs to N(xi)} { reach-dist(xi, xj) / | N(xi)| }

= inverse of avg reach dist of xi from its neighbors

## Local Outlier Factor (LOF) (xi)
= (sum {xj belongs to xi} lrd(xj) / | N(xi) | ) * (1 / lrd(xi))

if factor is large then it is an outlier.


# Model Interpretability vs Black box
- KNN can give that info saying because N neighbors belong to class_1 hence classified as 1.


## Feature importance and forward selection
- try for every feature and get the accuracy
- then pick one and start picking second one using same process in combination with first picked.
- and keep doing it until the last.


## Categorical and Ordinal features
- one hot encoding, rather than assigning 1,2,3,4 to enums, use boolean getter type features
- or replace with some agg value of y's.


## Missing value imputation
- mean replacement
- median replacement
- most-freq replacement (mode)
- as well as add new features called is_f1_missing, is_f2_missing, ... etc.
- model based imputation  (example: KNN)


# Curse of dimensionality
- as dimensions increase, the number of data points needed also increases. (We need data points spread everywhere)
- as dimensionality increases, for fixed size of given data, performance decreases.
- intuition of dist in 3D is not valid in high dim spaces.
- dim incre, d -> inf, limit prooves that point between any two points is somewhat same.
- that's why KNN is not good for high dimensional space. (cosine distance is better than euclidean distance)
- dim increases, overfitting increases in linear regression models


# Bias Variance Trade off
generalization error = bias ** 2 + variance + irreducible error
- underfitting -> high bias (loose constraints)
- variance -> model changes as training data changes (overfit model)
- train error increases, bias increases
- train error decreases, bias decreases