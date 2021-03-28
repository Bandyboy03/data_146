## Midterm Corrections

### Importing Libraries
```
from sklearn.linear_model import LinearRegression
from sklearn.datasets import fetch_california_housing
from sklearn.model_selection import KFold
import numpy as np
```
### Defining KFold
```
import pandas as pd
def DoKFold(model, X, y, k, standardize=False, random_state=146):
    if standardize:
        from sklearn.preprocessing import StandardScaler as SS
        ss = SS()

    kf = KFold(n_splits=k, shuffle=True, random_state=random_state)
   
    train_scores = []
    test_scores = []

    train_mse = []
    test_mse = []

    for idxTrain, idxTest in kf.split(X):
        Xtrain = X[idxTrain,:]
        Xtest = X[idxTest,:]
        ytrain = y[idxTrain]
        ytest = y[idxTest]

        if standardize:
            Xtrain = ss.fit_transform(Xtrain)
            Xtest = ss.transform(Xtest)

        model.fit(Xtrain, ytrain)

        train_scores.append(model.score(Xtrain, ytrain))
        test_scores.append(model.score(Xtest, ytest))

        ytrain_pred = model.predict(Xtrain)
        ytest_pred = model.predict(Xtest)

        train_mse.append(np.mean((ytrain - ytrain_pred)**2))
        test_mse.append(np.mean((ytest - ytest_pred)**2))
        
    return train_scores, test_scores, train_mse, test_mse
```
### Importing Data
```
data = fetch_california_housing(as_frame=True)
lin_reg = LinearRegression()

X = np.array(data.data)
y = np.array(data.target)
```

### Question 15
#### My Answer:
```
X = data.data
X_names = data.feature_names
X_df = pd.DataFrame(data = X, columns=X_names)
y = data.target
y_names = data.target_names

sns.heatmap(X_df.corr(), vmin = -1, vmax = 1, cmap = 'bwr')
plt.show()
```
#### Correct Answer:
```
Xy = X_df.copy()
Xy['y'] = y
Xy.corr()
```
#### Reflection
I used a heatmap that showed each of the Correlation Coefficients of the features to the target. This is a viable way to answer the problem, but I wasn't able to get the correct answer because I didn't know how to read the heatmap. I thought that the biggest cluster of red would mean the highest correlation. Thus, I chose Average Rooms instead of Median Income. I can see why I thought that, but it was a dumb mistake on my part.

### Question 17
#### What I did:
```
lin_reg = LinearRegression()
lin_reg.fit(X,y)
lin_reg.score(X,y)
```
#### Correct Answer:
```
np.round(np.corrcoef(X_df['MedInc'], y)[0][1]**2,2)

from sklearn.linear_model import LinearRegression as LR
lin_reg = LR()
lin_reg.fit(X_df['MedInc'].values.reshape(-1,1),y)
np.round(lin_reg.score(X_df['MedInc'].values.reshape(-1,1),y),2)
```
#### Reflection
I knew that I had to use Linear Regression and fit the targets to the features. However, I used the entire dataset of features and targets, instead of subsetting only the feature of "MedInc." I misread the question, so this was another dumb mistake by me. 

### Question 21
#### My Answer:
```
from sklearn.preprocessing import StandardScaler as SS
ss = SS()
Xs = ss.fit_transform(X)
lin_reg.fit(Xs,y)
lin_coefs = lin_reg.coef_

a_range = np.linspace(0,1000,100)

rid_coefs = []
for a in a_range:
    rid_reg = Ridge(alpha=a)
    rid_reg.fit(Xs,y)
    rid_coefs.append(rid_reg.coef_)


plt.figure(figsize=(12,6))
plt.plot(a_range, rid_coefs)
plt.scatter([0]*len(lin_coefs), lin_coefs)
plt.legend(X_names, bbox_to_anchor=[1, 0.5], loc='center left')
plt.xlabel('$\\alpha$')
plt.ylabel('Coeff. Estimates')
plt.show()
```
#### Correct Answer:
```
##21

print(X_names[5])
lin = LR(); rid = Ridge(alpha = 25.8); las = Lasso(alpha=0.00186)
lin.fit(Xs,y); rid.fit(Xs,y); las.fit(Xs.y);
lin.coef_[5], rid.coef_[5], las.coef_[5]
```
#### Reflection
Here, I wasn't sure how to approach the question. I decided to graph all of the Coefficient Estimates of all the features, and look at them to see which had the closest Absolute Value to zero. I think that this approach is useful for quick decision-making, but not in this case where the values are extremely close. To be completely honest, I was very lost on this section and didn't realize that I could solve it in just a couple lines of code with "lin.coef_[5]" and such.
### Question 22
#### My Answer:
```
from sklearn.preprocessing import StandardScaler as SS
ss = SS()
Xs = ss.fit_transform(X)
lin_reg.fit(Xs,y)
lin_coefs = lin_reg.coef_

a_range = np.linspace(0,1000,100)

rid_coefs = []
for a in a_range:
    rid_reg = Ridge(alpha=a)
    rid_reg.fit(Xs,y)
    rid_coefs.append(rid_reg.coef_)


plt.figure(figsize=(12,6))
plt.plot(a_range, rid_coefs)
plt.scatter([0]*len(lin_coefs), lin_coefs)
plt.legend(X_names, bbox_to_anchor=[1, 0.5], loc='center left')
plt.xlabel('$\\alpha$')
plt.ylabel('Coeff. Estimates')
plt.show()
```
#### Correct Answer:
```
##22
print(X_names[0])
lin.coef_[0], rid.coef_[0], las.coef_[0]
```
#### Reflection
This is essentially the same question as 21.

### Question 24
#### My Answer:
```
### Lasso Regression ###

from sklearn.linear_model import Lasso

a_range = np.linspace(0.001, 0.003, 101)

k = 20

avg_tr_score=[]
avg_te_score=[]

for a in a_range:
    las_reg = Lasso(alpha=a)
    train_scores,test_scores = DoKFold(las_reg,X,y,k,standardize=True)
    avg_tr_score.append(np.mean(train_scores))
    avg_te_score.append(np.mean(test_scores))

idx = np.argmax(MSE)
print('Optimal alpha value: ' + format(a_range[idx], '.5f'))
print('Training score for this value: ' + format(avg_tr_score[idx],'.5f'))
print('Testing score for this value: ' + format(avg_te_score[idx], '.5f'))
```
#### Correct Answer:
```
#24

idx = np.argmin(las_te_mse)
print(las_a_range[idx], las_tr[idx], las_te[idx], las_tr_mse[idx], las_te_mse[idx])

plt.plot(las_a_range, las_te_mse, 'or')
plt.xlabel('$\\alpha$')
plt.ylabel('Avg MSE')
plt.show()
```
#### Reflection
To answer this question, I did two different Lasso regressions. I copied the code from my earlier Lasso (which was completely correct), and substituted the "np.argmax()" with MSe inside instead of avg_te_score. I realize that the avg_te_score was only the values from the testing set, and not the entire dataset. Thus, my optimal alpha was 0.001.
