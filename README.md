# Orange-GeothermalData-ROP_Monitoring
<img width="717" alt="image" src="https://github.com/user-attachments/assets/8e3b3478-af87-4674-aec4-7bc0512038ea" />

Problem Statement: Using Orange Data Miner to analyze Geothermal Data in Utah Forge and monitor Rate of Penetration performance. Target ROP to determine the efficiency of geothermal drilling and provide insight into future drilling activities for the enhanced geothermal project of Utah FORGE.

Data Source: The U.S. Department of Energy's (U.S. DOE) Frontier Observatory for Research in Geothermal Energy (FORGE). Drilling and log data for well 58-32 (https://gdr.openei.org/submissions/1006)

Data Description: This is a one foot interval drilling dataset for well 58-32 that covers from 85.18 feet to 7536.25 feet in depth (which is TD). It contains information such as depth, rate of penetration, weight on bit, hookload, temperature in and out, pump pressure, flow in and out, and H2S etc. 7313 instances, 19 features (73% missing data), No target variable, 14 meta attributes (0% missing data)

Modelling Process:
<li>Feature Selection: From conventional drilling we know that there is a direct relation between WOB, RPM, Torque, Pump Pressure and Depth to ROP. narrowed it down to these features. The ROP(1 ft) is considered as target variable.![image](https://github.com/user-attachments/assets/ad6793eb-14d5-4a19-bcf8-b59fb5684689)
</li>
<il>Preprocessing: Used the “Preprocess” widget to perform the Z-Score normalization to make sure each feature has the  same scale. This helps to prevent one feature from dominating other during the training process. ![image](https://github.com/user-attachments/assets/f1d80df7-4a7a-4509-99b3-2ac2ee6c20ea) ![image](https://github.com/user-attachments/assets/185d96cb-e851-4b3f-9560-e43e381d85cc)
</il>
<li>Train-Test-Split: Used the “Data Sampler” widget to sample the data. 80:20 fixed proportion split was taken for data sampling, which divided the data into 746 and 186 entries respectively.</li>
<li>Model Training: Further trained the data using KNN, Linear Regression and Random Forest widgets individually checking which yields the highest R Squared(R2).![image](https://github.com/user-attachments/assets/83b0e68b-7ff4-43f3-937b-c2beaebdb11a)
</li>
<li>Model evaluation: Assessed the performance using the "Test and Score" widget, employing a 10-fold cross-validation approach with stratification. All 3 models were cross-checked to find the model with highest R2, comparably least MAE and less train time.![image](https://github.com/user-attachments/assets/b8bcd6d8-5ab3-4cbe-89df-e2d38be98095)
</li>
<li>Data visualization: Tableau was then used for visualizations.
<li>![image](https://github.com/user-attachments/assets/ffb050b0-bd6a-4b07-b607-f45da7ae5380)</li>
<li>![image](https://github.com/user-attachments/assets/efd9ddb7-884c-43c1-9f29-7ed10e17927e)</li>
</li>

Model Outputs: 
![image](https://github.com/user-attachments/assets/28a29e00-b04a-4c96-ae58-4d3d9bc54908)

Limitations:

Insights:  Predicted values from linear regression tends to deviate more from the values than kNN and random forest, especially in the case of any outliers in the ROP.  kNN and random forest were more accurate, but random forest sometimes predicted values higher than the actual ROP and kNN sometimes underestimated.
