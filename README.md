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

```python
if (rolling_avg_vibration > 1.0 and sudden_voltage_spike) or (signal drops over time):
    Error_Code = 1
