# Credit_Risk_Analysis

# Overview

The purpose of this analysis was to train and evaluate machine learning models using different resampling methods, as well as bias-reducing ensemble classifiers to predict credit risk. A problem inherent with classifying credit risk is that our classes (high vs low credit risk) will be very imbalanced. We attempt to account for this using a number of different methods, aiming to find the best model for our particular needs. Our models took into consideration a number of variables, including but not limited to the dollar amount of the loan, interest rates, and annual income, to predict if the loan should be considered high-risk or low-risk. We can analyze the results of these models in order to determine which is the best model for predicting credit risk. 
Overview of Models Used:
- Random OverSampler: Instances of the minority class are randomly selected and added to the training set until the majority and minority classes are balanced. 
 - SMOTE Oversampling: SMOTE (Synthetic Minority Oversampling Technique) interpolates new values by looking at a datapoint from the minority class and a number of its closest "neighbors", based on the values of these neighbors, new values are generated in order to have a balance of classes in the training dataset. 
 - Undersampling with the ClusterCetroids algorithm: Akin to SMOTE, but with undersampling. Identifies clusters of the majority class and generates synthetic data points, the majority class is then undersampled down to the size of the minority class. 
 - SMOTEENN: A combination of SMOTE and ENN (Edited Nearest Neighbor) techniques. The minority class is first oversampled with SMOTE, then cleaned and undersampled using ENN. If the nearest two "neighbors" of a data point belong to different classes, that data point is dropped. 
 - Random Forest: Samples data randomly and makes many small decision trees based on that sampled data. These decision trees are then combined and a prediction made. 
 - Easy Ensemble: Involves creating balanced samples of the training dataset by selecting all examples from minority class, and a subset from the majority class. Boosted decision trees. Using the AdaBoost algorithm, a decision tree is fit on the dataset, errors made by the tree are found, and examples in the dataset are weighed by those errors so more attention is paid to the misclassfied examples than the correctly predicted examples. This process is then repeated for a number of decision trees. 

# Technologies Used
- Technologies utilized in this analysis include: Python, Pandas, NumPy, scikit-learn, imbalanced-learn, Jupyter Notebook

# Results 
- The balanced accuracy score is simply the average of recall scores for each class. 
- As seen below, the models using Ensemble Classifiers to predict credit risk (Balanced Random Forest, Easy Ensemble) proved to have far higher balanced accuracy scores than the models that relied solely on resampling. The model using the Easy Ensemble Classifier had the highest balanced accuracy score of ~93.17%

- Random Oversampling

![ba1](images/ba1.PNG)



- SMOTE Oversampling

![ba2](images/ba2.PNG)




- Undersampling



![ba3](images/ba3.PNG)



- Combination (Over and Under) Sampling with SMOTEENN

![ba4](images/ba4.PNG)



- Balanced Random Forest Classifier

![ba5](images/ba5.PNG)



- Easy Ensemble Classifier

![ba6](images/ba6.PNG)


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

- Looking at the imbalanced classification reports for the six models, again we see that the ensemble classifiers predict credit risk more accurately than those solely relying on resampling. the precision metrics are higher for both models using Ensemble classifiers than the other four, and the F1 scores for the models using Ensemble Classifiers are higher than the rest of the models as well. The model with the highest F1 score is the model using the Easy Ensemble Classifier with an F1 score of .97.


- Random Oversampling

![ci1](images/ci1.PNG)



- SMOTE Oversampling

![ci2](images/ci2.PNG)


- Undersampling

![ci3](images/ci3.PNG)


- Combination (Over and Under) Sampling with SMOTEENN

![ci4](images/ci4.PNG)

- Balanced Random Forest Classifier

![ci5](images/ci5.PNG)

- Easy Ensemble Classifier

![ci6](images/ci6.PNG)



# Summary 
- After viewing the results of our models, we see that the models using Ensemble Classifiers are much better for predicting credit risk. With higher measures for precision, recall, and F1 scores (metric combining precision and recall metrics), we see the value that combining models creates in improving the accuracy and robustness of models. 
- If I were to make a reccomendation for a model based on these results, I would reccomend the Easy Ensemble Classifier. With the highest measures for balaced accuracy, as well as the highest F1 score, it would make sense to use this model to predict credit risk. 
- This reccomendation holds especially true because the problem we are trying to solve is credit risk. We want to capture as many instances of high credit risk as possible (as few false negatives as possible), so sensitivity/recall is likely the most important metric that we'll have, and the Easy Ensemble Classifier had the best sensitivity/recall scores by a fairly large margin.
