# Vibration-Based Bearing Fault Classification

## Project Overview

This project develops a vibration-based bearing fault classification system using signal processing and classical machine learning.

The system classifies three bearing fault types:

- Ball fault
- Inner-race fault
- Outer-race fault

The project uses CWRU-derived MATLAB vibration recordings and combines multiband signal processing, Hilbert envelope analysis, frequency-domain feature extraction, and machine learning.

## Methodology

The main processing pipeline is:

1. Load MATLAB vibration recordings and obtain rotational speed (RPM).
2. Apply a fourth-order Butterworth filter bank to the complete vibration signal.
3. Calculate the Hilbert envelope of each filtered signal.
4. Divide the filtered signals and envelopes into 0.5-second windows.
5. Extract statistical and frequency-domain features using Welch's power spectral density.
6. Aggregate window-level features using the median and interquartile range (IQR).
7. Apply preprocessing and feature selection.
8. Compare five classical machine learning classifiers.
9. Evaluate the models using Leave-One-Group-Out cross-validation.

## Machine Learning Models

The following classifiers were compared:

- Random Forest
- Extra Trees
- Linear SVM
- RBF SVM
- Logistic Regression

The final model uses an Extra Trees classifier with median and IQR features.

## Results

Using the 60-recording, 15-physical-group development dataset:

| Metric | Extra Trees |
|---|---:|
| Accuracy | 83.33% |
| Balanced Accuracy | 82.74% |
| Macro-F1 | 82.0% |

The model correctly classified 50 out of 60 recordings.

Class-wise accuracy:

| Fault Type | Correct | Total | Accuracy |
|---|---:|---:|---:|
| Ball fault | 14 | 16 | 87.5% |
| Inner-race fault | 12 | 16 | 75.0% |
| Outer-race fault | 24 | 28 | 85.7% |

## Important Note

The reported 83.33% result is a pooled out-of-fold development estimate obtained using Leave-One-Group-Out cross-validation. The same development groups were involved in feature/model selection, so this result should not be interpreted as performance on a completely untouched final test set.

The dataset contains three fault classes and does not include a healthy-bearing class.

## Report

The complete project report is available here:

`Bearing_Fault_Classification_Report.pdf`

## Tools and Technologies

- Python
- NumPy
- SciPy
- scikit-learn
- MATLAB-format vibration data
- Signal processing
- Hilbert transform
- Welch PSD
- Extra Trees
- Support Vector Machines
- Logistic Regression

## Project Context

Bearing Fault Classification Project  
Department of Electrical Engineering  
Indian Institute of Technology Bombay
