# Orange-GeothermalData-ROP_Monitoring
<img width="717" alt="image" src="https://github.com/user-attachments/assets/8e3b3478-af87-4674-aec4-7bc0512038ea" />

## Problem Statement: 
Using Orange Data Miner to analyze Geothermal Data in Utah Forge and monitor Rate of Penetration performance. Target ROP to determine the efficiency of geothermal drilling and provide insight into future drilling activities for the enhanced geothermal project of Utah FORGE.

## Data Source: 
The U.S. Department of Energy's (U.S. DOE) Frontier Observatory for Research in Geothermal Energy (FORGE). Drilling and log data for well 58-32 (https://gdr.openei.org/submissions/1006)

## Data Description: 
This is a one foot interval drilling dataset for well 58-32 that covers from 85.18 feet to 7536.25 feet in depth (which is TD). It contains information such as depth, rate of penetration (ROP), weight on bit, hookload, temperature in and out, pump pressure, flow in and out, and H2S etc. 7313 instances, 19 features (73% missing data), 14 meta attributes (0% missing data).

## Modelling Process:
Since the target variable (Rate of Penetration) was a continuous numeric variable, three different algorithms were tried to find out the best results: kNN, Random Forests and Linear Regression. 

<li>Feature Selection: From conventional drilling we know that there is a direct relation between WOB, RPM, Torque, Pump Pressure and Depth to ROP. narrowed it down to these features. The ROP(1 ft) is considered as target variable.
  
<img width="250" alt="image" src="https://github.com/user-attachments/assets/ad6793eb-14d5-4a19-bcf8-b59fb5684689"/></li>
<li>Preprocessing: Used the “Preprocess” widget to perform the Z-Score normalization to make sure each feature has the  same scale. This helps to prevent one feature from dominating other during the training process. 

<img width="350" alt="image" src="https://github.com/user-attachments/assets/f1d80df7-4a7a-4509-99b3-2ac2ee6c20ea"/><img width="350" alt="image" src="https://github.com/user-attachments/assets/185d96cb-e851-4b3f-9560-e43e381d85cc"/>

</li>
<li>Train-Test-Split: Used the “Data Sampler” widget to sample the data. 80:20 fixed proportion split was taken for data sampling, which divided the data into 746 and 186 entries respectively.</li>
<li>Model Training: Further trained the data using KNN, Linear Regression and Random Forest widgets individually checking which yields the highest R Squared(R2).
  
<img width="717" alt="image" src="https://github.com/user-attachments/assets/83b0e68b-7ff4-43f3-937b-c2beaebdb11a"/></li>
<li>Model evaluation: Assessed the performance using the "Test and Score" widget, employing a 10-fold cross-validation approach with stratification. All 3 models were cross-checked to find the model with highest R2, comparably least MAE and less train time.
  
<img width="350" alt="image" src="https://github.com/user-attachments/assets/b8bcd6d8-5ab3-4cbe-89df-e2d38be98095"/></li>
<li>Data visualization: Tableau was then used for visualizations.

This image shows the actual ROP values in yellow as compared to the predicted values from kNN, Random forest, and Linear regression. The x axis shows the depth taken as a dimension on a continuous scale for the purpose of modeling ROP as a line chart and comparing the values. Predicted values from linear regression tend to deviate more from the values than kNN and random forest, especially in the case of any outliers in the ROP. kNN and random forest were more accurate, but random forest sometimes predicted values higher than the actual ROP and kNN sometimes underestimated. 
  
<img width="600" alt="image" src="https://github.com/user-attachments/assets/ffb050b0-bd6a-4b07-b607-f45da7ae5380" /></li>
 
This chart displays the error in each of the models with depth along the x axis.The blue line shows the ROP values to give an idea of what the trend looks like. It can be seen that linear regression had the most error in the model.
  <img width="600" alt="image" src="https://github.com/user-attachments/assets/efd9ddb7-884c-43c1-9f29-7ed10e17927e" /></li>

## Model Outputs: 
This residual analysis models knn versus knn error. It indicates that lower depths had more error than higher depths.
<img width="550" alt="image" src="https://github.com/user-attachments/assets/28a29e00-b04a-4c96-ae58-4d3d9bc54908" />

## Limitations/Challenges:
Since there was a lot of missing data (73%), End of Well Reports and Well logs needed to be checked to correlate with missing data. It was found that certain sections of the subsurface had missing data and this information from the reports was used to filter out records from that sub-surface strata in the pre-processing stage.

## Insights:  

<li> Predictive Analysis: The kNN model for Rate of Penetration in geothermal wells can thus be used to predict ROP based on new input data for the predictor variables, and enhance ROP in future wells.
<li> Cost Optimization: Optimize the k-NN model to identify the best operational parameters, like WOB and RPM, for optimal ROP, lowering drilling costs and boosting project profitability.
<li> Performance Monitoring: Monitor performance by comparing predicted and actual ROP, analyzing discrepancies to refine drilling practices.</li>


