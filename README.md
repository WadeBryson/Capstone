# The K Zone: A Machine Learning Approach to Predicting Pitcher Strikeouts

## Project Overview
The goal of this project is to utilize Machine Learning to predict the season long strikoue total for a Major League Baseball pitcher using basic and advanced statistics from the Baseball Savant website. 

## Motivation and Background
The idea for this project originated when I was trying to utilize Machine Learning to give myself an advantage when creating season long projections for my Yahoo Fantasy Baseball League. Originally I tried to predict a pitcher's Yahoo Fantasy Baseball Points but I had very little success. I decided to take an indepentent look at each variable that is used to calcuate their final fantasy score. Strikeouts are a key part of the Yahoo Fantasy Baseball Pitcher Points equation.

## Creation of Dataset
**Data** - All data used was downloaded from the Baseball Savant Website (https://baseballsavant.mlb.com/). See Raw_Data.csv.  
Creating of CSV with Target Variables - In order to use last season's data to predict the current season's target feature I had to do a lot of manipulation and combining of data records.  
**Step 1** - I began by only downloading a pitcher's data if they pitched the minimum innings required to qualify for the ERA title in 2023 and 2022.  
**Step 2** - I kept all the features for their prior season (2022) and then added their 2023 target features (strikeouts) to their record.  
**Step 3** - I repeated this process for 2015-2016, 2016-2017, 2017-2018, and 2021-2022.  
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

## Machine Learning Methodology

## Results and Key Findings

## Conclusion and Future Work

## Project Requirements

## File Descriptions
Raw_Data.csv - Raw Pitching Data from 2015 - 2023 (No data for 2020 due to shortened COVID season)
Clean_2015_Pitching_Data - Pitcing Data containing prior year stats and new year taret features
Exploratory Data Analysis.ipynb - Imports and Cleans Data. Uses correlation analysis to select wanted features.


