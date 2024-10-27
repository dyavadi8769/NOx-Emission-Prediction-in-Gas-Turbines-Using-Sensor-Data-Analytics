# NOx-Emission-Prediction-in-Gas-Turbines-Using-Sensor-Data-Analytics
## Dataset Overview
The dataset captures operational and environmental parameters from a gas turbine located in Turkey's northwestern region. The primary purpose of this dataset is to study and predict Nitrogen Oxides (NOx) emissions, a harmful byproduct of the combustion process in gas turbines. NOx emissions are a major environmental concern due to their contribution to air pollution and smog formation, making the prediction of these emissions critical for compliance with environmental regulations.

## Source
The dataset is taken from the UCI repository.The dataset is sourced from a gas turbine located in Turkey's northwestern region and includes 7158 instances. Each instance capturing various turbine parameters and ambient conditions. The data includes sensor measurements and operational variables, which can be used to predict NOx emissions.

## Features:
1. Ambient Temperature (AT) [°C]: Temperature of the surrounding environment.
2. Ambient Pressure (AP) [mbar]: Atmospheric pressure around the turbine. 
3. Ambient Humidity (AH) [%]: Moisture content in the air.
4. Air Filter Difference Pressure (AFDP) [mbar]: Pressure difference across the turbine's air filters, indicating efficiency in air intake.
5. Gas Turbine Exhaust Pressure (GTEP) [mbar]: Exhaust pressure, affecting the flow of gases and the efficiency of combustion.
6. Turbine Inlet Temperature (TIT) [°C]: Temperature of the air-fuel mixture entering the turbine.
7. Turbine Energy Yield (TEY) [MWh]: Energy output of the turbine, related to fuel consumption and combustion efficiency.
8. Turbine After Temperature (TAT) [°C]: Temperature of the exhaust gases after passing through the turbine.
9. Compressor Discharge Pressure (CDP) [mbar]: The pressure after air is compressed in the turbine.
10. Carbon Monoxide (CO) [mg/m³]: Indicates the level of incomplete combustion. The concentration of CO in the exhaust gases.
    
## Target:
1. Nitrogen Oxides (NOx) [mg/m³]: The target variable, representing the concentration of NOx emissions, which are a key concern for environmental regulations.

## Challenges / Limitations:
1. Nonlinear Relationships: The relationships between the features and NOx emissions are complex and nonlinear, making modeling challenging.
2. Feature Correlation: Some features, such as turbine inlet and after temperatures, may be highly correlated, leading to multicollinearity, which can distort model predictions.
3. Sensor Data Quality: The dataset may contain noise or inaccuracies due to sensor degradation or external factors, affecting the reliability of predictions.
4. Environmental Sensitivity: NOx emissions are highly sensitive to changes in ambient conditions (temperature, pressure, humidity), introducing variability in the data.
5. Outliers in Sensor Data: Outliers in sensor readings due to miscalibration or extreme conditions.
6. Changing Operating Conditions: Turbine efficiency changes over time due to wear, tear, or maintenance.
7. Imbalanced Data Distribution: NOx emissions may be imbalanced, with more instances of low emissions and fewer of high emissions.

## Detailed Description of Regression Task
## Task Overview:
The goal of this predictive regression task is to predict the Nitrogen Oxides (NOx) emissions from a gas turbine based on various environmental and operational sensor data. NOx emissions are a critical environmental concern as they contribute to air pollution and must be monitored and regulated in many industries, including power generation.

## Target Variable:
NOx Emissions [mg/m³]: The concentration of Nitrogen Oxides (NOx) in the exhaust gases of the gas turbine. NOx emissions result from high-temperature combustion, and their reduction is vital for meeting environmental standards.

## Rationale:
1. Why NOx?:  NOx emissions are strictly regulated by environmental agencies due to their harmful effects on human health and the environment. Predicting NOx emissions in advance allows operators to make adjustments to turbine operations and reduce emissions before they reach harmful levels.
2. Relevance: Power plants are under increasing pressure to reduce NOx emissions as part of global efforts to combat air pollution. Developing a model that can accurately predict NOx emissions enables proactive management and optimization of combustion processes, ultimately contributing to better compliance with emission standards.
3. Interest: This problem is not only relevant from an environmental standpoint but also technologically interesting, as it involves complex interactions between variables like temperature, pressure, humidity, and combustion efficiency.

## Relevant Features:
1. Ambient Temperature (AT) [°C]: Affects combustion temperature and NOx formation.

2. Ambient Pressure (AP) [mbar]: Impacts air density and combustion efficiency.

3. Ambient Humidity (AH) [%]: Influences combustion temperatures and NOx emissions.

4. Air Filter Difference Pressure (AFDP) [mbar]: Reflects air intake efficiency.

5. Gas Turbine Exhaust Pressure (GTEP) [mbar]: Influences exhaust gas flow and combustion efficiency.

6. Turbine Inlet Temperature (TIT) [°C]: Affects combustion temperature, directly related to NOx emissions.

7. Turbine After Temperature (TAT) [°C]: Indicates combustion efficiency and exhaust gas conditions.

8. Turbine Energy Yield (TEY) [MWh]: Represents the energy output of the turbine, indirectly affecting emissions.

9. Compressor Discharge Pressure (CDP) [mbar]: Affects air compression efficiency and combustion. 

10. Carbon Monoxide (CO) [mg/m³]: An indicator of combustion efficiency and quality, influencing NOx emissions.

## Challenges:
1. Multicollinearity: Features like temperatures and pressures could be highly correlated with each other. Multicollinearity can distort the regression coefficients, making it difficult to interpret which variables are truly impacting the target variable.
2. Feature Selection: With many features, some may not contribute significantly to the prediction of NOx emissions. Deciding which features to include or exclude is challenging and could affect model accuracy and interpretability.
3. Overfitting: In regression tasks, overfitting can occur when the model is too complex or includes too many features. This leads to the model fitting the noise in the training data rather than the underlying pattern, causing poor performance on unseen data.
4. Outliers and Noise: Sensor data can often have outliers or noise that may skew the regression model. These abnormal values can disproportionately affect predictions and reduce model robustness.
5. Feature Scaling: Features such as ambient temperature (AT) and compressor discharge pressure (CDP) might have vastly different scales. Without appropriate scaling, the regression model could give more weight to variables with larger numerical ranges, leading to biased predictions.
6. Heteroscedasticity: In regression tasks, heteroscedasticity (i.e., non-constant variance of residuals) can be a problem. If the variance of the errors increases with the size of the predicted value, it can violate regression assumptions and affect the model’s ability to generalize.
7. Model Generalization: Ensuring that the regression model generalizes well to new, unseen data is always a challenge. If the model fits the training data too closely, it may fail to make accurate predictions in different environmental or operational conditions.

## Summary of findings

1. Most Impactful Step: Feature Scaling was the single most important step in the pre-processing sequence, boosting the model’s R² score from 0.266347 to 0.855444. This highlights the importance of ensuring features are on the same scale, especially for SVR models that rely on distance-based optimization.

2. Feature Engineering: In this case, feature engineering led to a decrease in model performance, indicating that the engineered features might have introduced noise or were not helpful in predicting the target variable. Careful feature engineering is crucial to avoid overfitting or degrading performance.

3. Dimensionality Reduction (PCA): While PCA reduced the dimensionality of the dataset, it caused a slight performance decrease from 0.855444 to 0.845503. This suggests that PCA removed some of the variance that was contributing to predictive performance. If dimensionality reduction is required for computational reasons, the slight loss in performance might be acceptable.

4. Feature Selection: Feature selection after PCA did not result in further improvement, confirming that earlier steps like scaling and PCA had already optimized the feature set.

## Conclusion:
The best pre-processing sequence for this SVR model is:

- Outlier Removal
- Correlated Feature Removal
- Feature Engineering
- Scaling
  
This sequence resulted in the highest R² score of 0.814374. Additional steps like PCA and feature selection did not yield significant improvements and may be omitted unless necessary for reducing dimensionality or computational load.
