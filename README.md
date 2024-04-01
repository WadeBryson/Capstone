# The K Zone: A Machine Learning Approach to Predicting Pitcher Strikeouts

## Project Overview
The goal of this project is to utilize Machine Learning to predict the season long strikeout total for a Major League Baseball pitcher using basic and advanced statistics from the Baseball Savant website. 

## Motivation and Background
The idea for this project originated when I was trying to utilize Machine Learning to give myself an advantage when creating season long projections for my Yahoo Fantasy Baseball League. Originally I tried to predict a pitcher's Yahoo Fantasy Baseball Points but I had very little success. I decided to take an indepentent look at each variable that is used to calcuate their final fantasy score. Strikeouts are a key part of the Yahoo Fantasy Baseball Pitcher Points equation.

## Creation of Dataset
**Data** - All data used was downloaded from the Baseball Savant Website (https://baseballsavant.mlb.com/). See Raw_Data.csv.  
Creating of CSV with Target Variables - In order to use last season's data to predict the current season's target feature I had to do a lot of manipulation and combining of data records.  
**Step 1** - I began by only downloading a pitcher's data if they pitched the minimum innings required to qualify for the ERA title in 2023 and 2022.  
**Step 2** - I kept all the features for their prior season (2022) and then added their 2023 target features (strikeouts) to their record.  
**Step 3** - I repeated this process for 2015-2016, 2016-2017, 2017-2018, 2018-2019, and 2021-2022.  
See Clean_2015_Pitching_Data.csv  

## Exploratory Data Analysis
**Step 1** - Import the Data  
**Step 2** - Basic Understand of the Data (Head, Tail, Shape)  
**Step 3** - Clean the Data Part 1  
             Remove String Values and Unnecessary Target Features  
**Step 4** - Correlation Analysis  
**Step 5** - Clean the Data Part 2  
             Create new dataframe that only includes features that correlate with my target_feature with a magnitude of 0.5 or higher  
**Step 6** - Basic Descriptive Statistics with new dataframe  
**Step 7** - Correlation Heat Chart with Target Feature  
**Step 8** - Scatter Plots with all remaining Features vs Target Feature  

## Machine Learning Models
#### **Model 1** - Single Feature Model with EDA Features  
Single Feature Regression Model Performance
| Feature   | Training   | Test    |
| -----     | -----      | -----   |
| k_percent | 0.42 | 0.36 |
| strikeout | 0.38 | 0.25 |
| whiff_percent | 0.30 | 0.32 |
| p_swinging_strike | 0.31 | 0.25 |
| xba | 0.30 | 0.27 |
| z_swing_miss_percent | 0.27 | 0.29 |
| iz_contact_percent | 0.27 | 0.29 |
| in_zone_swing_miss | 0.30 | 0.23 |
#### **Model 2** - Multi Feature Model with EDA Features  
Multi-Feature Model Performance
| # Features | Features | Training   | Test    |
| -----     | -----      | -----   | ----- |
| 2 | strikeout, k_percent | 0.45 | 0.35 |
| 2 | k_percent, whiff_percent | 0.42 | 0.35 |
| 2 | k_percent, p_swinging_strike | 0.43 | 0.36 |
| 2 | k_percent, xba | 0.42 | 0.36 |
| 2 | strikeout, whiff_percent | 0.41 | 0.33 |
| 2 | whiff_percent, xba | 0.35 | 0.35 |
| 3 | k_percent, strikeout, xba | 0.45 | 0.35 |
| 4 | k_percent, strikeout, xba, whiff_percent | 0.45 | 0.34 |
| 5 | k_percent, strikeout, xba, whiff_percent, p_swinging_strike | 0.45 | 0.34 |
#### **Model 3** - Decision Tree Model with Full Features
Model 3 - Decision Tree with Full Features Results
| Depth | MSE   | R2    |
| ----- | ----- | ----- |
| 5     | 2632 | -.07?? |
| 4     | 1946 | .20 |
| 3     | 2138 | .13 |
| 2     | 1591 | .35 |
| 1     | 1783 | .27 |
#### **Model 4** - Decision Tree Model with EDA Features
Model 4 Decision Tree with EDA Features Results
| Depth | MSE   | R2    |
| ----- | ----- | ----- |
| 5     | 1750 | .28 |
| 4     | 1645 | .33 |
| 3     | 1365 | .44 |
| 2     | 1591 | .35 |
| 1     | 1783 | .27 |
#### **Model 5** - LASSO Model with Full Features
Model 5 - Lasso Alpha with Full Features Results
| Alpha | MSE   | R2    |
| ----- | ----- | ----- |
| .001  | 1398 | .4281 |
| .01   | 1401 | .4217 |
| .1    | 1372 | .4388 |
| 1     | 1354 | .4462 |
| 10    | 1255 | .4865 |
| 11    | 1254 | .4871 |
| 100   | 1293 | .4713 |
#### **Model 6** - LASSO Model with EDA Features
Model 6 - Lasso Alpha with EDA Features Analysis
| Alpha | MSE   | R2    |
| ----- | ----- | ----- |
| .001  | 1312 | .4633 |
| .01   | 1314 | .4625 |
| .1    | 1315 | .4621 |
| 1     | 1328 | .4568 |
| 10    | 1362 | .4432 |
| 100   | 1556 | .3635 |

## Results and Key Findings

## Conclusion and Future Work

## Project Requirements


## File Descriptions
**Raw_Data.csv** - Raw Pitching Data from 2015 - 2023 (No data for 2020 due to shortened COVID season).    
**Clean_2015_Pitching_Data.csv** - Pitcing Data containing prior year stats and new year taret features.  
**Exploratory Data Analysis.ipynb** - Jupyter Notebook that imports and cleans the data and then uses correlation analysis to select and analyze wanted features.  

## How to Manage Virtual Environment
**Step 1** - In VS Code open the Command Palette.  
**Step 2** - Type "Python:Create Environment" and then select that command.  
**Step 3** - Select Venv to create a Venv environment.  
**Step 4** - Activate your environment by typing ".venv\Scripts\Activate" in the terminal.  



