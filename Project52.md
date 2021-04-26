## Project 5
Create a new markdown file and upload it to your GitHub repository. Provide a link to your newly created project5.md file from your main index (parts 1 & 2).
Populate your newly created markdown file with your answers to the following questions. Each part of this lab is worth 10 points.
Upload your response no later than midnight on Sunday, April 25th.


Download the anonymized dataset describing city_persons.csv from a larger city in a West African county and import it into your PyCharm project workspace
(right click and download from the above link or you can also find the data pinned to the slack channel). This time we will only use the variable wealthC as your target.
It is not necessary to set a seed.


Import your libraries, functions and create the commands DoKFold, GetData and CompareClasses as we have previously done in class.
Import the data and then complete the following steps.


### Question 1

Execute a K-nearest neighbors classification method on the data. What model specification returned the most accurate results? Did adding a distance weight help?

Using the KNeighborsClassifier, I made the range 70 to 80. This resulted in a k value of 72 and a testing score of 0.5637. This showed that the model isn't overfit. After adding distance as a weight, the KNN Classifier returned a testing score of 0.5003.

### Question 2
Execute a logistic regression method on the data. How did this model fair in terms of accuracy compared to K-nearest neighbors?

The logistic regression method performed relatively similar to the KNeighborsClassifier, with a slightly higher testing score of 0.5447.

### Question 3
Next execute a random forest model and produce the results. See the number of estimators (trees) to 100, 500, 1000 and 5000 and determine which specification is most likely to return the best model. Also test the minimum number of samples required to split an internal node with a range of values. Also produce results for your four different estimator values by both comparing both standardized and non-standardized (raw) results.

I think that the model with 5000 estimators is most likely to return the best model.
Here are the results of the random forest model for 100, 500, 1000, and 5000 estimators:

RAW
Training and Testing Scores of 100 trees: 0.7869 and 0.5012

Training and Testing Scores of 500 trees: 0.7869 and 0.5009

Training and Testing Scores of 1000 trees: 0.7869 and 0.5002

Training and Testing Scores of 50000 trees: 0.7869 and 0.5005

SCALED
Training and Testing Scores of 100 trees: 0.7972 and 0.4997

Training and Testing Scores of 500 trees: 0.7972 and 0.4904

Training and Testing Scores of 1000 trees: 0.7972 and 0.4982

Training and Testing Scores of 50000 trees: 0.7972 and 0.4953

Surprisingly, the model with 100 trees (the least amount of estimators) performed the best, with the highest testing score.

The minimum number of samples required to split an internal node with a range of 10 to 30 was 28.

### Question 4
Repeat the previous steps after recoding the wealth classes 2 and 3 into a single outcome. Do any of your models improve? Are you able to explain why your results have changed?

For the KNN model, testing score increased from 0.5637 to 0.6144.

For the Linear Regression model, testing score increased from 0.5447 to 0.6000.

For the Decision Tree models, the values of all the training and testing data (Raw and Scaled) increased by almost 25%.

Overall, the recoding increased the accuracy of all of the models, some more than others. This may be due to the decreased amount of variance in the data, making accuracy better.

### Question 5

Which of the models produced the best results in predicting wealth of all persons throughout the large West African capital city being described? Support your results with plots, graphs and descriptions of your code and its implementation. You are welcome to incorporate snippets to illustrate an important step, but please do not paste verbose amounts of code within your project report. Avoiding setting a seed essentially guarantees the authenticity of your results. You are welcome to provide a link in your references at the end of your (part 2) Project 5 report.

The KNN model created the best results in predicting wealth before and after recoding the wealth classes 2 and 3. With testing scores of 0.5637 and 0.6144, the KNN model performed better than the Linear and Tree models by a substantial amount. However, the overall accuracy being around 55-60% isn't the greatest.
