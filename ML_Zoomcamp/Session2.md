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
- Understand linear regression logic
- Evaluate model with RMSE (root-mean-square error)
- Feature engineering
- Regularization (solve some paast problems with numerical values)

