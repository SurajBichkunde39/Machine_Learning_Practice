## Diabetes dataset Analysis
* The dataset is available on [link](https://www4.stat.ncsu.edu/~boos/var.select/diabetes.tab.txt)
* This is also one of the toy datasets present in scikit-learn [here](https://scikit-learn.org/stable/datasets/toy_dataset.html#diabetes-dataset)

### DataSet information
|||
| ---------------------:|:----|
| Number of data points | 442 |
| Number of features    | 10  |
| Target                | Quantitative measure of disease progression one year after baseline| 
|Attribute Information  |AGE : in years<br>sex<br>BMI : body mass index<br>BP : average blood pressure<br>S1 : tc, T-Cells (a type of white blood cells)<br>S2 : ldl, low-density lipoproteins<br>S3 : hdl, high-density lipoproteins<br>S4 : tch, thyroid stimulating hormone<br>S5 : ltg, lamotrigine<br>S6 : glu, blood sugar level|


## Feature Engingeering and Insights
* SEX columns is given with the info 1 & 2, Not sure what is representing male and female. Giving this feature as int value could misslead the model.
* Converted the SEX feature into categorical feature and passed in the model with one hot encoding.
* Tried the model with all data in given scale, and with the Standardscale mean = 0 and standard deviation = 1
* In terms of sex (only categorical feature) is balanced over dataset.
* Feature S1 and S2 are highly correllated with each other, but dropping one of them also did not impact the performance.
* All the features (except S4) are approximatly normally distributed.
* As we are predicting quantitative measure of disease progression in one year, so mean squared error will be a good metric to measure the performance.

## Model Proformances
### Linear Models
#### Data In Given Scale
| Model | Hyperparameter | Testing Score |
|:-------|---------------:|--------------:|
|LinearRegression||2686.9614998088423|
|Ridge ( l2-regularization ) | alpha = 1 | 2683.460776694342|
|Support Vector Machine | C = 100 |  3511.170879778455 |
|Support Vector Machine | C = 5000 |  2597.1265991073433 |
|Support Vector Machine | C = 100<br> kernel='linear' |  2597.1265991073433 |
<br><br>

#### Data in Standard Scale
| Model | Hyperparameter | Testing Score |
|:-------|---------------:|--------------:|
|LinearRegression||3138.069488901397|
|Ridge ( l2-regularization ) | alpha = 10 | 3125.2949736585156|
|Support Vector Machine | C = 10 |  3218.9508136077884 |

<br><br>
### Non-Linear Models
| Model | Hyperparameter | Testing Score |
|:-------|---------------:|--------------:|
|Decision Tree | Max_depth = 3 | 4119.321566362705 |
|Random Forest | max_depth = 3 <br> n_estimators = 300|3317.3921070803444 |


