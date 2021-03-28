## Midterm Corrections
### Question 15
The remainder of the questions are based on the California House Price data provided by sklearn.  To load this data (you will need an internet connection) you will first need to import:

from sklearn.datasets import fetch_california_housing

After that, the process to unpack the data is similar to what we have done in class with the other sklearn datasets.  The documentation can be found here: https://scikit-learn.org/stable/modules/generated/sklearn.datasets.fetch_california_housing.html

Which of the below features is most strongly correlated with the target?

#### My Answer:
```
import pandas as pd
```
#### Correct Answer:
```
```
#### Reflection
An alias is used while importing pandas in order to have 'pd' represent pandas. This makes it easier when coding because you don't have to type as much
### Question 17

If we were to perform a linear regression using only the feature identified in question 15, what would be the coefficient of determination? Enter your answer to two decimal places, for example: 0.12

Note: It is possible to compute this in a single line of code.
#### My Answer:
```
import pandas as pd
```
#### Correct Answer:
```
```
#### Reflection
An alias is used while importing pandas in order to have 'pd' represent pandas. This makes it easier when coding because you don't have to type as much
### Question 21

Let's look at some of what these models are estimating. 

Refit a linear, Ridge, and Lasso regression to the entire (standardized) dataset.  No need to do any train/test splits or K-fold validation here. Use the optimal alpha values you found previously.

Which of these models estimates the smallest coefficient for the variable that is least correlated (in terms of absolute value of the correlation coefficient) with the target?
#### My Answer:
```
import pandas as pd
```
#### Correct Answer:
```
```
#### Reflection
An alias is used while importing pandas in order to have 'pd' represent pandas. This makes it easier when coding because you don't have to type as much
### Question 22
Which of the above models estimates the smallest coefficient for the variable that is most correlated (in terms of the absolute value of the correlation coefficient) with the target?

#### My Answer:
```
import pandas as pd
```
#### Correct Answer:
```
```
#### Reflection
An alias is used while importing pandas in order to have 'pd' represent pandas. This makes it easier when coding because you don't have to type as much
### Question 24
	
If we had looked at MSE instead of R2 when doing our Lasso regression (question 20), what would we have determined the optimal value for alpha to be?

Enter your answer to 5 decimal places, for example: 0.12345
#### My Answer:
```
import pandas as pd
```
#### Correct Answer:
```
```
#### Reflection
An alias is used while importing pandas in order to have 'pd' represent pandas. This makes it easier when coding because you don't have to type as much
