# Project 1 unfinished

## Question 1
A package is a collection of related modules. A library is a collection of packages that is imported in code. To install a package in Pycharm, click on settings, then 'Python Interpreter'. After pressing the plus sign at the bottom of the page, type in the package and install it. While coding, it is necessary to import the library so that you can access the modules/functions. Here are two examples of importing packages:
```
import pandas as pd
import numpy
```
An alias is used while importing pandas in order to have 'pd' represent pandas. This makes it easier when coding because you don't have to type as much
## Question 2
A dataframe is a data structure with rows and columns like a table. Pandas is extremely useful when going through data frames. To read a file in its remote location, use the pandas.read_csv() function. Here is an example of how to read the gapminder file and import it into your work.
```
path_to_data = 'C:/Users/Andy Kim/PycharmProjects/pythonProject1/gapminder.tsv'
data = pd.read_csv(path_to_data, sep = '\t')
```
This code creates the path to the gapminder file and saves it as a tab-seperated values file. This is important because it makes sure that the data structure isn't seperated by commas even though the gapminder file is already seperated by tabs.

To describe the data frame createe, use data.describe(). This shows statistics for each column.
To determine the amount of rows and columns, use data.shape()

An alternative terminology for describing rows and columns is as vectors.
## Question 3
Import the gapminder.tsv data set and create a new data frame. Interrogate and describe the year variable within the data frame you created. Does this variable exhibit regular intervals? If you were to add new outcomes to the raw data in order to update and make it more current, which years would you add to each subset of observations? Stretch goal: can you identify how many new outcomes in total you would be adding to your data frame?

Looking only at the year variable of the data frame, we can see that it has regular intervals of 5 years. If we were to add new outcomes and update it, we would add the years 2012 and 2017.
```
oneYear = data['year'] == 2002
data[oneYear]
```
Using this code, I can look at the data from only 2002 and see that each year has 142 instances. Thus, adding the two years would result in 284 new outcomes into the data frame.
## Question 4
The country with the lowest life expectancy in the data frame was Rwanda in 1992,with a life expectancy of 23.599. 
To find this data, I found the index of the minimum life expectancy in the data and then used that index to find all information about that particular observation.
```
MinLifeExp = data['lifeExp'].min()
idx_Min = data['lifeExp'] == MinLifeExp
data[idx_Min]
```
This can be explained by the Rwandan genocide during the civil war that happened from 1990 - 1994.
## Question 5
Using the data frame you created by importing the gapminder.tsv data set, multiply the variable pop by the variable gdpPercap and assign the results to a newly created variable. Then subset and order from highest to lowest the results for Germany, France, Italy and Spain in 2007. Create a table that illustrates your results (you are welcome to either create a table in markdown or plot/save in PyCharm and upload the image). Stretch goal: which of the four European countries exhibited the most significant increase in total gross domestic product during the previous 5-year period (to 2007)?

```
data['GDP'] = data['pop'] * data['gdpPercap']
important_data = data[(data['country'].isin(['Germany', 'Italy', 'France', 'Spain'])) & (data['year'] == 2007)]
important_filtered = important_data.sort_values('GDP', ascending = False)
```
Here:

![](Project1Table.PNG)

Stretch: Germany had the most significant increase in total GDP during the previous 5-year period. This was calculated by creating a subset of the 4 countries with the years 2002 and 2007. Then, the GDP between the years was calculated by subtracting. Finally, the highest increase was measured using > and < statements.
```
stretch_data = data[(data['country'].isin(['Germany', 'Italy', 'France', 'Spain'])) & ((data['year'] == 2007) | (data['year'] == 2002))]
```
## Question 6
You have been introduced to four logical operators thus far: &, ==, | and ^. Describe each one including its purpose and function. Provide an example of how each might be used in the context of programming.

The logical operators &, ==, |, and ^ are used in conditional statements or functions that include two values/variables.

&, the AND operator, returns true if both conditional statements are true.
Example: If the country is Germany AND the year is 2007, return true

==, the Equals operator, returns true if two values/variables are the same.
Example: If 5+5 == 10, return true

|, the OR operator, returns true if one of the conditional statements is true.
Example: If the country is US OR Canada, return true

^, the XOR operator, returns true if only one of the conditional statements is true.
Example: If 
## Question 7
Describe the difference between .loc and .iloc. Provide an example of how to extract a series of consecutive observations from a data frame. Stretch goal: provide an example of how to extract all observations from a series of consecutive columns.

```

```
## Question 8
Describe how an api works. Provide an example of how to construct a request to a remote server in order to pull data, write it to a local file and then import it to your current work session.

```

```
## Question 9
Describe the apply() function from the pandas library. What is its purpose? Using apply) to various class objects is an alternative (potentially preferable approach) to writing what other type of command? Why do you think apply() could be a preferred approach?

```

```
## Question 10
Also describe an alternative approach to filtering the number of columns in a data frame. Instead of using .iloc, what other approach might be used to select, filter and assign a subset number of variables to a new data frame?
```

```
