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
