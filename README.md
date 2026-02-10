# Heart-Disease-deepLearning

# 🫀 ECG Signal Denoising & Heart Disease Detection
### Using Fourier Transform (FFT) and CNN-LSTM

---

## 📌 Project Overview

This project implements a **real-world ECG signal analysis pipeline** for heart disease detection.  
Electrocardiogram (ECG) signals are often corrupted by noise such as power-line interference and muscle artifacts.  
To handle this, **Fourier Transform (FFT)** is applied for frequency-domain noise removal before deep learning-based classification.

The cleaned ECG signals are then classified using a **CNN-LSTM model**, which learns both:
- **Morphological features** (CNN)
- **Temporal patterns** (LSTM)

---

## 🎯 Objectives

- Apply **Fourier Transform (FFT)** for ECG signal denoising  
- Classify ECG heartbeats into multiple disease categories  
- Understand **training, validation, and test accuracy**  
- Build an **industry-aligned machine learning pipeline**

---

## 📂 Dataset Information

### ✅ MIT-BIH Heartbeat Dataset (CSV)

**Source:** Kaggle  
**Dataset Link:**  
https://www.kaggle.com/datasets/shayanfazeli/heartbeat


---

## 📊 Dataset Structure

Each row represents **one ECG heartbeat**.

| Column Range | Description |
|-------------|------------|
| 0 – 186 | ECG signal samples (187 points) |
| 187 | Class label |

- Sampling Frequency: **360 Hz**
- One heartbeat ≈ **0.52 seconds**
- Total Columns: **188**

### 🏷 Class Labels

| Label | Description |
|------|------------|
| 0 | Normal Beat |
| 1 | Supraventricular Ectopic Beat |
| 2 | Ventricular Ectopic Beat |
| 3 | Fusion Beat |
| 4 | Unknown / Paced Beat |

---

## 🧠 Methodology

### 🔹 1. Data Loading
- ECG data is loaded from CSV files using Pandas.
- Features and labels are separated.

### 🔹 2. Fourier Transform (FFT) Denoising
- ECG signals are converted from **time domain to frequency domain**.
- Frequencies outside the ECG band (0.5–40 Hz) are removed.
- Inverse FFT converts the signal back to time domain.

**Why FFT?**
- Removes power-line noise and muscle artifacts
- Matches real-world ECG device preprocessing

---

### 🔹 3. Data Preprocessing
- ECG signals are normalized
- Data reshaped into `(samples, 187, 1)` for CNN input
- Labels are one-hot encoded into 5 classes

---

### 🔹 4. Deep Learning Model

**CNN-LSTM Architecture**
- 1D Convolution layers extract ECG morphology
- LSTM captures temporal dependencies
- Softmax layer performs multi-class classification

---

## 🧪 Model Training

- Loss Function: `categorical_crossentropy`
- Optimizer: `Adam`
- Batch Size: `64`
- Epochs: `15`

### Data Split
- Training Data: Used to update model weights
- Validation Data: Used to monitor overfitting
- Test Data: Used for final evaluation

---

## 📈 Results

| Metric | Value |
|------|------|
| Training Accuracy | ~100% |
| Validation Accuracy | ~13% (due to class imbalance) |
| Test Accuracy | ~82–85% |

**Note:**  
High training accuracy indicates overfitting, while test accuracy reflects true generalization performance.

---

## ⚠️ Important Observations

- Validation accuracy is low because `validation_split` is not stratified.
- Test accuracy is the **correct metric** to report.
- FFT improves signal quality but can reduce class separability if applied aggressively.

---

## 📝 How to Run the Project

1. Download the dataset from Kaggle
2. Place `mitbih_train.csv` and `mitbih_test.csv` in the project folder
3. Run the notebook or script top-to-bottom
4. Evaluate model using test data

---

## 🧠 Key Learnings

- Difference between **training, validation, and test data**
- Practical use of **Fourier Transform in real systems**
- Overfitting in deep learning models
- Importance of proper data splitting

---

## 🚀 Future Improvements

- Use **Wavelet Transform** for better denoising
- Apply **stratified validation split**
- Add **class-imbalance handling**
- Deploy model for real-time ECG monitoring

---

## 👨‍💻 Author

**Project Type:** Academic  
**Domain:** AI + Signal Processing + Healthcare

---

## 📜 License

This project is intended for **educational and research purposes only**.
