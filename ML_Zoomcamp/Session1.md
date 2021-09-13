### Machine Learning vs Ruled-based Systems
Email example: there are some spam complains (we want a system that classifies massages as spam or not): First approach (find patterns like a particular email,
some words in title: if, else if, else is, else.. *never end process* that consist of software solution difficult to maintain). Thus, we can use machine learning
with the following  general steps: get data, define/calculate features, train and use model. Example: first we use the spam folder as spam data (true spam) and
some email that are not, second see features (lenght, sender domain, contain a word, etc).
Thus, these features are encoded into some values (1 or 0 if a rule is completed : e.g. length greater than 10) and we also know that this is spam (our target). This is made for
all the dataset we have (all data samples). Then, we train/fit the model which then can predict our target with features we have. 

**Supervised ML** e.g. regression, classification, ranking

In the first class, we show what the price should be to the model (*we are supervising* by giving examples). Because ML is based on computer science, it has math
and statistics abstraction (representation). Our **X_matrix** is two dimensional (2-D) array of our features, **y** is a vector with the desired output in a column with
a value for each matrix (1-D). **g(X_matrix) = y_predicted** but usually the predictions are probabilities of a row. **Regression** we find a number which represent price
(up to infinity), age (in a range), number of something, etc; **Classification** for 2 categories (binary classification)
while for more than 2 is multiclass classification. Finally, ranking are recommender system (there are many interesting and get the top 5 for this used, relevant movies,
products, product search, search engine)

### CRISP-DM ML Process (methodology): From problem to deployment
We organize the tasks in a methodoly that formalize the work. The  6 steps are as follows:
- Business Understanding: identify problem to solve, need ML, goals and measures/metrics for succesful projects
- Data Understanding : analyze data source, metadata, data governance, realiability, see if enough data
- Data Preparation: transform data so we can put into ML algorithm (extract features), build pipeling, clean data (all I've seen before), convert to tabular form
- Modeling: train the model, try different modules (NN, logistic regression, decision tree), add features, etc
- Evaluation: see if goal was reached or metrics were improved; thus, we decide if need to adjust goal, show model to users or stop working on project
- Deployment: online evaluation, deploy and evaluate a part of users (5% as option), do monitoring and ensure quality/maintainability

![image](https://user-images.githubusercontent.com/74158005/133008924-1039b459-8ee8-435b-9532-ed4c143b08d9.png)

### Modeling step
Usually we try different models to select the best for our task. Because if we want to see if really is working, we will need to see the future (just a phrase)
or we can extract a part of our data (train and validation). So we train with train_X and train_y while we validate the model with val_X and val_, get a
prediction percentage and select the better. But there are some problems: what if a model is lucky to predict the same validation set we've chosen.
![Problem when compare](https://user-images.githubusercontent.com/74158005/133010153-6b447cf2-607a-403d-86c5-bb72b3bd1136.png)
A solution is to divide the data into three groups: 20% for validation, 20% for testing and 60% for training. Then we've got 3 sets of data and put the
testing data away. Then we train and make validation, compare and choose the best. Then, we see how the best model works with testing and see how accurate has been.
Then, we can repeat (if overall accuracy is not enough) without know about the testing. If we've chosen the best model, we can train again with the
data from validation and training together, thus we can test with a model which is trained with more data.

Then we set the environment and see a little review about Numpy, Statistics and Pandas.

Numpy is well known because its numpy array whose characteristic is the element wise operations as well as the comparison that return an array. Some functions are:
```python
np.zeros(2): [0, 0] (column) or np.zeros((2,3)): [ [0, 0, 0], [0, 0, 0]] (rows, column)
np.ones(2): [1, 1] (column) or np.ones((2,3)): [ [1, 1, 1], [1, 1, 1]] (rows, column)
np.full(3, 2.5) : [2.5, 2.5, 2.5]
np.linspace(0, 100, 11): [0, 10, 20..., 100] #it makes an array with n equal separation (first, last, number of items)
np.arange(5,10) : [5, 6, 7, 8, 9]
# multidimension array acces a[0,2] or a[row, column]
# we can replace rows : n[2] = [1, 1, 1] or replace columns: n[:, 2] = [0, 1, 2]
```
```python
# RANDOM GENERATION
np.random.seed(2) #seed to get same random each running
100 * np.random.rand(5, 2) #it give us a positive distribution of 5 rows and 2 cols
np.random.randn(5, 2) #it give us a positive/negative distribution of 5 rows and 2 cols
np.random.randint(low=0, high=100, size=(5, 2)) #to get integers in a range
```
