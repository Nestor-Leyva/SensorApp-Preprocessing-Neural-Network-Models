# SensorApp: A Digital Mirror
## Personality Recognition with Deep Learning Using a Mobile Usage Dataset

**Submission ID:** 10133

---

### Authors Description
* **Néstor Leyva López**: PhD student in engineering science at Tecnológico Nacional de México: Instituto Tecnológico de Culiacán. His research interests include machine and deep learning and affective computing.
* **Ramón Zatarain Cabada**: Professor and researcher at Tecnológico Nacional de México: Instituto Tecnológico de Culiacán. He holds a Ph.D. in Computer Science and focuses on artificial intelligence in education and affective computing.
* **María Lucía Barrón Estrada**: Professor and researcher at Tecnológico Nacional de México: Instituto Tecnológico de Culiacán. She holds a Ph.D. in Computer Science and specializes in AI and affective computing applied to education.
* **Hugo Jair Escalante**: Full-time researcher at the Instituto Nacional de Astrofísica, Óptica y Electrónica (INAOE). He is an Associate Editor for IEEE Transactions on Affective Computing and specializes in machine learning.

---
### Project Overview
This repository contains the official implementation of the methodology proposed in the manuscript **"SensorApp: A Digital Mirror"**. The study predicts personality traits according to the **OCEAN model** by integrating mobile sensor data (accelerometer and gyroscope) and self-reported usage habits using deep neural networks.

The project evaluates four main architectures: **MLP, CNN, LSTM, and Transformer**.

---

### File Description
The following scripts represent the complete pipeline for data processing and model training:

1. **`1 - basic preprocessing.py`**:
    * Loads raw data from JSON format.
    * Calculates basic descriptive statistics: mean and standard deviation for both sensors.
    * Normalizes OCEAN trait values to a 0-1 range.
    * Implements feature scaling using `StandardScaler`.

2. **`2 - Deep Learning Models.py`**:
    * Initial implementation of MLP, CNN, LSTM, and Transformer architectures using only basic sensor metrics.

3. **`3 - Advanced preprocessing (statistical features).py`**:
    * **Time Domain**: Implements Variance, Interquartile Range (IQR), Root Mean Square (RMS), and Entropy.
    * **Frequency Domain**: Implements Discrete Fast Fourier Transform (DFFT), Discrete Cosine Transform (DCT), Energy, and Power Frequency Range (PFR).

4. **`4 - Deep Learning Models (new features).py`**:
    * Final training environment using the augmented feature set (Time + Frequency domains).
    * Includes **K-Fold Cross-Validation** to ensure robust performance estimation.

---
### How to Reproduce the Results
### Dependencies Description

- **TensorFlow/Keras**: For deep learning model architecture.  
- **Scikit-learn**: For data scaling (`StandardScaler`) and dataset splitting.  
- **Scipy**: Specifically `scipy.fftpack` for Discrete Cosine Transform (DCT) calculations.  

---

### Computational Environment

The experiments were executed in **Google Colaboratory**. For optimal performance, we recommend:

- **Runtime**: Python 3 with GPU acceleration (NVIDIA Tesla T4 or similar).  
- **RAM**: Minimum 12 GB.  

---

#### Execution Order

Follow this order to replicate the study's findings:

- **Preparation**: Run `1 - basic preprocessing.py` to generate the base DataFrame.  

- **Initial Benchmark**: Run `2 - Deep Learning Models.py` to evaluate performance using basic features only.  

- **Advanced Feature Extraction**: Run `3 - Advanced preprocessing (statistical features).py` to generate the `df_completo` file.  

- **Final Training**: Run `4 - Deep Learning Models (new features).py` to obtain the final results (MSE/MAE).  

---
### Results Summary

- **CNN**: Most effective when working only with raw movement data, showing the best performance in cross-validation.  
  - **Average MAE: 0.1689**

- **Transformer**: Superior performance when integrating statistical metrics from time and frequency domains.  
  - **MSE = 0.0513**  
  - **MAE = 0.1704**
