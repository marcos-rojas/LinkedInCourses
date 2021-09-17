## Car Price Prediction
We would like to help user to come up with best price: develop a model with *Car Features and MSRP* [Kaggle Dataset](https://www.kaggle.com/CooperUnion/cardataset).
Among features, we would like to predict MSRP (Manufacturer's suggested retail price). Thus, we would follow a project plan:
- Prepare data (column name, value name format) and do Exploratory Data Analysis
```python
# Some commands we've used
data = read_csv(filenpath)
data.columns
data_replaced = data_df.columns.str.lower().str.replace(' ','_') # lowercase columns and replace spaces
stringData = list(data_df.dtypes[data_df.dtypes == "object"].index) #data column names that are objects with index

# We work over each column value in string format to add _ and lowercase
for col in stringData:
    data_df[col] = data_df[col].str.lower().str.replace(' ','_')
data_df.head()
data_df.isnull().sum() # number of null elements by each column
```
```python
for col in data_df.columns:
    print(col) #print column name
    print(data_df[col].unique()[:5]) #print 5 unique element list
    print(data_df[col].nunique()) #print number of unique elements in a column
```
```python
# Visualizing data
import matplotlib.pyplot as plt
import seaborn as sns
sns.histplot(data_df.msrp, bins=10) #plotting the histogram
sns.histplot(data_df.msrp[data_df.msrp < 100000], bins= 50) #plotting just msrp less than 100k
price_logs = np.log1p(data_df.msrp) #calculating log(1+x of data) to convert to a log scacale
sns.histplot(price_logs, bins= 50) #plotting
```
- Prepare data : Setting the validation framework (train, validation and test data groups)
There are already some libraries but it would be useful if we manipulate data by ourselves
```python
idx = np.arange(n) # we get a set/array of index values shuffled to make it random
np.random.seed(2)
np.random.shuffle(idx)
df_val = data_df.iloc[idx[:n_val]] # each group is selected with iloc method and the idx order
df_train = df_train.reset_index(drop = True) # we delete the previous index values (when were part of bigger dataset)
y_train = np.log1p(df_train.msrp.values) # sabe output values in another variable
del df_train['msrp'] # delete the columns with the output variable to training without it
```
- Use linear regression to price prediction
From *g(x)=y* we know g() is our linear regression model (which we want to get), x is a feature matrix and y is our desired output (values predicted).
For one observation: *g(x_i) = y_i*, where x_i is a vector = (x_i1, x_i2, ...x_in). Because we want a function which combines this values and return us our output y_i.
Then, we start by giving a form of linear equation to g(x_i) = w_0+w_1\*x_i1+...+w_n\*x_in -> g(x_i) = w_o + sum(w_j\*x_ij) (here 'i' doesn't change). Don't forget we've
made a log(y+1), so we should make e^(x_i)-1 to get our result.
w_0 is bias (if we didn't know anything about data)
```python
xi = [453, 11, 86]
w0 = 7.17
w = [0.01, 0.04, 0.002]
def linear_regression(xi):
    n = len(xi)
    pred = w0
    for j in range(n):
        pred = pred + w[j]*xi[j]
    return pred
```
- Understand linear regression logic
**Linear regression in vector form** We need to generalize our equation to *g(X) = y*. From past equation (w_0 + sum(w_j\*x_ij)), we can reformulate
in a way that we get a vector dot product (add 1 parameter at beginning of x_ij). Thus 
```python
w = [w0, w1, w2, w3, .. wn]
x = [1, x1, x2, x3...xn]
# Thus X.T*w is what we've found before
# remember that [w0] + w = [w0 ...w] for numpy array
X = [[1 x11 x12 ..x1n]
     [1 x21 x22 ..x2n],
     ...]
w = [w0 w1 w2 ... wn]
```
```python
# Example of linear regression vectorized
x1 = [1, 148, 24, 1385]
x2 = [1, 18, 25, 2031]
x3 = [1, 14, 11, 86]
X = [x1, x2, x3]
X = np.array(X)
X.dot(w) # this is our prediction for each element with linear regression
```
The basic problem of linear regression is to solve this equation: Xw = y (as an aproximation); an easy approach would be to use the inverse of X but
it's not square matrix because number of rows are great than columns. Another approach is using **Gram matrix X.T\*X**, which has an inverse because it's (n+1)\*(n+1).
It's important to remember that solution doesn't exist, we just get an approximation for x = (XT\*X)-1\*X.T\*y. 
```python
# After declare our X
X = [
     [148, 24, 1385],
     [18, 25, 2031],
     [14, 11, 86].. #and so on
]
ones = np.ones(X.shape(0)) #same number of rows for ones
X = np.column_stack([ones, X]).round()
# we declare our y
y = [ y1, y2, ...]
XTX = X.T.dot(X)
XTX_inv = np.linalg.inv(XTX)
w_full = XTX_inv.dot(X.T).dot(y) #This is our output, thus we can use it as a function

def train_linear_regression(X, y):
    ones = np.ones(X.shape(0))
    X = np.column_stack([ones, X]).round()
    
    XTX = X.T.dot(X)
    XTX_inv = np.linalg.inv(XTX)
    w_full = XTX_inv.dot(X.T).dot(y)
    return w_full[0], w_full[1:] #return solution as a tupple
```
- Evaluate model with RMSE (root-mean-square error)
After we've train our model with the equation before, we need to calculate how well our model predicts values. Thus, we calculate the sum of square differences between
predictions and real values. Then, we get the mean of that sum and, finally, we get the square root.
![image](https://user-images.githubusercontent.com/74158005/133707125-2e05fd0e-4a96-481e-a571-70718c5a6431.png)
```python
def rmse(y, y_pred):
    se = (y - y_pred)**2
    mse = se.mean()
    return np.sqrt(mse)
```
To get a real measurement of the usefulness of our model, we need to use validation and test data.

- Feature engineering
We can improve our model by using year of the car, then we can get the age which is very useful when price is predicted. Thus, we modify
the prepare_x function to make a copy of our data, get age data and add it to our dataset, fill NaN values and return it as numpy array.
```python
def prepare_X(df): #This function is build to make it readable
    df = df.copy() # we make a copy to make functional programming
    df['age'] = 2017 - df.year #we define a new column inside our dataframe
    features = base + ['age']
    df_num = df[features]
    df_num = df_num.fillna(0)
    X = df_num.values
    return X
# We train our model with this new data and get predicted values of our validation dataset. Finally, we get rmse and plot distribution of outputs    
X_train = prepare_X(df_train)
w0, w = train_linear_regression(X_train, y_train) #training our model again

X_val = prepare_X(df_train)
y_pred = w0 + X_val.dot(w)
print(rmse(y_val, y_pred))
sns.histplot(y_pred, color = 'red', alpha=0.5, bins=50)
sns.histplot(y_val, color = 'blue', alpha=0.5, bins=50)
```

- Regularization (solve some paast problems with numerical values)

