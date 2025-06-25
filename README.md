#  Emotion Recognition: Model Pipeline

##  Project Structure

- **Intro to Dataset**
- **Data Preprocessing**
  - Feature Extraction
- **Exploratory Data Analysis**
- **Model Deployment**
- **Evaluation**
- **Streamlit Deployment**

---

##  Intro to Dataset

The **RAVDESS** dataset is a multi-modal emotional expression dataset consisting of **speech** and **song** recordings from professional actors.

###  Dataset Folders:

- Audio_Speech_Actors_01-24: **1440 samples**
- Audio_Song_Actors_01-24: **1012 samples**


##  Filename Structure

Each filename is formatted as:


| Position | Field         | Example | Meaning                                      |
|----------|---------------|---------|----------------------------------------------|
| 1        | Modality      | 03      | 03 = Audio-Visual                            |
| 2        | Vocal Channel | 01/02   | 01 = Speech, 02 = Song                        |
| 3        | Emotion       | 06      | 06 = Fearful                                 |
| 4        | Intensity     | 01/02   | 01 = Normal, 02 = Strong                      |
| 5        | Statement     | 01/02   | 01 = "Kids", 02 = "Dogs"                      |
| 6        | Repetition    | 01/02   | 01 = First utterance, 02 = Second utterance   |
| 7        | Actor         | 01–24   | Actor ID (odd = male, even = female)         |

---

##  Emotion Mapping

| Code | Emotion    |
|------|------------|
| 01   | Neutral    |
| 02   | Calm       |
| 03   | Happy      |
| 04   | Sad        |
| 05   | Angry      |
| 06   | Fearful    |
| 07   | Disgust    |
| 08   | Surprised  |

---

##  Modality

| Value | Type          |
|-------|---------------|
| 01    | Audio Only    |
| 02    | Video Only    |
| 03    | Audio-Visual  |

---

##  Vocal Channel

| Value | Type    |
|-------|---------|
| 01    | Speech  |
| 02    | Song    |

---

##  Emotional Intensity

| Code | Intensity |
|------|-----------|
| 01   | Normal    |
| 02   | Strong    |

---

## Statements

| Code | Sentence                           |
|------|------------------------------------|
| 01   | "Kids are talking by the door"     |
| 02   | "Dogs are sitting by the door"     |

---

##  Repetition

| Code | Meaning           |
|------|-------------------|
| 01   | First utterance   |
| 02   | Second utterance  |

---

##  Data Preprocessing

###  Feature Extraction

Features used in this project:

- **MFCC** (Mel-Frequency Cepstral Coefficients)
- **Delta MFCC**
- **Log Mel-Spectrogram**
- **Zero-Crossing Rate (ZCR)**
- **Spectral Centroid**
- **Spectral Bandwidth**
- **Spectral Rolloff**
- **Spectral Flatness**
- **Spectral Contrast**

Each audio file is processed into a **220+ dimensional feature vector**.

---

##  Exploratory Data Analysis
---

##  Exploratory Data Analysis (EDA)

###  Emotion Distribution

- The chart shows the **frequency of each emotion** in the dataset.
- **Neutral** and **Happy** are the most common.
- **Disgust** and **Fearful** are the least frequent.

---

###  Power vs. Relative Pace (ZCR)

- **Power** (Log-Mel Energy):
  - Higher for high-energy emotions like **Angry** and **Happy**.
  - Lower for **Calm** and **Sad**.

- **Relative Pace** (Zero Crossing Rate - ZCR):
  - **Angry** and **Fearful** show **higher ZCR** → faster, more erratic pacing.
  - **Calm** and **Neutral** have **lower ZCR** → slower, smoother pacing.

---

###  Energy (RMS) Variation

- **High RMS Energy**:  
  - **Angry**, **Happy**, and **Surprised** exhibit higher energy.
  
- **Low RMS Energy**:  
  - **Sad**, **Calm**, and **Neutral** show lower energy.
  
- **Disgust** appears as an outlier with **moderate energy**.

---

### Tempo Variation

- **Fast Tempo**:  
  - **Angry**, **Surprised**, and **Happy** have faster tempos.

- **Slow Tempo**:  
  - **Sad**, **Calm**, and **Neutral** have slower tempos.

---

###  Pitch (Fundamental Frequency - F0) Variation

- **High Pitch**:  
  - **Angry**, **Fearful**, and **Surprised** show higher pitch ranges.

- **Low Pitch**:  
  - **Sad**, **Calm**, and **Neutral** are associated with lower pitch.

---

>  These insights are essential for understanding how audio characteristics align with emotional states, which informs feature engineering and model performance.


---
##  Model Deployment & Evaluation

---

##  Model Training & Evaluation

###  Model Details

- **Model Used**: `RandomForestClassifier()` from Scikit-learn
- **Label Encoding**: Applied `LabelEncoder()` to map emotion labels to integers
- **Train-Test Split**:  
  - `test_size = 0.2`  
  - `stratify = y_encoded` (to preserve emotion distribution)
  - `random_state = 42`

---

###  Evaluation Metrics

- **Accuracy**: **89%**
- **Macro F1-Score**: **0.89**
- **Weighted F1-Score**: **0.89**

####  Classification Report

| Emotion    | Precision | Recall | F1-score | Support |
|------------|-----------|--------|----------|---------|
| Angry      | 0.99      | 0.91   | 0.94     | 75      |
| Calm       | 0.85      | 0.91   | 0.88     | 75      |
| Disgust    | 0.87      | 0.96   | 0.91     | 75      |
| Fearful    | 0.89      | 0.84   | 0.86     | 76      |
| Happy      | 0.95      | 0.81   | 0.88     | 75      |
| Neutral    | 0.91      | 0.95   | 0.93     | 75      |
| Sad        | 0.88      | 0.80   | 0.84     | 76      |
| Surprised  | 0.83      | 0.96   | 0.89     | 75      |


####  Confusion Matrix Summary

| Emotion     | Correct Predictions | Misclassifications |
|-------------|---------------------|--------------------|
| Angry       | 68                  | 7                  |
| Calm        | 68                  | 7                  |
| Disgust     | 72                  | 3                  |
| Fearful     | 64                  | 12                 |
| Happy       | 61                  | 14                 |
| Neutral     | 71                  | 4                  |
| Sad         | 61                  | 15                 |
| Surprised   | 72                  | 3                  |


---
##  Offline Emotion Prediction (Notebook)

You can test the trained model using the Jupyter notebook:

**File:** `test_model.ipynb`

This allows testing on any `.wav` file and outputs the predicted emotion label.

# Example
test_file = "test.wav"
---


##  Streamlit Deployment

---

##  Live Demo

You can try out the deployed Streamlit web app here:

👉 **[Emotion Recognition App](https://marsprojectapp-33hckpieodv92lspyiiczn.streamlit.app/)**

> Upload a `.wav` file to predict the emotion using audio signal features like MFCC, ZCR, Spectral Contrast, etc.







     


     


 
     



     

    
