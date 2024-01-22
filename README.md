# Practical-Application-3
This project is about improving the success of marketing campaigns to get clients to open new bank accounts. 
A major bank in Portugal wants to improve how it targets existing clients and understand what key factors drive its clients to open new bank accounts.  

As part of the assignment, the performance of the classifiers K-Nearest Neighbors, Logistic Regression, Decision Trees, and Support Vector Machines is evaluated on a dataset containing 41,188 client samples and 20 different features including client age, type of employment, marital status, education, previous loan defaults, existing home loans, personal loans, number of previous client contacts, and month and day of marketing outreach.    

# Executive Summary
A dataset containing information on 41,188 clients of a Portugese bank gathered from multiple marketing campaigns was evaluated to identify what key characteristics drive the successful opening of new bank accounts as a result of targeted marketing activities to existing clients. 

Based on the findings of the project, the main recommendation is to increase the number of interactions with existing clients, as this is by far the most significant driver of marketing campaign and business success. Another recommendation is to carry out targeted marketing campaigns primarily during the months of March and October, followed by the month of September. Further, campaigns during the month of May should be avoided. Finally, the targeting of clients who are retired as well as students has a relatively high correlation with the successful opening of new bank accounts. 

The machine learning models that performed the best were K-Nearest Neighbors (KNN) and Decision Trees, which were able to reach classification accuracies of close to 90%. However, more work remains in incorporating additional features such as macro economic indicators and optimizing the models further, but this is outside of the scope of this project. 

# Introduction and Initial Hypothesis
The initial hypothesis was that the information features Age, Profession, Marital Status, Education, Defaults, Home Loan, and Personal Loan are able to predict which clients would open new bank accounts after targeted marketing campaigns. The initial model had 13% successful account openings in the target variable, which means that the dataset is quite unbalanced. From this follows that the baseline performance that the classifier should aim to beat is 87% accuracy.

# Methodology
A set of input features consisting of Age, Profession, Marital Status, Education, Defaults, Home Loan, and Personal Loan was prepared, including removing rows that contained 'unknown' data, and replacing 'no' and 'yes' values with 0 and 1 values. The different levels of education were encododed with numerical values from 0 to 6 with higher values corresponding to higher education. After that, the different professional categories were encoded as binary values by creating an extra column for each job type. Finally, the resulting dataset was normalized with StandardScaler(), split into training and testing data sets, and then fitted to Logistic Regression, KNN, Decision Trees, and SVM models using their default settings. 

Processing time was recorded, training and testing accuracies were calculated, as well as the recall score. The assumption here is that the bank will want to minimize the number of false negatives in the predictions, as they represent business that is potentially lost by not targeting these clients. 

# Summary: Key Findings and Recommendations
The initial input features yielded limited prediction performance at the baseline or slighly below at around 85-87 percent test accuracy with recall scores of only 5-8 percent. The Decision Tree and KNN models tended to perform the best overall with the SVC model being several magnitudes slower than the other ones:

![First model](https://github.com/fredrik-pettersson/Practical-Application-3/assets/146313002/34d7e82d-27ac-4d2d-bf77-dbb77c78b8c5)


Subsequent optimization of hyperparameters using GridSearchCV did not yield any significant improvement in performance, and in the case of the SVC model, it was not even possible to finish the full set of hyperparameters due to its slow performance.

Therefore, a new set of six input features was prepared based on analysis of the correlation matrix between input features and the target variable y, and conclusions from a research paper. This resulted in a somewhat higher prediction performance with test accuracies around 89% and recall scores from 9% to 22%. The KNN model performed the best overall followed by the Decision Tree and Logistic Regression models. The SVC model performed quite well too, although it was orders of magnitudes slower than the other three models:

![Second model](https://github.com/fredrik-pettersson/Practical-Application-3/assets/146313002/2c149370-3140-48c6-b603-8ac47b8bbc92)


The most significant input feature by far was Previous Contacts with Client, followed by marketing campaigns carried out particularly during the months of March and October, and in the month of September. The month of May had a significant negative correlation, while clients who are either retired or students have relative high correlation with successful bank account openings:

![correlations2](https://github.com/fredrik-pettersson/Practical-Application-3/assets/146313002/42b4b386-3c1e-475e-a43d-e95fd5abebd1)



As can be seen in the below chart, the proportion of successful bank account openings ('yes' marked in red) improves as the number of previous contacts with client increases:

![previous contacts](https://github.com/fredrik-pettersson/Practical-Application-3/assets/146313002/3425319b-9bd6-4bb0-8206-e73a5de175fc)


## Recommendations and Next Steps
Based on the findings of the project, the main recommendation is to increase the number of interactions with existing clients, as this is by far the most significant driver of marketing campaign and business success. Another recommendation is to carry out targeted marketing campaigns primarily during the months of March and October, followed by the month of September. Further, campaigns during the month of May should be avoided. Finally, the targeting of clients who are retired as well as students has a relatively high correlation with the successful opening of new bank accounts. 

The machine learning models that performed the best were K-Nearest Neighbors (KNN) and Decision Trees, which were able to reach classification accuracies of close to 90%. However, more work remains in incorporating additional features such as macro economic indicators and optimizing the models further, but this is outside of the scope of this project. 

  
