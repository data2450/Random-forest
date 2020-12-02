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

# create random forest model(bagging)
first we decide on how many trees to bulid .This is set using the "n_estimated" parameter both(random forest classification,random forest regression)

**each tree would bulid from different sample of the data called bootstrap sample**

Bootstrap sampling:if ure training set has N instances or samples in total ,a bootstrap sample of size N is created by just repetadely picking on of the N dataset rows at random with replacment , that allowing for the possiblity of picking the same row again at each selection

u repeat this random selection process N times.This resulting bootstrap sample has N rows just like the original training set but with possibly some rows from the original dataset missing and other occuring multiple times just due to nature of the random selection with replacment.

bulding a decision tree for a random forest ,the process is almost the same as for the standard decision tree but with one important difference

when picking the best split for a node instead of finding the best split across all possible features , a random subset of features is chosen and the best split is found within the smaller subset of features

The n.o of features in the subset that are randomly  considered at each stage is controlled by the **max_feature** parameter 

this randomess in selecting the bootstrap sample to train in a forest ensemble ,combined with the fact that splitting a node in the tree is restricted to random subsets of the features of the split,virtually guarantess that all of the decision trees and the random forest will be different 

forest model is sensitive to max_features if it is one ,the model is limited to performing a split on the single feature that was selected randomly ,instead of being able to take the best split over several variables

trees in forest will be very different from each other and possibly will with many levels in order to produce agood fit to the data

if max_feature is close to total n.o of features that each instance has ,trees in the forest will tend to be similar and probably will require fewer lvelsto fit the data using the most informative features 

# prediction
once the random forest is trained ,it predicts the target value for new instance by the first making a prediction for every random forest .for regression tasks the overall prediction is then typically the mean of the individual tree predictions 

for **classification** the overall prediction is based on the weighted vote .Each tree give gives a probablity for each target classes label then probablities for each class are averaged across all the trees and the class with the highest probablity is the final predicted class.

# key parameters
**n_estimators**:n.o of trees to use in ensample(default:1),-should be larger for larger dataset to reduce overfitting(but use more computation)

**max_features**:has a strong effect on performance.Influence the diversity of trees in the forest. -default works well in practice ,but adjusting may lead to some further gains

**max_depth**:controls the depth of each tree (default:none split until all leaves are pure)

**n_jobs**:How many cores to use in parllel clustring training

choose a fixed settings for random_state parameter if u need reprodusable result

 # others
**bias**:our model will learn by training dataset ,when we introduce with testing or validation data to the model there may create a difference in predicted values and true values

**"bias is the difference between the predicted value and the expected value".**

when there is a high bias error ,it results in a model that is not capable of taking so much variation.since it does not learn enough from training data,it is called **underfitting**

**variance**:is the error that occurs when the model captures flutuations or noise of the data,the model sholud be able to learn the general trend .not the local changes
the model learns too much from the training data,so when it is introducede with new testing data,it is unable to predict the results accuretly


high variance our model is overfitting

# ensemble methods
Ensemble method create multiple models (called base learners/weaklearners)  and combine/aggregates them into a final predictive model to decreases erros (variance and bias) 

**parallel ensemble method**:in this method base learners are generated parallely,hence encourge independence between the base learners.Due to the application of averages.the oveall error is reduced

**sequential ensemble methods**:in this method base learners are generated sequence try,hence base leaners are dependent on each other.overall performance of the model ids the increased by allocating higher weights to previously mislabeled/mispredicted learners.

# bagging
bagging standes for Bootstrap Aggregating or simply Bootstrapping + Aggregating.

**bootstrapping**:in bagging refers to a technique where multiple subsets are divided from the whole(set) using replacment procedure 

**aggregating**:combines all possible outcomes of the prediction and randomizes the outcome

hence many weak models are combined to form a better model

bagging is a parallel ensemble method,where every weak models is constructed inpependently .

baggibg is used when the aim is to reduce variance

# how is bagging performed
The whole process of bagging is explained in just a few steps.please refer the digram

1)'n' n.o of multiple data subset(d1,d2,d3...dn) are generated randomly with replacement from the original dataset 'D'
**bootstrapping**

2)now these multiple sub-datasets are used to train multiple models (which are called 'weak learners' like m1,m2,m3...mn

3)Final prediction (ensemble method) is givien based on the aggregation of predictions from all weak models, **Aggregating**

* **in case of regressor**:the average /mean of these is considered as the final prediction

* **classifier**:majority vote gained from voting mechanism is considered as the final prediction

as "random sampling with rwplacement" is used here therefore every element has the same probablity to appear in a newtraining sub-dataset and also some observations may be repeated.Ensemble model produced with weak models is much robust and with low variance

eg:random forest algorithm uses the concept of bagging

# boosting
bossting is a sequential ensemble method,where each consecutive model atempt to correct the errors of the previous.

if a base classifier is misclassified in one weak model,it's weight will get increased and the next base learner will classify it more correctly.

since the output of one base learners will be input to another ,hence every model is dependent on it's previous model

boosting is used when the aim is to reduce bias

# how is boosting performed
the whole of boosting is explained in just a few steps.please refer to the diagram 

1)let d1 be the subset ,which is generated randomly with replacment from the original dataset 'D'

2)now the subset is then used to train the model m1(which is called weak learner)

3)this model is then used to make predictions on the original (complete) dataset .elements or instances which are misclassified /mispredicted by this model ,will be given more weights while choosing the next data-subset 

4)let d2 is the datasubset,which is generated randomly with replacement from the dataset 'D'(which is now updated with weights)  In this step instances which have more weights (concluded from the previous step) will be more likely to be chosen

5)now this subset is agian used to train the model 'm2'(which is called a weak learner)

6)above steps are repeated for 'n' n.o of times to get n such model (m1,m2,m3....mn)

7)results of these 'n' weak models are combined to make a final prediction.


# Implementation
* AdaBoost

* Gradient boosting

thses algorithms uses boosting in a different manner

# similarities between bagging and boosting
1.both them are ensemble methods to get N learners to from one learner

2.both of them generate several sub-datasets for training by random sampling

3.both of them make the final decision by averaging N learners (or by majority voting)

4.both of them are good st providing higher stability.

# bagging vs boosting

1.the main goal of bagging is to decrease variance ,not bias.The main goal of boosting is to decrease bias,not variance

2.IN bagging multiple training data-subsets are drawn randomly with replacment from the original dataset.In boosting the new subdataset are drawn randomly with replacment from the weighted (updated) dataset

3.in bagging every model is constructed independently .in boosting ,new models are dependent on the performance of previous model

4.in bagging every model recevies an equal weight .In boosting ,models are weighted by thier performance

5.in bagging ,final prediction is just the normal average .in boosting the final prediction is weighted average.

6.bagging is usually applied where the classifier is unstable and has a high variance.boosting is usually applied where the classifier is stable and has high bias.

7.bagging is used for connecting predictions of the same type.boosting is used for connecting predictions that are of different types

8.bagging is an ensemble method of type parllel.boosting is an ensemble method of type sequential

# conclusion
the algorithm selection depends on the circumstances of the givenproblem .u need to analysze the errors first and then look foreard to choosing a better option for ure specific problem.

if ure problem is **underfitting the boosting** can give better results .in contrast ,if ure prb is **overfitting then bagging** wolud be better choice
