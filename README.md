# 18-763 Fall 2024 Group Project Option 1
#### Team Members:
Kristy He(xiaokeh@andrew.cmu.edu), Rong Mu(rongmu@andrew.cmu.edu)
## Task 1: Build and Populate Necessary Tables
### 📊 Metadata of Dataset: 
Data from https://www.kaggle.com/stefanoleone992/fifa-22-complete-player-dataset/
| Feature  | Description |
|:------|-----:|
| sofifa_id |  a unique identifier for players in the **Sofifa** database (*Integer*)  |
| player_url   |  web link of player (*Text*) |
| short_name |  player initials (*Text*)|
| long_name |  player's full name (*Text*)|
| player_positions  |  position of player (*Text*)|
| overall | a composite rating of player (*Integer*)  |
| potential | a rating that indicates a player's future growth (*Integer*)|
| value_eur | the estimated market value of a player in euros (*double precision*)|
| wage_eur | the salary of player in euros (*double precision*)|
| age | age of player (*Integer*)|
| dob | birthday of player (*Date*) |
| height_cm | height of player in cetimeter (*Integer*)| 


### 🧐 Discssion: *Why is PostgreSQL DB table better compared to a NoSQL Database?*
**Schema Enforcement**  
PostgreSQL enforces a defined schema that enhances data integrity by specifying the structure of the data, including data types and constraints. Even in cases where certain columns may be missing in files like `female_players_20.csv`, this schema framework effectively prevents the entry of invalid data and ensures consistency across records. This mechanism effectively prevents the entry of invalid data (For example, input of `String` value into `IntegerType` column is invalid) and ensures consistency across records.  
  
**Complex SQL Queries**  
Structured data enables the execution of complex `SQL` queries like `JOIN` facilitating sophisticated data analysis and retrieval. Such operations may be cumbersome or less efficient in NoSQL databases, which are typically optimized for simpler queries and less rigid data structures.


## Task 3: Machine Learning Modeling
### Choice of Classifiers/Regressors
**Linear Regression**

FIFA players dataset is a comprehensive dataset that contains ratings and scores of different aspects of players' characteristics. We choose to use linear regression as a baseline model to capture the linear relationship between individual features and the overall score of each player. Due to the high dimensionality of the datasets, we use elastic net regularization that combines L1 and L2 penalty to prevent overfitting. 

We choose to tune the following parameters in our Spark ML version: regularization parameter ([0.01, 0.1, 0.5, 1.0]), number of epochs ([5, 10, 15, 20, 25]), and elastic net parameter ([0, 0.2, 0.4, 0.6, 0.8, 1]). By tuning the elastic net parameter, we find the best value is 0, meaning that simply applying L2 penalty to the loss function leads to lowest validation RMSE loss. We find the best value of the number of epochs is 5, and the best value of the regularization parameter is 0.01. Both of them are the smallest value in the selections, in the best direction to prevent overfitting.

**Random Forest**

Random forest is an ensembled method that reduces correlation between trees by randomly selecting a subset of features to split on. It has advantages of capturing high-dimensional features and non-linear relationship between features. FIFA dataset has over 100 features, among which some of the players' football characteristics are correlated with others. Using random forest model can handle this complexity well.

**Multilayer Perceptron(MLP)**
