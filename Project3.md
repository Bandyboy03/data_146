## Project 3

Create a new markdown file and upload it to your GitHub repository. Provide a link to your newly created project3.md file from your main index. Populate your newly created markdown file with your answers to the following questions. This lab is worth 10 points. Upload your response no later than midnight on Tuesday, March 16th.

### Question 1

I set the features to be beds, baths, and square feet, with the target being asking price. Using Kfold, I seperated the data into Testing and Training data with 10 folds. This produced a training score of 0.019 and a testing score of -0.043. These are poor scores because a perfectly fit model would have a score of 1. This shows that the model does not perform well at the current moment.

### Question 2
After standardizing the features with StandardScaler, the model still performed poorly. I kept the folds at 10 to keep it consistent. The model had a training score of 0.020 and a testing score of -0.038. Although, the scores ma;y have improved slightly, there is still a long way to go.

### Question 3
Then train your dataset with the asking price as your target using a ridge regression model. Now how did your model perform? What were the training and testing scores you produced? Did you standardize the data? Interpret and assess your output.


### Question 4
Next, go back, train and test each of the three previous model types/specifications, but this time use the dataset charleston_act.csv (actual sale prices). How did each of these three models perform after using the dataset that replaced asking price with the actual sale price? What were the training and testing scores you produced? Interpret and assess your output.

### Question 5

Non-Standardized: Training score of 0.339//Testing score of 0.217


Standardized: Training score of 0.339//Testing score of 0.243


Ridge Regression:Training score of 0.336//Testing score of 0.229

Indicating the zip code where each individual home is located greatly improved the model's accuracy. The Non-standardized, standardized, and ridge regression models all had positive testing and training scores. This is a huge improvement that could suggests that housing prices rely on their locations (zip codes). I kept the folds at 10.


### Question 6
The Standardized model with zip codes produced the best results. I estimate that this model is being overfit, due to the training score being higher than the testing score. In order to improve the predictive power of the model, I would recommend that they add more variables. They could add crime rate in the area, access to education and convenience stores, or many other variables that determine the price of a house.
