# Predictive Maintenance for IoT Sensor Devices

This project focuses on developing a predictive maintenance system for IoT-enabled industrial equipment. By analyzing sensor data, the system aims to predict equipment failures, allowing for timely maintenance and reducing unexpected downtimes.

---

## 📁 Project Structure

- `Predictive_Maintenance_for_IoT_Sensor_Devices.ipynb`: Main Jupyter notebook containing data preprocessing, feature engineering, model training, evaluation, and visualization.
- `train.csv`: Training dataset with sensor readings and failure labels.
- `test.csv`: Test dataset for model validation.
- `train_enhanced.csv`: Enhanced training dataset after feature engineering.
- `test_predictions.csv`: Predictions on the test dataset.

---

## 📊 Dataset Overview

The dataset comprises synthetic sensor data simulating real industrial scenarios. Key features include:

- `Timestamp`: Time of the sensor reading.
- `Device_ID`: Unique identifier for each device.
- `Vibration_Level`: Vibration intensity of the device.
- `Voltage_Fluctuation`: Variations in voltage supply.
- `Signal_Strength`: Strength of the signal received.
- `Temp_Sensor`: Temperature readings from the device.
- `Error_Code`: Binary indicator (0 or 1) denoting normal operation or failure.

The `Error_Code` is determined based on specific conditions:

if (rolling_avg_vibration > 1.0 and sudden_voltage_spike) or (signal drops over time):
    Error_Code = 1

## 🛠️ Feature Engineering

To enhance model performance, several features were engineered:

- **Vibration_Mean_3**: Rolling mean of vibration over a window of 3 readings.
- **Signal_Change**: Difference in signal strength between consecutive readings.
- **Vib_Temp_Ratio**: Ratio of vibration level to temperature.
- **Vibration_STD_3**: Rolling standard deviation of vibration over 3 readings.
- **Temp_Voltage_Interaction**: Product of temperature and voltage fluctuation.
- **Signal_Diff_Abs**: Absolute difference in signal strength.

---

## 🤖 Model Development

An XGBoost classifier was employed for failure prediction. Key steps included:

- **Data Preprocessing**: Label encoding for `Device_ID` and standardization of numerical features.
- **Model Training**: Utilized `RandomizedSearchCV` for hyperparameter tuning with a stratified 5-fold cross-validation.
- **Evaluation Metrics**: Assessed using classification report, confusion matrix, ROC AUC score, and precision-recall curves.
- **Threshold Optimization**: Determined the optimal probability threshold that maximizes the F1 score.

---

## 📈 Model Evaluation

The model's performance was evaluated on the test set:

- **Confusion Matrix**: Illustrates the true vs. predicted classifications.
- **Classification Report**: Provides precision, recall, F1-score, and support for each class.
- **ROC Curve**: Plots true positive rate against false positive rate.
- **Precision-Recall Curve**: Helps in selecting the optimal threshold.

---

## 🔍 Model Interpretability with SHAP

SHAP (SHapley Additive exPlanations) was used to interpret the model's predictions:

- **Feature Importance**: Identified top contributing features to the model's decisions.
- **Visualization**: Bar plots showcasing mean absolute SHAP values for the top features.

---

## 🧪 Validation on Test Data

The trained model was applied to the `test.csv` dataset:

- **Feature Engineering**: Applied the same preprocessing steps as the training data.
- **Prediction**: Generated failure predictions using the optimized threshold.
- **Output**: Saved predictions in `test_predictions.csv`.

---

## 📋 Final Report

The final report encompasses:

- **Model Overview**: Description of the modeling approach and rationale.
- **Feature Engineering**: Detailed explanation of engineered features.
- **Performance Metrics**: Comprehensive evaluation results.
- **SHAP Analysis**: Insights into feature contributions.
- **Business Implications**: Discussion on how the model can aid in proactive maintenance strategies.

---

## 🚀 Deployment Considerations

For real-world application:

- **Real-time Monitoring**: Integrate the model into IoT platforms for continuous monitoring.
- **Alert Systems**: Set up notifications for predicted failures.
- **Periodic Retraining**: Update the model with new data to maintain accuracy.

