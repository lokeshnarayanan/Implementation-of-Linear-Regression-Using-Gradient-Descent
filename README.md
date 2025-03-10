# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import the required library and read the dataframe.

2.Write a function computeCost to generate the cost function.

3.Perform iterations og gradient steps with learning rate.

4.Plot the Cost function using Gradient Descent and generate the required graph.

## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: Lokesh N
RegisterNumber: 212222100023 
*/
```
```python
import numpy as np
import pandas as pd
from sklearn.preprocessing import StandardScaler
def linear_regression(x1,y,learning_rate=0.01,num_iters=100):
  x=np.c_[np.ones(len(x1)),x1]
  theta=np.zeros(x.shape[1]).reshape(-1,1)
  for _ in range(num_iters):
    predictions=(x).dot(theta).reshape(-1,1)
    errors=(predictions-y).reshape(-1,1)
    theta-=learning_rate*(1/len(x1))*x.T.dot(errors)
  return theta
data=pd.read_csv('50_Startups.csv',header=None)
x=(data.iloc[1:,:-2].values)
x1=x.astype(float)
scaler=StandardScaler()
y=(data.iloc[1:,-1].values).reshape(-1,1)
x1_Scaled=scaler.fit_transform(x1)
y1_Scaled=scaler.fit_transform(y)

theta=linear_regression(x1_Scaled, y1_Scaled)

new_data=np.array([165349.2,136897.8,471784.1]).reshape(-1,1)
new_Scaled=scaler.fit_transform(new_data)
prediction=np.dot(np.append(1,new_Scaled),theta)
prediction=prediction.reshape(-1,1)
pre=scaler.inverse_transform(prediction)
print(f"Predicted value: {pre}")

```
## Output:
## data table:
![Screenshot 2024-03-08 115101](https://github.com/lokeshnarayanan/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/119393019/36a9ae86-b534-4cbb-8dd0-cded8b0cd877)
## predicted value:
![Screenshot 2024-03-08 114206](https://github.com/lokeshnarayanan/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/119393019/d195b7da-b300-4d9e-a2bd-fe4afefd7bc5)


## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
