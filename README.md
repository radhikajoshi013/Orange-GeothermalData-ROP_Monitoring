# Orange-GeothermalData-ROP_Monitoring
Using Orange Data Miner to analyze Geothermal Data in Utah Forge and monitor Rate of Penetration performance.
Target ROP to determine the efficiency of geothermal drilling and provide insight into future drilling activities for the enhanced geothermal project of Utah FORGE
This is a one foot interval drilling dataset for well 58-32 that covers from 85.18 feet to 7536.25 feet in depth (which is TD). It contains information such as depth, rate of penetration, weight on bit, hookload, temperature in and out, pump pressure, flow in and out, and H2S etc.
7313 instances, 19 features (73% missing data), No target variable, 14 meta attributes (0% missing data)
Feature Selection: From conventional drilling we know that there is a direct relation between WOB, RPM, Torque, Pump Pressure and Depth to ROP. narrowed it down to these features.
The ROP(1 ft) is considered as out target variable.
used the “Preprocess” widget to perform the Z-Score normalization to make sure each feature has the  same scale. This helps to prevent one feature from dominating other during the training process.
used the “Data Sampler” widget to sample the data. We used the 80:20 fixed proportion split for data sampling which divided the data into 746 and 186 entries respectively.
further trained the data using KNN, Linear Regression and Random Forest widgets individually checking which yields the highest R Squared(R2).
assessed the performance using the "Test and Score" widget, employing a 10-fold cross-validation approach with stratification. We checked the model with highest R2, comparably least MAE and less train time.
Tableau was then used for visualizations. predicted values from linear regression tends to deviate more from the values than kNN and random forest, especially in the case of any outliers in the ROP.  kNN and random forest were more accurate, but random forest sometimes predicted values higher than the actual ROP and kNN sometimes underestimated.





