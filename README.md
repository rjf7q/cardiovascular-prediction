<p align="center">
  <img src="images/cardio.png" alt="Heart Disease Feature Prediction" width="100%">
</p>

This project dives into the critical challenge of heart disease prediction, leveraging machine learning to uncover significant factors and provide predictive insights. By analyzing patient data, we aim to identify meaningful patterns and build models that can assist in early diagnosis and health interventions.

## Table of Content 
- Objectives
- Data Overview
- Data Preparation
- Key Findings
- Machine Learning Approach
- Conclusion and Recommendations
- Summary
- Presentation
- Contributors  

# Objectives
- Identify key predictors for heart disease.
- Develop and evaluate machine learning models for accurate prediction.
- Provide insights to guide lifestyle and policy changes.  

# Data Overview
We worked with datasets sourced from:
- **Kaggle**: CMS Cardiovascular Disease dataset.
- **CDC**: Data on heart disease prevalence and related factors.  

# Data Preparation
**Cleaning and Encoding**:  
- We addressed missing values, standardized numerical data, and converted categorical variables into numerical formats.  

- Features with binary categories (Smoking, AlcoholDrinking, Stroke, Sex) are encoded using OrdinalEncoder into values like 0 and 1. This ensures these categorical values are transformed into numeric representations suitable for machine learning models.  

- Multi-Category Features like AgeCategory and GenHealth are encoded with custom ordinal mappings to reflect logical orders (e.g., "Poor" to "Excellent" or age brackets).  

- One-Hot Encoding for categorical variables without a clear order, such as Race and Diabetic, OneHotEncoder is used to create separate columns for each category. This avoids imposing ordinal relationships on non-ordinal data.  

**Feature Analysis**:  
- For integration of encoded data, we merged back the encoded data into the training set, ensuring that all transformed features are included.  
- We explored correlations to identify significant predictors, like exercise levels and cholesterol.  

# Key Findings
1. **Exercise and Cholesterol: Lack of exercise correlates with lower HDL cholesterol**  

    A strong negative correlation (-0.49) was observed between low exercise habits and low HDL cholesterol levels. This suggests that individuals with lower levels of physical activity tend to have reduced levels of "good" cholesterol (HDL), which is critical for cardiovascular health.  
    HDL cholesterol helps remove other forms of cholesterol from the bloodstream and protects against heart disease.  
    Low exercise habits, as a modifiable lifestyle factor, directly influence HDL levels and, by extension, overall cardiovascular health.  

2. **Diabetes Risk: Fasting blood sugar levels strongly align with diabetes prevalence** 

    Diabetes strongly correlates with fasting blood sugar (0.65) and moderately with physical health (0.43), highlighting its critical role as a cardiovascular risk factor.  
    Diabetes significantly impacts overall health and increases the risk of complications like heart disease and kidney damage.  
    Early detection and management of diabetes are essential to improving health outcomes and reducing cardiovascular risks.  
    Including fasting blood sugar as a key predictor in heart disease models promotes lifestyle interventions like physical activity and healthy diets.  

3. **BMI as a Factors: Higher BMI is linked to elevated cholesterol levels**
   
    BMI shows mild positive correlations with high LDL cholesterol (0.2) and overall cholesterol levels (0.15), indicating that higher BMI is associated with elevated "bad" cholesterol, a known risk factor for heart disease.  
    High BMI reflects overweight or obesity, which are strongly linked to cardiovascular disease risk.  
    BMI is a significant, modifiable factor in cardiovascular health. Reducing obesity can directly lower heart disease risks.  
    Include BMI as a critical feature in heart disease predictive models and promote public health initiatives focused on weight management through healthier lifestyles.

4. **Age and Chronic Conditions: Older individuals show higher heart disease risks due to compounded health challenges.**  
    
    Age strongly correlates with heart disease (0.68 for 65+), and chronic conditions like stroke and diabetes amplify the risk.  
    While age is non-modifiable, managing chronic conditions can significantly reduce cardiovascular risks.  
    Prioritize early screening and include age and chronic conditions in heart disease models to enhance accuracy.  

<p align="center">
  <img src="images/rjf_corr_matrix.png" alt="Correlation Matrix" width="600">
</p>

<p align="center">
  <img src="images/cms_cm.png" alt="CMS Correlation Matrix" width="600">
</p>

# Machine Learning Approach
 **Models**
- **Logistic Regression**:  
Achieved 93% accuracy, highlighted feature importance.  
Its performance suggests clear linear patterns in the data, supported by preprocessing techniques like resampling and PCA. It cannot capture complex non-linear relationships in the data.  

- **Decision Tree**: Less Robuts 91% accuracy.  
Use as a baseline model for interpretability. It prones to overfitting and it's less robust than ensemble methods like Random Forest.  

- **Random Forest**: Delivered robust performance with 92% accuracy.  
It outperforms the DecisionTreeClassifier in all metrics (accuracy, precision, and recall). Also benefits from hyperparameter tuning using RandomizedSearchCV, which likely optimized its performance.  

![CMS Cardiovascular Disease Data](images/dt_rf.png)

**Feature Engineering**  
- Under-Sampling, SMOTE, and SMOTE-ENN  
To address the class imbalance in the heart disease dataset and to create a more balanced dataset by increasing the representation of heart disease cases.  
The confusion matrix after applying SMOTE for resampling demonstrates exceptional results: 
    - True Positives (TP): 2,750 — Correctly predicted positive class cases.  
    - True Negatives (TN): 29,230 — Correctly predicted negative class cases.  
    - False Positives (FP): 0 — Cases incorrectly predicted as positive.  
    - False Negatives (FN): 0 — Cases incorrectly predicted as negative.  
These results indicate zero misclassifications, with all positive and negative cases predicted accurately. The perfect prediction metrics reflects the effectiveness of the resampling techniques and the Random Forest model.  

<p align="center">
  <img src="images/rjf_resampled_conf_matrix.png" alt="Correlation Matrix" width="600">
</p>

- PCA  
To simplify the dataset by keeping the most important features, making the analysis more efficient and reducing noise. The Random Forest model, trained on this balanced and PCA-transformed data, achieved better accuracy and fairness in predicting heart disease. Random Forest proved highly effective in handling imbalanced data and improving predictions for underrepresented groups.  

# Conclusion and Recommendations
### Conclusion
The findings emphasize the importance of lifestyle changes and early interventions in reducing the risk of heart disease. Our models have demonstrated robust predictive power, with Random Forest providing reliable insights. By focusing on modifiable factors such as exercise and weight management, there is significant potential to mitigate cardiovascular risk at both individual and population levels.

### Recommendations
- **Encourage Preventive Healthcare**:  
Exercise and weight management emerged as significant modifiable predictors. Promote regular physical activity and healthy dietary practices through public health initiatives.

- **Adopt Data-Driven Policy Making**:  
Use findings to guide resource allocation and intervention strategies like campaigns focused on lifestyle interventions in healthcare systems.

-  **Enhance Health Monitoring**:  
Encourage the integration of predictive tools like our machine learning models into routine health assessments for early detection. Data-backed evidence emphasizes the need for proactive healthcare policies targeting physical activity and dietary improvements.

- **Expand Research**:  
Develop alternate methods for combining datasets at a group level rather than at the patient level. Focus on refining feature selection to enhance interpretability and simplify predictive models. Experiment with advanced machine learning techniques, including gradient boosting classifiers and neural networks, to explore varied approaches and improve predictive accuracy.  

# Summary  

- The heart disease prediction uses machine learning to uncover significant factors and provide actionable insights. By leveraging datasets from Kaggle and the CDC, the analysis identified key predictors of heart disease, including exercise habits, diabetes, BMI, and age-related health risks.

- The lack of exercise strongly correlates with low HDL cholesterol, emphasizing the importance of physical activity in cardiovascular health. Diabetes was found to have a significant correlation with fasting blood sugar, underscoring its role as a major cardiovascular risk factor.  

- BMI was linked to elevated LDL cholesterol, making weight management a crucial factor in reducing heart disease risk.  

- Age and chronic conditions such as diabetes and stroke were identified as compounding risk factors, particularly in older populations.

- Several machine learning models were tested, with Random Forest emerging as the most robust performer, achieving 92% accuracy. Techniques like SMOTE and PCA were applied to balance the dataset and improve model efficiency, ensuring better predictions for underrepresented groups.  

# Presentation  

[Download the Heart Disease Feature Prediction Presentation](AI_Bootcamp_Project_2.pptx)

# Contributors
This project was developed by:
- Robert Ferrari
- Laetitia Germe
- Tamara Freeman
- Vinayak Grover