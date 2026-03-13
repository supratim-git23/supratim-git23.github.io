---
layout: post
title: Some Practical program implemented in Python 3.12, can be used for AI/ML
date: 13-03-2026
categories: [documentations]
tag: [like,comment,subscribe]
---



```python
# Matrix multiplication

import numpy as np
A = np.array([[1, 2, 3],
              [4, 5, 6],
              [7, 8, 9]])

print("3x3 Matrix: A: ")
print(A)

B = np.array([[1, 4, 7],
              [2, 5, 8],
              [3, 6, 9]])

print("3x3 Matrix: B :")
print(B)
C = np.dot(A, B)
# we also use C=A@B
print("3x3 Matrix: C(result of multiplication) :")
print(C)



```

    3x3 Matrix: A: 
    [[1 2 3]
     [4 5 6]
     [7 8 9]]
    3x3 Matrix: B :
    [[1 4 7]
     [2 5 8]
     [3 6 9]]
    3x3 Matrix: C(result of multiplication) :
    [[ 14  32  50]
     [ 32  77 122]
     [ 50 122 194]]
    


```python
# finding the inverse of a Matrix
import numpy as np
from scipy import linalg


# Define matrix A
A = np.array([[1, 2, 3],
              [0, 1, 4],
              [5, 6, 0]])

# Calculate determinant
det = linalg.det(A)

print("Matrix A:")
print(A)

print("\nDeterminant:", det)

# Check if matrix is invertible
if det != 0:
    A_inv = linalg.inv(A)
    print("\nMatrix is invertible.")
    print("Inverse of A:")
    print(A_inv)
else:
    print("\nMatrix is NOT invertible (determinant = 0).")
```

    Matrix A:
    [[1 2 3]
     [0 1 4]
     [5 6 0]]
    
    Determinant: 0.9999999999999987
    
    Matrix is invertible.
    Inverse of A:
    [[-24.  18.   5.]
     [ 20. -15.  -4.]
     [ -5.   4.   1.]]
    


```python
import math

# input coordinates
x1 = float(input("Enter x1: "))
y1 = float(input("Enter y1: "))
x2 = float(input("Enter x2: "))
y2 = float(input("Enter y2: "))

# calculate Euclidean distance
distance = math.sqrt((x2 - x1)**2 + (y2 - y1)**2)
#distance = math.sqrt(math.pow(x2-x1,2) + math.pow(y2-y1,2))     this can also be used
print("Euclidean Distance =", distance)
```

    Enter x1: 1
    Enter y1: 2
    Enter x2: 3
    Enter y2: 4
    Euclidean Distance = 2.8284271247461903
    


```python
# alternative method
import math

# Points stored in arrays
A = [2, 3]
B = [6, 7]

# Calculate Euclidean distance
sum_sq = 0
for i in range(len(A)):
    sum_sq += (A[i] - B[i]) ** 2

distance = math.sqrt(sum_sq)

print("Euclidean Distance =", distance)
```

    Euclidean Distance = 5.656854249492381
    


```python
# alternative method
# use of zip function
import math

# Points stored in arrays
A = [2, 3]
B = [6, 7]

# Calculate Euclidean distance
distance = math.sqrt(sum((a - b) ** 2 for a, b in zip(A, B)))

print("Euclidean Distance =", distance)
```

    Euclidean Distance = 5.656854249492381
    


```python
import math

def euclidean_distance(vector1, vector2):
    
    if len(vector1) == len(vector2):
        squared_differences_sum = 0
        for i in range(len(vector1)):
            squared_differences_sum += (vector1[i] - vector2[i]) ** 2
        return math.sqrt(squared_differences_sum)
    else:
        Print("Vectors must have the same dimensions.")


# Example Usage- 2D:

vector_a = [10, 20]
vector_b = [15, 25]

distance_2d = euclidean_distance(vector_a, vector_b)
print(f"The Euclidean distance between {vector_a} and {vector_b} is: {distance_2d}")

# Example Usage 3D:
vector_c = [1, 2, 3]
vector_d = [4, 5, 6]

distance_3d = euclidean_distance(vector_c, vector_d)
print(f"The Euclidean distance between {vector_c} and {vector_d} is: {distance_3d}")
```

    The Euclidean distance between [10, 20] and [15, 25] is: 7.0710678118654755
    The Euclidean distance between [1, 2, 3] and [4, 5, 6] is: 5.196152422706632
    


```python
# read csv file
import os
import pandas as pd

# Read CSV file
data = pd.read_csv('C:/hs1.csv')

# Display the data(5)
print(data.head())
```

      name  age  income
    0   RC   33   33056
    1   AS   45   45056
    2   AC   38   38056
    3   AD   13   13056
    4   AF   16   16056
    


```python
# read csv file
import os
import pandas as pd

# Read CSV file
data = pd.read_csv('C:/hs1.csv')

#display particular column

data1=data['name']

# Display the data (5)
print(data1.head())
```

    0    RC
    1    AS
    2    AC
    3    AD
    4    AF
    Name: name, dtype: object
    


```python
# Alternative method -    good as the column name will also appear
import os
import pandas as pd

# Read CSV file
data = pd.read_csv('C:/hs1.csv', usecols=["name"])
print(data.head())
```

      name
    0   RC
    1   AS
    2   AC
    3   AD
    4   AF
    


```python
# finding correlation coefficient
def pearson_correlation(x, y):
    n = len(x)
    if n != len(y) or n == 0:
        return None  # Invalid input

    # Calculate means
    sum_x = sum(x)
    sum_y = sum(y)
    mean_x = sum_x / n
    mean_y = sum_y / n

    # Calculate standard deviations
    sum_sq_x = sum([(i - mean_x)**2 for i in x])
    sum_sq_y = sum([(i - mean_y)**2 for i in y])
    
    try:
        std_x = (sum_sq_x / n)**0.5
        std_y = (sum_sq_y / n)**0.5
    except ZeroDivisionError:
        return 0.0  # Handle cases with zero standard deviation

    # Calculate covariance
    covariance = sum([(x[i] - mean_x) * (y[i] - mean_y) for i in range(n)]) / n

    # Calculate Pearson correlation coefficient
    try:
        correlation_coefficient = covariance / (std_x * std_y)
    except ZeroDivisionError:
        return 0.0

    return correlation_coefficient


# Example Usage (replace with your data)
age = [25, 30, 35, 40, 45]
income = [50000, 60000, 70000, 80000, 90000]

correlation = pearson_correlation(age, income)

print(f"Pearson correlation coefficient: {correlation}")

```

    Pearson correlation coefficient: 1.0
    


```python
# alternatively
import numpy as np
import random

x=[1,2,3,5,7,8,9,4,6]
y=[11,22,33,55,77,88,99,44,66]


x_bar=sum(x)/len(x)
y_bar=sum(y)/len(y)

n=len(x)   # equals len(y) also
print(n)

print(f'x_bar= {x_bar}, y_bar={y_bar}')

n_cov_x_y=0


for xi,yi in zip(x,y):
     n_cov_x_y += (xi-x_bar)*(yi-y_bar)

cov_x_y = n_cov_x_y/n

print(f'covariance ={cov_x_y}')

sigma_x_sqr=0
sigma_y_sqr=0


for k in range(n):
     sigma_x_sqr += (x[k]-x_bar)**2
        
for l in range(n):      
     sigma_y_sqr += (y[l]-y_bar)**2


# Calculate standard deviations
sigma_x=((sigma_x_sqr/n)**0.5)

sigma_y=((sigma_y_sqr/n)**0.5)

r=cov_x_y/(sigma_x*sigma_y)

print(f'Pearson correlation coefficient  ={r}')
```

    9
    x_bar= 5.0, y_bar=55.0
    covariance =73.33333333333333
    Pearson correlation coefficient  =1.0
    


```python
# linear regression
import numpy as np
import random

x=[2,3,5,7,8,9,4,12]
y=[22,33,55,81,89,96,48,127]


m=1
c=1

learning_rate=.01


def grad_desc(x,y,m,c,learning_rate):
    dldm=0
    dldc=0
    n=len(x)
    for xi,yi in zip(x,y):
        dldm += -2*xi*(yi-(m*xi+c))
        dldc += -2*(yi-(m*xi+c))
    
    m=m-(1/n)*learning_rate*dldm
    
    c=c-(1/n)*learning_rate*dldc
    
    return m, c 


def mse(y_true, y_pred):
    y_true = np.array(y_true)
    y_pred = np.array(y_pred)
    return np.mean((y_true - y_pred) ** 2)

# Assuming x and y are NumPy arrays
x = np.array(x)  # Ensure x is a NumPy array
y = np.array(y)  # Ensure y is a NumPy array

for epoch in range(100):
    m,c = grad_desc(x,y,m,c,learning_rate)
    yhat= m*x+c
    loss= mse(y,yhat)
    
    print(f'epoch: {epoch}, loss ={loss} for m={m},c={c}')

```

    epoch: 0, loss =6.017884375 for m=10.5875,c=2.2325
    epoch: 1, loss =5.941109893984372 for m=10.6251875,c=2.2419124999999998
    epoch: 2, loss =5.939060294149141 for m=10.6247646875,c=2.2464258125
    ......
    epoch: 97, loss =5.80328770131262 for m=10.579367442770804,c=2.6008956505093472
    epoch: 98, loss =5.802337163530998 for m=10.578975392541746,c=2.6039568071528096
    epoch: 99, loss =5.801394197664435 for m=10.578584906956733,c=2.607005746942035
    


```python
# using statmodel
import numpy as np
import statsmodels.api as sm

X=np.array([2,3,5,7,8,9,4,12])            # Independent variable
Y=np.array([22,33,55,81,89,96,48,127])    # Dependent variable

     

X = sm.add_constant(X)          # Add intercept
model = sm.OLS(Y, X).fit()      # Fit regression model

print(model.params)
```

    [ 3.36792453 10.48113208]
    


```python
# creating random linear function
import numpy as np
import pandas as pd
import random

# Set a random offset
r_d = random.randint(0, 16)

# List to store the (x, y) pairs
data = []

# Generate 100 pairs
for i in range(100):
    r_x = random.randint(0, 256)
    r_y = 4 * r_x + 4 + r_d
    data.append((r_x, r_y))

# Create a DataFrame
df = pd.DataFrame(data, columns=['x', 'y'])

# Display the first few rows
print(df.head())


#df.to_csv("random_data.csv", index=False)
```

         x    y
    0   72  301
    1  156  637
    2    8   45
    3  206  837
    4  164  669
    


```python
#  Generation of random (x, y) pairs where y = f(x) + d (d varies from -r to +r , 
# a random value ), f being a linear function 
#  Linear regression or line fitting of the data 
# Optimizing the function using gradient descent 
# Plotting the steps using matplotlib 

import numpy as np
import matplotlib.pyplot as plt

# True parameters
m_true = 2
c_true = 1
r = 2

# Generate random x values
x = np.linspace(0, 10, 50)

# Random noise
d = np.random.uniform(-r, r, len(x))

# Generate y values
y = m_true * x + c_true + d

# Initial guess for parameters
m = 0
c = 0

learning_rate = 0.01
epochs = 20

plt.scatter(x, y, color='blue', label='Data')

# Gradient descent
for i in range(epochs):

    y_pred = m*x + c

    # gradients
    dm = (-2/len(x)) * np.sum(x*(y - y_pred))
    dc = (-2/len(x)) * np.sum(y - y_pred)

    # update parameters
    m = m - learning_rate*dm
    c = c - learning_rate*dc

    # plot intermediate lines
    plt.plot(x, y_pred, alpha=0.3)

# Final fitted line
plt.plot(x, m*x + c, color='red', linewidth=3, label='Fitted Line')

plt.legend()
plt.title("Linear Regression using Gradient Descent")
plt.show()

```


    

    <img width="543" height="433" alt="output_14_0" src="https://github.com/user-attachments/assets/aed9f829-2a89-48ab-b0ba-f2f25ba0948b" />




```python
# alternatively
import numpy as np
import pandas as pd
import random
from sklearn.linear_model import LinearRegression
import matplotlib.pyplot as plt

# Create and store data
data = []
for i in range(100):
    r_d = random.randint(0, 316)  # Generate random offset
    r_x = random.randint(0, 256)
    r_y = 4 * r_x + 4 + r_d
    data.append((r_x, r_y))

# Create DataFrame
df = pd.DataFrame(data, columns=['x', 'y'])

# Print sample
print(df.head())

# Save to CSV (optional)
#df.to_csv("random_data.csv", index=False)

# Reshape x for scikit-learn (expects 2D input)
X = df[['x']]   # or df['x'].values.reshape(-1, 1)
y = df['y']

# Create and fit the linear regression model
model = LinearRegression()
model.fit(X, y)

# Get model parameters
slope = model.coef_[0]
intercept = model.intercept_

print(f"\nFitted Linear Model: y = {slope:.2f}x + {intercept:.2f}")

# Predict y values for plotting
y_pred = model.predict(X)

# Plotting
plt.scatter(X, y, color='blue', label='Actual Data')
plt.plot(X, y_pred, color='red', linewidth=2, label='Regression Line')
plt.title('Linear Regression Fit')
plt.xlabel('x')
plt.ylabel('y')
plt.legend()
plt.grid(True)
plt.show()
```

         x     y
    0   61   320
    1  191   808
    2   81   337
    3  206  1006
    4  186   862
    
    Fitted Linear Model: y = 3.91x + 163.11
    


        
<img width="580" height="453" alt="output_15_1" src="https://github.com/user-attachments/assets/387f240c-5744-4f91-9d5e-9aa8aae99f07" />



```python
# LR without using ML
import numpy as np

# 1. Define the same sample data
# X = 'Hours Studied', y = 'Test Score'
X = np.array([1, 2, 3, 4, 5])
y = np.array([50, 65, 75, 80, 95])

# 2. Count the number of data points (n)
n = len(X)

# 3. Calculate all the required raw sums
sum_x = np.sum(X)
sum_y = np.sum(y)
sum_xy = np.sum(X * y)
sum_x_squared = np.sum(X ** 2)

#denominator for bith is same
denominator = (n * sum_x_squared) - (sum_x ** 2)


# 4. Apply the raw score formula for slope (a, may be call m)
numerator_a = (n * sum_xy) - (sum_x * sum_y)

a = numerator_a / denominator



# 5. Apply the raw score formula for intercept (b, may be call c)

numerator_b= (sum_y*sum_x_squared) - (sum_x*sum_xy)

b=numerator_b / denominator



print(f'The required slope is {b}, the required intercept is {a}')


```

    The required slope is 41.5, the required intercept is 10.5
    


```python
# Prediction using LR
import numpy as np

# 1. Define the same sample data
# X = 'Hours Studied', y = 'Test Score'
X = np.array([1, 2, 3, 4, 5])
y = np.array([50, 65, 75, 80, 95])

# 2. Count the number of data points (n)
n = len(X)

# 3. Calculate all the required raw sums
sum_x = np.sum(X)
sum_y = np.sum(y)
sum_xy = np.sum(X * y)
sum_x_squared = np.sum(X ** 2)

# 4. Apply the raw score formula for slope (m)
numerator_m = (n * sum_xy) - (sum_x * sum_y)
denominator_m = (n * sum_x_squared) - (sum_x ** 2)
m = numerator_m / denominator_m

# 5. Apply the raw score formula for y-intercept (c)
c = (sum_y - (m * sum_x)) / n

# 6. Output the results
print("--- Alternative Linear Regression Formula Implemented ---")
print(f"Slope (m): {m}")
print(f"Y-Intercept (c): {c}")
print(f"Equation of the line: y = {m}x + {c}")

# 7. Make a prediction 
x_new = 3.5
y_pred = (m * x_new) + c
print(f"\nPrediction for X = {x_new}: y = {y_pred}")
```

    --- Alternative Linear Regression Formula Implemented ---
    Slope (m): 10.5
    Y-Intercept (c): 41.5
    Equation of the line: y = 10.5x + 41.5
    
    Prediction for X = 3.5: y = 78.25
    


```python
# Logistic regression
from sklearn import datasets
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, classification_report

# 1. Load the Iris dataset
iris = datasets.load_iris()
X = iris.data   # Features: sepal length, sepal width, petal length, petal width
y = iris.target # Target: 0 (setosa), 1 (versicolor), 2 (virginica)

# 2. Split the data into training (80%) and testing (20%) sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# 3. Initialize the Multinomial Logistic Regression model
# - multi_class='multinomial': Tells the model to use the Softmax loss function for multiclass
# - solver='lbfgs': An optimization algorithm that works well for multinomial loss
# - max_iter=200: Gives the algorithm enough iterations to converge
model = LogisticRegression(multi_class='multinomial', solver='lbfgs', max_iter=200)

# 4. Train the model using the training data
model.fit(X_train, y_train)

# 5. Make predictions on the testing data
y_pred = model.predict(X_test)

# 6. Evaluate the model's performance
print("--- Multiclass Logistic Regression Results ---\n")
print(f"Overall Accuracy: {accuracy_score(y_test, y_pred) * 100:.2f}%\n")
print("Detailed Classification Report:")
print(classification_report(y_test, y_pred, target_names=iris.target_names))
```

    --- Multiclass Logistic Regression Results ---
    
    Overall Accuracy: 100.00%
    
    Detailed Classification Report:
                  precision    recall  f1-score   support
    
          setosa       1.00      1.00      1.00        10
      versicolor       1.00      1.00      1.00         9
       virginica       1.00      1.00      1.00        11
    
        accuracy                           1.00        30
       macro avg       1.00      1.00      1.00        30
    weighted avg       1.00      1.00      1.00        30
    
    


```python
# Finding Entropy
from scipy.stats import entropy
p = [0.9, 0.1] # probability distribution
ent = entropy(p, base=2)
print("Entropy:", ent)
```

    Entropy: 0.46899559358928117
    


```python
# Decision tree
from sklearn import datasets
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import accuracy_score, classification_report

# 1. Load the Iris dataset
iris = datasets.load_iris()
X = iris.data   # Features: sepal length, sepal width, petal length, petal width
y = iris.target # Target: 0 (setosa), 1 (versicolor), 2 (virginica)

# 2. Split the data into training (80%) and testing (20%) sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# 3. Initialize the Decision Tree Classifier
# Setting max_depth=3 keeps the tree simple and prevents it from memorizing the training data.
# random_state=42 ensures you get the exact same results every time you run the code.
model = DecisionTreeClassifier(max_depth=3, random_state=42)

# 4. Train the model using the training data
model.fit(X_train, y_train)

# 5. Make predictions on the testing data
y_pred = model.predict(X_test)

# 6. Evaluate the model's performance
print("--- Decision Tree Classifier Results ---\n")
print(f"Overall Accuracy: {accuracy_score(y_test, y_pred) * 100:.2f}%\n")
print("Detailed Classification Report:")
print(classification_report(y_test, y_pred, target_names=iris.target_names))
```

    --- Decision Tree Classifier Results ---
    
    Overall Accuracy: 100.00%
    
    Detailed Classification Report:
                  precision    recall  f1-score   support
    
          setosa       1.00      1.00      1.00        10
      versicolor       1.00      1.00      1.00         9
       virginica       1.00      1.00      1.00        11
    
        accuracy                           1.00        30
       macro avg       1.00      1.00      1.00        30
    weighted avg       1.00      1.00      1.00        30
    
    


```python

```
