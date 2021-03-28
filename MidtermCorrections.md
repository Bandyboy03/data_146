## Midterm Corrections

### Importing Libraries and Data
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
import pandas as pd
```
#### Correct Answer:
```
### K-fold cross validation ###

def DoKFold(model, X, y, k, standardize=False, random_state=146):
# def DoKFold(model, X, y, k, standardize=False):
    from sklearn.model_selection import KFold
    if standardize:
        from sklearn.preprocessing import StandardScaler as SS
        ss = SS()

    kf = KFold(n_splits=k, shuffle=True, random_state=random_state)
    # kf = KFold(n_splits=k, shuffle=True)

    train_scores = []
    test_scores = []

    train_mse = []
    test_mse = []
    
    for idxTrain, idxTest in kf.split(X):
        Xtrain = X[idxTrain, :]
        Xtest = X[idxTest, :]
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
        
        train_mse.append(np.mean((ytrain - ytrain_pred) ** 2))
        test_mse.append(np.mean((ytest - ytest_pred) ** 2))
        

    return train_scores, test_scores, train_mse, test_mse

from sklearn.datasets import fetch_california_housing as ld

data = ld()

X = data.data
X_names = data.feature_names

y = data.target

X_df = pd.DataFrame(X, columns = X_names)

plt.hist(y, rwidth = 0.9)
plt.xlabel('Avg House Price (US $100k)')
plt.ylabel('Count')
plt.show()

## 15
Xy = X_df.copy()
Xy['y'] = y
Xy.corr()
```
#### Reflection
An alias is used while importing pandas in order to have 'pd' represent pandas. This makes it easier when coding because you don't have to type as much

### Question 17
#### My Answer:
```
import pandas as pd
```
#### Correct Answer:
```
## 17 
np.round(np.corrcoef(X_df['MedInc'], y)[0][1]**2,2)

from sklearn.linear_model import LinearRegression as LR
lin_reg = LR()
lin_reg.fit(X_df['MedInc'].values.reshape(-1,1),y)
np.round(lin_reg.score(X_df['MedInc'].values.reshape(-1,1),y),2)
```
#### Reflection
An alias is used while importing pandas in order to have 'pd' represent pandas. This makes it easier when coding because you don't have to type as much

### Question 21
#### My Answer:
```
import pandas as pd
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
An alias is used while importing pandas in order to have 'pd' represent pandas. This makes it easier when coding because you don't have to type as much

### Question 22
#### My Answer:
```
import pandas as pd
```
#### Correct Answer:
```
##22
print(X_names[0])
lin.coef_[0], rid.coef_[0], las.coef_[0]
```
#### Reflection
An alias is used while importing pandas in order to have 'pd' represent pandas. This makes it easier when coding because you don't have to type as much

### Question 24
#### My Answer:
```
import pandas as pd
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
An alias is used while importing pandas in order to have 'pd' represent pandas. This makes it easier when coding because you don't have to type as much
