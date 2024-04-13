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
### **Initial Model** Using Strikeouts to Predict New Strikeouts
<img width = "341" height = "250" src="Strikeout Model.png">  

Model Performance  
| Feature   | Training   | Test    |  
| -----     | -----      | -----   |  
| strikeout | 0.38 | 0.25 |  

### **Model 1** - Single Feature Model with EDA Features  
<img width = "335" height = "250" src="k_percent Model.png">  

Model Performance
| Feature   | Training   | Test    |
| -----     | -----      | -----   |
| k_percent | 0.42 | 0.36 |
| whiff_percent | 0.30 | 0.32 |
| p_swinging_strike | 0.31 | 0.25 |
| xba | 0.30 | 0.27 |
| z_swing_miss_percent | 0.27 | 0.29 |
| iz_contact_percent | 0.27 | 0.29 |
| in_zone_swing_miss | 0.30 | 0.23 |
### **Model 2** - Multi Feature Model with EDA Features  
<img width = "454" height = "230" src="Multi-Feature Regression Model.png">  

Model Performance
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
### **Model 3** - Decision Tree Model with Full Features
<img width = "463" height = "327" src="Decision Tree Full Model.png">  

Model Performance
| Depth | MSE   | R2    |
| ----- | ----- | ----- |
| 5     | 2632 | -.07?? |
| 4     | 1946 | .20 |
| 3     | 2138 | .13 |
| 2     | 1591 | .35 |
| 1     | 1783 | .27 |
### **Model 4** - Decision Tree Model with EDA Features  
<img width = "454" height = "318" src="Decision Tree EDA Model.png">  

Model Performance
| Depth | MSE   | R2    |
| ----- | ----- | ----- |
| 5     | 1750 | .28 |
| 4     | 1645 | .33 |
| 3     | 1365 | .44 |
| 2     | 1591 | .35 |
| 1     | 1783 | .27 |

### **Model 5** - LASSO Model with Full Features
<img width = "477" height = "297" src="LASSO Full Model.png">  

Model Performance
| Alpha | MSE   | R2    |
| ----- | ----- | ----- |
| .001  | 1398 | .4281 |
| .01   | 1401 | .4217 |
| .1    | 1372 | .4388 |
| 1     | 1354 | .4462 |
| 10    | 1255 | .4865 |
| 11    | 1254 | .4871 |
| 100   | 1293 | .4713 |

### **Model 6** - LASSO Model with EDA Features
<img width = "461" height = "310" src="LASSO EDA Model.png">  

Model Performance
| Alpha | MSE   | R2    |
| ----- | ----- | ----- |
| .001  | 1312 | .4633 |
| .01   | 1314 | .4625 |
| .1    | 1315 | .4621 |
| 1     | 1328 | .4568 |
| 10    | 1362 | .4432 |
| 100   | 1556 | .3635 |

## Compiled Model Performances
The LASSO Model with Full Features performed the best of all of the models. It had an r2 value of 0.49 which almost doubles the accuracy of the baseline model r2 of 0.26.  
<img width = "404" height = "243" src="Final Results Table.png">  


## Key Findings  
**Baseline Model** - I started with an r2 value of 0.26 on the test data using the feature strikeout to predict new_strikeout. This is really poor and I was confident that I could improve upon this.  
**Single Feature Model** - I tried a few different features and found out that the best single feature model was using k_percent (r2 of 0.36). This is the first time that k_percent really started to stand out and it's a common theme throughout the next few models.  
**Multi-Feature Model** - I did not improve my model by adding more features. I did notice that models that included k_percent were consistently better than models that did not include it.  
**Decision Tree Model** - The Decision Tree Model with Full Features was really disappointing. I did not expect those models to be that bad. When I switched to the EDA Features Data the Decision Tree Models improved significantly. The best model was a big improvement from the basic regression models. The Decision Tree Model with a depth of 3 had an r2 value of 0.44. The features and their importance for that model are listed below. Notice that once again k_percent seems to be the most important feature.  
<img width = "561" height = "250" src="Decision Tree EDA Features.png">  

**LASSO EDA Model** - This model was once again an improvement and was my 2nd best overall model with an r2 value of 0.46. This is where things started to get messy and its not surprising because an r2 value of 0.46 is pretty bad.  
<img width = "590" height = "286" src="LASSO EDA Features.png"> 

Because each feature is drastically different, I have also included a table below with the coefficient for each feature, the mean for each feature, and then a product of the two values so you can see a snapshot of the average impact of each feature on the data.

| Feature | Coefficient | Mean | Product |
| ------- | ----------- | ---- | ------- |
| iz_contact_percent | 2.1803 | 82.53 | 179.9 |
| k_percent | 3.8944 | 22.74 | 88.6 |
| whiff_percent | 2.6788 | 24.15 | 64.7 |
| in_zone_swing_miss | 0.4309 | 149.84 | 64.6 |
| p_swinging_strike | -0.2369 | 268.04 | -63.5 |
| strikeout | 0.2768 | 160.2 | 44.3 |
| xba | -43.4735 | 0.24 | -10.4 |

At face value it looks like k_percent is once again pretty important but the real puzzling thing here is the iz_contact_percent. It has not been a feature that has been very important until this model. I found it interesting that the bias is -177.54. This was very similar to the iz_contact_percent value so I tried cutting iz_contact_percent out and creating a new LASSO model but it performed slightly worse with an r2 value of 0.44.  

**LASSO Full Features Model** - This model was the best model that I created with an r2 value of 0.49.   
<img width = "333" height = "416" src="LASSO Full Features.png">  

Once again the features and their coefficients can be a little misleading so I created a table below with the coefficient for each feature, the mean for each feature, and then a product of the two values so you can see a snapshot of the average impact of each feature on the data.  

| Feature | Coefficient | Mean | Product |
| ------- | ----------- | ---- | ------- |
| p_total_strike | -0.1111 | 1757.68 | -195.1 | 
| strikeout | 0.9183 | 160.2 | 147.1 |
| fastball_avg_spin | 0.0652 | 2222.82 | 144.9 |
| total_pitches | 0.04 | 2711.33 | 108.5 |
| p_total_ball | -0.1030 | 962.42 | -99.1 |
| p_ball | 0.1061 | 894.9 | 95.0 |
| pa | -0.1203 | 703.45 | -84.63 |
| in_zone | 0.0499 | 1330.5 | 66.4 |
| out_zone | -0.0254 | 1385.15 | -35.2 |
| p_lob | 0.2969 | 116.67 | 34.6 |
| player_age | -0.8347 | 28.56 | -23.8 |
| p_total_bases | -0.0764 | 253.88 | -19.4 |
| out_zone_swing | 0.0468 | 405.3 | 19.0 |
| offspeed_avg_spin | -0.0096 | 1723.9 | -16.5 |
| last_year_Yahoo | -0.0483 | 328.28 | -15.9 |
| p_total_swinging_strike | 0.0122 | 760.99 | 9.3 |
| double | 0.2483 | 30.81 | 7.7 |
| pitch_count_fastball | 0.0047 | 1621.4 | 7.6 |
| p_swinging_strikes | -0.0256 | 268.04 | -6.9 |
| p_called_strike | -0.0096 | 464.1 | -4.5 |
| pitch_count_breaking | 0.0056 | 693.5 | 3.9 |
| breaking_avg_spin | 0.0013 | 2384.4 | 3.1 |
| edge | 0.0014 | 1174 | 1.6 |
| ab | -0.0013 | 639.4 | -0.8 |
| pitch_count_offspeed | 0.0002 | 366.2 | 0.1 | 



## Future Work

## Project Requirements


## File Descriptions
**Raw_Data.csv** - Raw Pitching Data from 2015 - 2023 (No data for 2020 due to shortened COVID season).    
**Clean_2015_Pitching_Data.csv** - Pitcing Data containing prior year stats and new year taret features.  
**Exploratory Data Analysis.ipynb** - Jupyter Notebook that imports and cleans the data and then uses correlation analysis to select and analyze wanted features. 
**Simple Regression Models.ipynb** - Jupyter Notebook that builds and analyzes Model 1 - Single Feature and Model 2 - Multi Feature.  
**LASSO and Decision Tree Models.ipynb** - Jupyter Notebook that builds and analyzes Model 3 - Decision Tree with Full Features, Model 4 - Decision Tree with EDA Features, Model 5 - LASSO with Full Features, and Model 6 - LASSO with EDA Features.  
**Final Results.ipynb** - Jupyter Notebook that displays the best iteration of each of the six models.  

## How to Manage Virtual Environment
**Step 1** - In VS Code open the Command Palette.  
**Step 2** - Type "Python:Create Environment" and then select that command.  
**Step 3** - Select Venv to create a Venv environment.  
**Step 4** - Activate your environment by typing ".venv\Scripts\Activate" in the terminal.  



