15, 17, 21, 22, 24
## Midterm Corrections
### Question 15
	
The remainder of the questions are based on the California House Price data provided by sklearn.  To load this data (you will need an internet connection) you will first need to import:

from sklearn.datasets import fetch_california_housing

After that, the process to unpack the data is similar to what we have done in class with the other sklearn datasets.  The documentation can be found here: https://scikit-learn.org/stable/modules/generated/sklearn.datasets.fetch_california_housing.html



Which of the below features is most strongly correlated with the target?
```
import pandas as pd

```
An alias is used while importing pandas in order to have 'pd' represent pandas. This makes it easier when coding because you don't have to type as much
### Question 17

If we were to perform a linear regression using only the feature identified in question 15, what would be the coefficient of determination? Enter your answer to two decimal places, for example: 0.12

Note: It is possible to compute this in a single line of code.
```
path_to_data = 'C:/Users/Andy Kim/PycharmProjects/pythonProject1/gapminder.tsv'
data = pd.read_csv(path_to_data, sep = '\t')
```
This code creates the path to the gapminder file and saves it as a tab-seperated values file. This is important because it makes sure that the data structure isn't seperated by commas even though the gapminder file is already seperated by tabs.

To describe the data frame createe, use data.describe(). This shows statistics for each column.
To determine the amount of rows and columns, use data.shape()

An alternative terminology for describing rows and columns is as observations and variables.
### Question 21

Let's look at some of what these models are estimating. 

Refit a linear, Ridge, and Lasso regression to the entire (standardized) dataset.  No need to do any train/test splits or K-fold validation here. Use the optimal alpha values you found previously.

Which of these models estimates the smallest coefficient for the variable that is least correlated (in terms of absolute value of the correlation coefficient) with the target?
```
oneYear = data['year'] == 1952
data[oneYear]
```
Using this code, I can look at the data from only 2002 and see that each year has 142 instances. Thus, adding the two years would result in 284 new outcomes into the data frame.
### Question 22
Which of the above models estimates the smallest coefficient for the variable that is most correlated (in terms of the absolute value of the correlation coefficient) with the target?

```
MinLifeExp = data['lifeExp'].min()
idx_Min = data['lifeExp'] == MinLifeExp
data[idx_Min]
```
This can be explained by the Rwandan genocide during the civil war that happened from 1990 - 1994.
### Question 24
	
If we had looked at MSE instead of R2 when doing our Lasso regression (question 20), what would we have determined the optimal value for alpha to be?

Enter your answer to 5 decimal places, for example: 0.12345
```
data['GDP'] = data['pop'] * data['gdpPercap']
important_data = data[(data['country'].isin(['Germany', 'Italy', 'France', 'Spain'])) & (data['year'] == 2007)]
important_filtered = important_data.sort_values('GDP', ascending = False)
```
Here:


Stretch: Germany had the most significant increase in total GDP during the previous 5-year period. I modified the previos subset of the 4 countries with the years 2002 and 2007 using the | operator.
```
stretch_data = data[(data['country'].isin(['Germany', 'Italy', 'France', 'Spain'])) & ((data['year'] == 2007) | (data['year'] == 2002))]
```
