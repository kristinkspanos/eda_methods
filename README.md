# Exploratory Data Analysis for Machine Learning
## project goals
*This project is a work in progress.*

Exploratory data analysis (EDA) methods to perform before performing data analysis, or fitting a regression or classifier model. Exact methods used will vary based on the project goals.

### Preview the dataset
```df.head()```

```df.info()```

```df.describe()```
### Remove duplicates
```df.drop_duplicates()```

### Explore data types
  * ```df.dtypes```
  * Ensure all variables have the appropriate data type; change data types if necessary
  * Variables that should be floats or ints may be stored as objects because missing values could be stored as a str (i.e. 'x', '-', 'unknown'). In this case, replace the str values with 'NaN'.
### Inspect missing data
  * Missing data could be represented with 'Nan', or with another str value (i.e. 'x', '-', 'unknown'). 
  * Depending on the analysis beinf performed, missing values can:
    * remain as-is
    * be removed
    * be replaced with an imputed value
    * be replaced with a missing data type that Python can recognize, such as NaN
  * It's also possible that 0 values are intended to be missing values. This can be inspected by looking at the range of a variable or visualizing the distribution of a variable through a boxplot or other distribution chart. If a variable has zero values that don't make intuitive sense, it's possible that the zeros represent missing values.
### Categorize and/or bin data
  * Inspect categorical variables to determine distribution among categories and trends in the data (using ```
df.value_counts()``` or visualization tools such as boxplots
  * Categorical features with many levels are “expensive” to include in a regression model. Consider:
    * deleting records of data with only a few observations
    * cobining categories with bew observations into larger categories of related variables
  * Records can be categorized/coded differently depending on the trends in the analysis. For example, the variable "day of month" could be coded as:
    * ordinal, if the value rises approximately linearly throughout the month
    * nominal, if the value rises and falls throughout the month
    * categorized into day of the week groups, if the data follows trends such as rising on weekends and falling on weekdays
  * Methods for grouping and ordering categorical variables include:
    * ```pd.Categorical()``` - stores data as type category and stores the order of the categories; useful for ordinal categorical varaibles
    * ```df['column'].cat.codes``` - converts each category in a variable to an integer; allows numerical operations to be performed on the columns
    * ```pd.get_dummies()``` - creates a new binary variable for each category within the original variable
      * useful in cases where it doesn't make sense to assign numbers to variables and therefore create the appearance of an order between the variables, or in cases where we don't want to assume equal spacing between categories
      * be careful using this method with a large number of categories, as a new variable will be created for each category
* Combining categories
  * Categories that are similar can be combined to show a larger, more general category.
  * Categories with few observations can be combined and shown as 'other'
* Binning numeric data
  * Binning is categorizing numeric data based on a range of data.  
### Scaling and normalization
  * It is difficult to compare variables with vastly different scales, or create models using these variables. Variables can be re-scaled or noramlized so that each feature can be compared.
  * Scaling and normalization methods
    * Data centering
      * Distance from mean: Subtract the mean of the variable from each data point so that the new mean is zero. This tells us how far above or below the mean each data point is.
      * Percent distance from mean: Divide each data point by the mean of the variable so that the new mean is one. This tells us each data point's percent distance from the mean (i.e. a centered value of 1.07 is 7% above the mean).
    * min-max normalization
      * Minimum is transformed to zero, max is transformed to 1, all other values are transformed to a decimal between 0 and 1.
      * All features will have the same scale, but outliers will continue to skew the data
    * z-score normalization
      * If a value is exactly equal to the mean of all the values of the feature, it will be normalized to 0. If it is below the mean, it will be a negative number, and if it is above the mean it will be a positive number. 
      * Handles outliers, but does not produce normalized data with the exact same scale. 
### Outliers
  * inspect data for outliers using visualization tools such as scatterplots or boxplots
### Distributions and associations
  * inspect distribution of quantitative variables using histogram, boxpot, or other distribution plot
    * log transformation
      * transforming highly skewed data can produce better results in machine learning models  
  * inspect association between variables using scatterplots, pairplots, and/or correlation matrices                       

## resources
This project is inspired by the [Codecademy](https://www.codecademy.com/learn) articles:
* EDA Prior to Fitting a Regression Model
* EDA Prior to Fitting a Classification Model
* Normalization
* Intro to Variable Types
* Data Centering and Scaling
* Discretizing Numerical Data and Collapsing Categories
* Advanced Data Transformations

Other Resources:
* [A One-Stop Shop for Principal Component Analysis](https://towardsdatascience.com/a-one-stop-shop-for-principal-component-analysis-5582fb7e0a9c)
* [Transformations: and introduction](http://fmwww.bc.edu/repec/bocode/t/transint.html)

## built with
* Python 3
* Jupyter Notebook

## data sources
[2016 MLB Season (Kaggle)](https://www.kaggle.com/cyaris/2016-mlb-season)

*Note: a subset of the full dataset is used for this analysis*

Field | Description
------------ | -------------
game_type | is the game during the day or at night
day_of_week | what day of the week did the game occur
temperature | average game temperature (Fahrenheit)
sky | description of sky condition at the time of the game
total_runs | total runs scored in the game
attendance | total game attendence
## acknowledgements
* [Codecademy Data Scientist Skill Path](https://www.codecademy.com/learn)
* [Kaggle](https://www.kaggle.com/cyaris/2016-mlb-season)
