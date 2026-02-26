# SensorApp: A Digital Mirror
## Personality Recognition with Deep Learning Using a Mobile Usage Dataset

**Submission ID:** 10133

---

### Authors Description
* **Néstor Leyva López**: received the B.S. degree in mechatronics in 2018, and in 2022 he received his M.S. degree in computer science from Tecnológico Nacional de México: Instituto Tecnológico de Culiacán (TECNM: Instituto Tecnológico de Culiacán), Mexico. Currently he is a PhD student in engineering science at the same university. His research interests are machine and deep learning and affective computing.
* **Ramón Zatarain Cabada**: Professor and researcher at Tecnológico Nacional de México: Instituto Tecnológico de Culiacán (TECNM: Instituto Tecnológico de Culiacán). He received his M.S. and Ph.D. in Computer Science from the Florida Institute of Technology. Ramón Zatarain Cabada is a member level II in the National Researchers System (Conacyt, Mexico. His main research interests include artificial intelligence in education, m-learning and e-learning, and affective computing applied to education.
* **María Lucía Barrón Estrada**: Received the B.S. degree in informatics from Tecnológico Nacional de México: Instituto Tecnológico de Culiacán (TECNM: Instituto Tecnológico de Culiacán), Mexico, in 1987, the M.S. degree in computer sciences from Instituto Tecnológico de Toluca, Mexico, in 1990, and the Ph.D. degree in computer sciences from Florida Institute of Technology, Melbourne, FL, USA, in 2004. Dr. Barrón Estrada is a member level III in the National Researchers System (Conacyt, Mexico). Her research interests include artificial intelligence in education and affective computing applied to education.
* **Hugo Jair Escalante**: Received his Ph.D. degree in computer science from Instituto Nacional de Astrofísica, Óptica y Electrónica (INAOE) in 2010, where he is currently a full-time researcher. Hugo Jair Escalante Balderas is member level II in the National Researchers System (Conacyt, Mexico). Associate Editor of the IEEE Trans. on Affective Computing (since 2022), and the Data Centric Learning Research Journal. His research interests are in challenge organization, machine learning, and its applications in language and vision.

---
### Project Overview
This repository contains the official implementation of the methodology proposed in the manuscript **"SensorApp: A Digital Mirror"**. The study predicts personality traits according to the **OCEAN model** by integrating mobile sensor data (accelerometer and gyroscope) and self-reported usage habits using deep neural networks.

The project evaluates four main architectures: **MLP, CNN, LSTM, and Transformer**.

---

### File Description
The following scripts represent the complete pipeline for data processing and model training:

1. **`dataset_anonymized.json`**: The core dataset containing anonymized records of 126 participants. It includes sensor measurements (accelerometer and gyroscope), daily survey responses, and validated OCEAN scores from the IPIP-50 test.

2. **`1 - basic preprocessing.py`**:
    * Loads raw data from JSON format.
    * Calculates basic descriptive statistics: mean and standard deviation for both sensors.
    * Normalizes OCEAN trait values to a 0-1 range.
    * Implements feature scaling using `StandardScaler`.

3. **`2 - Deep Learning Models.py`**:
    * Initial implementation of MLP, CNN, LSTM, and Transformer architectures using only basic sensor metrics.

4. **`3 - Advanced preprocessing (statistical features).py`**:
    * **Time Domain**: Implements Variance, Interquartile Range (IQR), Root Mean Square (RMS), and Entropy.
    * **Frequency Domain**: Implements Discrete Fast Fourier Transform (DFFT), Discrete Cosine Transform (DCT), Energy, and Power Frequency Range (PFR).

5. **`4 - Deep Learning Models (new features).py`**:
    * Final training environment using the augmented feature set (Time + Frequency domains).
    * Includes **K-Fold Cross-Validation** to ensure robust performance estimation.

---
### How to Reproduce the Results
### Dependencies Description

- **TensorFlow/Keras**: For deep learning model architecture.  
- **Scikit-learn**: For data scaling (`StandardScaler`) and dataset splitting.  
- **Scipy**: Specifically `scipy.fftpack` for Discrete Cosine Transform (DCT) calculations.  

#### Installation
Clone the repository and install the dependencies listed in `requirements.txt`:

---

### Computational Environment

The experiments were executed in **Google Colaboratory**. For optimal performance, we recommend:

- **Runtime**: Python 3 with GPU acceleration (NVIDIA Tesla T4 or similar).  
- **RAM**: Minimum 12 GB.  

---

#### Execution Order

Follow this order to replicate the study's findings:

- **Preparation**: Place `dataset_anonymized.json` in your working directory and run `1 - basic preprocessing.py`.  

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
