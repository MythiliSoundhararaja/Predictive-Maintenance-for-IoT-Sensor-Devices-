
## 📁 Project Structure

- `Predictive_Maintenance_for_IoT_Sensor_Devices.ipynb`:Main Jupyter notebook containing data preprocessing, feature engineering, model training, evaluation, and visualization
- `train.csv`:Training dataset with sensor readings and failure labels
- `test.csv`:Test dataset for model validation
- `train_enhanced.csv`:Enhanced training dataset after feature engineering
- `test_predictions.csv`:Predictions on the test dataset

## 📊 Dataset Overview
The dataset comprises synthetic sensor data simulating real industrial scenarios. Key features includ:

- `Timestamp` Time of the sensor readin.
- `Device_ID` Unique identifier for each devic.
- `Vibration_Level` Vibration intensity of the devic.
- `Voltage_Fluctuation` Variations in voltage suppl.
- `Signal_Strength` Strength of the signal receive.
- `Temp_Sensor` Temperature readings from the devic.
- `Error_Code` Binary indicator (0 or 1) denoting normal operation or failur.
The `Error_Code` is determined based on specific condition:

```python
if (rolling_avg_vibration > 1.0 and sudden_voltage_spike) or (signal drops over time):
    Error_Code = 1
``


## 🛠️ Feature Engineerin

To enhance model performance, several features were engineerd:

- `Vibration_Mean_3: Rolling mean of vibration over a window of 3 readins.
- `Signal_Change: Difference in signal strength between consecutive readins.
- `Vib_Temp_Ratio: Ratio of vibration level to temperatue.
- `Vibration_STD_3: Rolling standard deviation of vibration over 3 readins.
- `Temp_Voltage_Interaction: Product of temperature and voltage fluctuatin.
- `Signal_Diff_Abs: Absolute difference in signal strengh.

## 🤖 Model Developmet

An XGBoost classifier was employed for failure prediction. Key steps inclued:

- **Data Preprocessing*: Label encoding for `Device_ID` and standardization of numerical featues.
- **Model Training*: Utilized `RandomizedSearchCV` for hyperparameter tuning with a stratified 5-fold cross-validaton.
- **Evaluation Metrics*: Assessed using classification report, confusion matrix, ROC AUC score, and precision-recall cures.
- **Threshold Optimization*: Determined the optimal probability threshold that maximizes the F1 scre.

## 📈 Model Evaluaton

The model's performance was evaluated on the testset:

- **Confusion Matri**: Illustrates the true vs. predicted classificatons.
- **Classification Repor**: Provides precision, recall, F1-score, and support for each cass.
- **ROC Curv**: Plots true positive rate against false positive ate.
- **Precision-Recall Curv**: Helps in selecting the optimal thresold.

## 🔍 Model Interpretability with HAP

SHAP (SHapley Additive exPlanations) was used to interpret the model's predicions:

- **Feature Importane**: Identified top contributing features to the model's deciions.
- **Visualizatin**: Bar plots showcasing mean absolute SHAP values for the top feaures.

## 🧪 Validation on TestData

The trained model was applied to the `test.csv` dtaset:

- **Feature Engineerng**: Applied the same preprocessing steps as the trainin data.
- **Predicton**: Generated failure predictions using the optimized thrshold.
- **Outut**: Saved predictions in `test_prediction.csv`.

## 📋 Final eport

The final report encopasses:

- **Model Overiew**: Description of the modeling approach and raionale.
- **Feature Engineeing**: Detailed explanation of engineered fatures.
- **Performance Metics**: Comprehensive evaluation esults.
- **SHAP Analsis**: Insights into feature contriutions.
- **Business Implicatons**: Discussion on how the model can aid in proactive maintenance strtegies.

## 🚀 Deployment Consideations

For real-world appication:

- **Real-time Monitring**: Integrate the model into IoT platforms for continuous moitoring.
- **Alert Sytems**: Set up notifications for predicted ailures.
- **Periodic Retraning**: Update the model with new data to maintain ccuracy.

## 📌 Coclusion

This project demonstrates the potential of machine learning in predictive maintenance, leveraging IoT sensor data to foresee equipment failures and optimize maintenance chedules.

---

Feel free to customize this `README.md` further to align with your project's specifics and any additional insights you wish to highlight. 
