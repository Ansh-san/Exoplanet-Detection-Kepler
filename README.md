# Exoplanet Detection from Kepler Light Curves 🔭

Detecting exoplanets from NASA Kepler light curves using classical ML and Deep Learning.

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)

## Overview

This project analyzes flux (light intensity) data from stars observed by the NASA Kepler
space telescope to classify each star as **exoplanet-hosting** or **non-exoplanet-hosting**.
A transiting exoplanet causes a small, periodic dip in a star's brightness as it passes in
front of it — this project trains models to detect that pattern automatically.

## Dataset

- **Source:** [<DATASET NAME, e.g. Kaggle "Kepler Labelled Time Series Data">](<DATASET LINK>)
- **Size:** 5,087 stars in the training set, 570 in the test set
- **Features:** 3,197 flux (brightness) measurements per star, highly imbalanced (very few confirmed exoplanet-hosting stars)
- Raw data is not included in this repo. Download instructions: `<ADD DOWNLOAD SCRIPT OR STEPS>`

## Approach

1. **Preprocessing** — normalization, noise reduction, handling missing values
2. **Feature engineering** — FFT (Fast Fourier Transform) analysis to extract frequency-domain features from light curves
3. **Class imbalance handling** — SMOTE applied **only on the training split** to avoid data leakage
4. **Models trained:**
   - Random Forest
   - XGBoost
   - CNN-LSTM (deep learning, sequence-based)

## Results

> ⚠️ Because exoplanets are rare in this dataset, accuracy alone is misleading.
> Precision, recall, and F1 for the **exoplanet class specifically** are the metrics that matter here —
> the numbers below are overall accuracy / ROC-AUC; add per-class precision/recall/F1 if you have them,
> since that's what best demonstrates the model actually catches rare exoplanets rather than just
> predicting "no exoplanet" every time.

| Model | Accuracy | ROC-AUC |
|---|---|---|
| Random Forest | ~97% | ~96% |
| XGBoost | ~97% | ~97% |
| CNN-LSTM | ~98% | ~98% |

**Confusion Matrices**

![Confusion Matrices](images/confusion_matrices.png)

**ROC Curves**

![ROC Curves](images/roc_curves.png)

**Feature Importance**

![Feature Importance](images/feature_importance.png)

**FFT Analysis**

![FFT Analysis](images/fft_analysis.png)

**Sample Light Curves**

![Light Curves](images/light_curves.png)

**Training History (CNN-LSTM)**

![Training History](images/training_history.png)

**Class Distribution**

![Class Distribution](images/class_distribution.png)

## Project Structure

```
├── notebooks/
│   └── Exoplanet_Detection_Kepler.ipynb   # main exploration & training notebook
├── images/                                 # result plots used in this README
├── requirements.txt
├── LICENSE
└── README.md
```

## How to Run

```bash
git clone https://github.com/Ansh-san/Exoplanet-Detection-Kepler.git
cd Exoplanet-Detection-Kepler
pip install -r requirements.txt
jupyter notebook notebooks/Exoplanet_Detection_Kepler.ipynb
```

## Limitations & Future Work

- With such extreme class imbalance, accuracy/ROC-AUC alone can look excellent while still
  missing most real exoplanets — adding explicit precision/recall/F1 for the positive class
  would give a more honest picture of performance.
- `<e.g. Model trained only on Kepler data — generalization to TESS data untested>`
- `<e.g. Deeper CNN architectures / attention-based models could be explored>`
- `<e.g. Hyperparameter tuning was limited to X, could expand with grid/Bayesian search>`

## References

- NASA Kepler Mission: https://www.nasa.gov/mission_pages/kepler/main/index.html
- `<Add dataset citation here>`

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.
