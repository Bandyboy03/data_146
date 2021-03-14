## Project 3

Create a new markdown file and upload it to your GitHub repository. Provide a link to your newly created project3.md file from your main index. Populate your newly created markdown file with your answers to the following questions. This lab is worth 10 points. Upload your response no later than midnight on Tuesday, March 16th.

### Question 1

I set the features to be beds, baths, and square feet, with the target being asking price. Using Kfold, I seperated the data into Testing and Training data with 10 folds. This produced a training score of 0.019 and a testing score of -0.043. These are poor scores because a perfectly fit model would have a score of 1. This shows that the model does not perform well at the current moment.

### Question 2
Now standardize your features (again beds, baths and area) prior to training and testing with a linear regression model (also again with asking price as your target). Now how did your model perform? What were the training and testing scores you produced? How many folds did you assign when partitioning your training and testing data? Interpret and assess your output.



### Question 3
Then train your dataset with the asking price as your target using a ridge regression model. Now how did your model perform? What were the training and testing scores you produced? Did you standardize the data? Interpret and assess your output.


### Question 4
Next, go back, train and test each of the three previous model types/specifications, but this time use the dataset charleston_act.csv (actual sale prices). How did each of these three models perform after using the dataset that replaced asking price with the actual sale price? What were the training and testing scores you produced? Interpret and assess your output.

## Question 5
Go back and also add the variables that indicate the zip code where each individual home is located within Charleston County, South Carolina. Train and test each of the three previous model types/specifications. What was the predictive power of each model? Interpret and assess your output.

##Question 6
Finally, consider the model that produced the best results. Would you estimate this model as being overfit or underfit? If you were working for Zillow as their chief data scientist, what action would you recommend in order to improve the predictive power of the model that produced your best results from the approximately 700 observations (716 asking / 660 actual)?

