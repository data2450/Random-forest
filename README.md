# Random-forest
Random forest is an **Ensemble** of tress(descision tree), not just one tree. Random Forest is one of the most popular and most powerful machine learning algorithms

because

 **It is a type of ensemble machine learning algorithm**, ( Bootstrap Aggregation or bagging and boosting)=ensampling methods 
 
 AN ensemble takes individual learning models & combines them to produce an aggreagative model that is more powerful than any of its individual model
 
 ##$)As tha name suggest random forest as the forest consist of many trees random forest algorithm also bulid by combination of multiple decision trees
 
 
 # ensemble learning
 We all do that. Before we make any big decisions, we ask people’s opinions, like our friends, our family members, even our dogs/cats, to prevent us from being biased  or irrational.
The model does that too. it is very common that the individual model suffers from bias or variances and that’s why we need the ensemble learning.
**Ensemble learning, in general, is a model that makes predictions based on a number of different models**. By combining individual models, the ensemble model tends to be more flexible (less bias) and less data-sensitive  (less variance).

Two most popular ensemble methods are bagging and boosting.

**Bagging**: Training a bunch of individual models in a parallel way. Each model is trained by a random subset of the data

**Boosting**: Training a bunch of individual models in a sequential way. Each individual model learns from mistakes made by the previous model.

##$)one decision tree :prone to overfitting

Many descision tree :More stable better generalisation

The random variation during tree bulding happens in two ways 

1.The data used to bulid each tree selected randomly

2.feature chosen in each split test are also randomly selected

# create random forest model
first we decide on how many trees to bulid .This is set using the "n_estimated" parameter both(random forest classification,random forest regression)

**each tree would bulid from different sample of the data called bootstrap sample**

Bootstrap sampling:if ure training set has N instances or N n.o of 


