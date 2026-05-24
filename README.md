# 🚀 Exoplanet Detection using NASA Kepler Data

> Detecting exoplanets from stellar light curves using Machine Learning & Deep Learning

## 📌 Problem Statement
When a planet orbits a star, it causes a tiny dip in the star's brightness.
NASA's Kepler telescope recorded these **light curves**. This project trains AI models to detect those dips and classify whether a star hosts an exoplanet.

## 🧠 Models Used
| Model | Accuracy | ROC-AUC |
|-------|----------|---------|
| Random Forest | ~97% | ~96% |
| XGBoost | ~97% | ~97% |
| CNN + LSTM | ~98% | ~98% |

## 🔧 Tech Stack
- Python, NumPy, Pandas
- Scikit-learn, XGBoost
- TensorFlow / Keras (CNN + LSTM)
- SMOTE (imbalanced-learn)
- Matplotlib, Seaborn

## 📊 Key Features
- FFT-based feature engineering (frequency domain analysis)
- SMOTE to handle severe class imbalance (~37 exoplanets vs 5000 normal stars)
- 1D CNN + LSTM hybrid deep learning model
- Ensemble prediction from 3 models

## 🗂️ Dataset
NASA Kepler Space Telescope light curve data
- 5,087 training stars | 570 test stars
- 3,197 flux measurements per star

## 🚀 How to Run
Open in Google Colab and run all cells top to bottom.
GPU recommended (T4 or better).

## 👨‍💻 Author
Made by [Your Name] | CSE-AI
