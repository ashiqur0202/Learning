# Learning
This repository is for learning purpose. 
# Data Science

### Data Analysis with Python:-
1. Importing Datasets
2. Data Wrangling
3. Exploratory Data Analysis
4. Model Development
5. Model Evaluation



Python for Data Science
Importing Data
In [ ]:

Data Wrangling
handling missing value
data formatting
data normalization
data binning
catagorical to numerical
Exploratory Data Analysis
In [ ]:

Model Development
Simple and Multiple Linear Regression
Model Evaluation Using Visualization
Polynomial Regression and Pipelines
R-squared amd MSE for In-Sample Evaluation
Prediction and Decision Making
1. Simple and Multiple Linear Regression
Linear Regression

The predictor (independent) value --- x
The target (demendent) value --- y y = b0 + b1x

b0=intercept
b1= slope
Import linear_model from scikit-learn

from sklearn.linear_model import LinearRegression

Create a linear regression object using the constructor

lm=LinearRegression()

We define the predictor variable and target variable x = df[["column name"]] y = df[["column name"]]

Then use lm.fit(x,y) to fit the model, i.e fine the parameters b0 and b1

lm.fit(x,y)

We can obtain a prediction

yhat = lm.predict(x)

Multiple Linear Regression

y = b0 +b1x1+b2x2+b3x3+b4x4

b0=intercept(x=0)
b1=the coefficient or parameter of x1
b2=the coefficient of parameter x2 and so on..
Import linear_model from scikit-learn

from sklearn.linear_model import LinearRegression

Create a linear regression object using the constructor

lm=LinearRegression()

We can extract the for 4 predictor variables and store them in the variable Z Z = df[["column name", "column name", "column name","column name",]]

Then train the model as before:

lm.fit(z, df["column name(price)"])

We can obtain a prediction

yhat = lm.predict(x)

MLR - Estimated Linear Model

Find the intercept(b0)

lm.intercept_

Find the coefficients(b1, b2, b3, b4)

lm.coef_

array[[value, value, value, value]]

The Estimated Linear Model:

Price =

2. Model Evaluation Using Visualization
Regression Plot

import seaborn as sns

sns.regplot(x="column name", y="price", data=df) plt.ylim(0,)

Residual Plot
import seaborn as sns

sns.residpolot(df["column name"], df["price"])

Distribution Plot
import seaborn as sns

ax1 = sns.distplot(df["price"], hist=False, color="r", label="Actual Value"]
sns.distplot(yhat, hist=False, color="b", label="Fitted Values", ax=ax1]

3. Polynomial Regression and Pipelines
Calculate Polynomial Or 3rd order

f=np.polyfit(x,y,3)
p=np.polyld(f)

We can print out the model

print (P)

The "preprocessing" library in scikit-learn

from sklearn.preprocession import PolynomialFeature
pr=PolynomialFeature(degree=2, include_bias=False)
x_polly=pr.fit_transform(x[["column", "column"]])

We can normalize the each feature simultaneously

from sklearn.preprocession import StandardScaler
SCALE=StandardScaler()
SCALE.fit(x_data[["column", "column"]])
x_scale=SCALE.transform(x_data[["column", "column"]])

Pipeline

from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import StandardScaler
from sklearn.pipeline import Pipeline

Pipeline Constructor

Input=[("scale", StandardScaler()), ('polynomial', PolynomialFeatures(degree=2),...('model', LinearRegression())]

Train the Pipeline

Pipe.fit(df[['colum', 'colum', 'colum', 'colum']],y)

Predict the Pipeline

yhat=Pipe.predict(x[['colum', 'colum', 'colum', 'colum']],y)

4. Measures for In-Sample Evaluation
Mean Squared Error (MSE) - value are between 0 and 1
R-squared (R^2)
In Python we can measure the MSE as follows

from sklearn.metrics import mean_squared_error
mean_squared_error(df["price"],y_predict_simple_fit)

We calculate the R^2 as follows

x = df[['column']]
y = df['price']

lm.fit(x,y)

lm.score(x,y)

5. Prediction and Decision Making
To determine final best fit, we look at a combination of:

Do the predicted values make sense
Visualization
Numerical measures for evaluation
Comparing Models
Do the predicted values make sense First we train the model

lm.fit(df["column", df["price"])

Let's predict the value

lm.predict(np.array(30.0).reshape(-1,1))

Result:

lm.coef_

Price = 
First we import numpy
import numpy as np

We use the numpy function arrange to generate a sequence from 1 to 100

new_input=np.arange(1,101,1).reshape(-1,1)

We can predict new values

> yhat = lm.predict(new_input)
For Decision Making follow this things:
Visualization
Regression Plot
Residual Plot
Distribution Plot
Mean Squared Error (MSE)
R-squared (R^2)

Model Evaluation
Training 70% / Testing 30%

Function train_test_split()

c_train, x_test, y_train, y_test = train_test_split(x_data, y_data, test_size=0.3, random_state=0)

Cross Validation

from sklearn.model_selection import cross_val_score score=cross_val_score(lr, x_data, y_data, cv=3) np.mean(score)

Overfitting, Underfitting and Model Selection

Ridge Regression

from sklearn.linear_model import Ridge RidgeModel=Ridge(alpha=0.1)
RidgeModel.fit(x,y)

yhat=RidgeModel.predict(x)

Grid Search

from sklearn.kinear_model import Ridge
from sklearn.model_selection import GridSearchCV

parameters1=[{'alpha':[0.0001, 0.1, 100, 1000]}]
RR=Ridge()

Grid1=GridSearchCV(RR, parameters1, cv=4)
grid1.fit(x_data[['horsepower','curb-weight','engine-size']],y_data)
Grid1.bestestimator

scores=Grid1.cvresults
SCORE['mean_test_score']
