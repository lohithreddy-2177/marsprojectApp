# emotionrecognition-app
Emotion Recognition:
Model Pipeline:
  - Intro to Dataset
  - Data preprocessing
      |
       -Featrue extraction
      |
       - Exploratory data analysis
  - Model deployment
  - Evaluation
  - Streamlit Deployment



Intro to Dataset:
     The RAVDESS dataset is a multi-modal emotional expression dataset consisting of speech and song recordings from professional actors.
     Audio_Speech_Actors_01-24/
     ├── Actor_01/
     │   ├── 03-01-01-01-01-01-01.wav
     │   ├── 03-01-01-01-01-02-01.wav
     │   └── ...
     ├── Actor_02/
     │   └── ... 
     ...
     ├── Actor_24/
     There is a specific file structure for each audio in the dataset.
     let's decode it
     Audio_Song_Actors_01-24 contains total of 1012 samples of audio
     Audio_Speech_Actors_01-24  contains total of 1440 samples of dataset
     Each file follows the naming convention:
     modality-vocal_channel-emotion-intensity-statement-repetition-actor.wav
     Breakdown:
     | Position | Field         | Example | Meaning                              |
     | -------- | ------------- | ------- | ------------------------------------ |
     | 1        | Modality      | 03      | Audio-Visual                         |
     | 2        | Vocal Channel | 01/02   | 01 = speech, 02 = song               |
     | 3        | Emotion       | 06      | 06 = fearful                         |
     | 4        | Intensity     | 01/02   | 01 = normal, 02 = strong             |
     | 5        | Statement     | 01/02   | 01 = “kids”, 02 = “dogs”             |
     | 6        | Repetition    | 01/02   | 1st or 2nd repetition                |
     | 7        | Actor         | 01–24   | Actor ID (odd = male, even = female) |
     Emotion mapping:
     | Code | Emotion   |
     | ---- | --------- |
     | 01   | Neutral   |
     | 02   | Calm      |
     | 03   | Happy     |
     | 04   | Sad       |
     | 05   | Angry     |
     | 06   | Fearful   |
     | 07   | Disgust   |
     | 08   | Surprised |
     Modality:
     | Value | Meaning      |
     | ----- | ------------ |
     | 01    | Audio only   |
     | 02    | Video only   |
     | 03    | Audio-Visual |
     Vocal Channel:
     | Value | Type       |
     | ----- | ---------- |
     | 01    |   Speech   |
     | 02    |   Song     |
     Emotional Intensity:
     | Code | Intensity |
     | ---- | --------- |
     | 01   | Normal    |
     | 02   | Strong    |
     Statement:
     | Code | Sentence                       |
     | ---- | ------------------------------ |
     | 01   | "Kids are talking by the door" |
     | 02   | "Dogs are sitting by the door" |
     Repetition:
     | Code | Repetition       |
     | ---- | ---------------- |
     | 01   | First utterance  |
     | 02   | Second utterance |

Data preprocessing:
    1) Feature Extraction:
       Features that i used:
        MFCC (Mel-Frequency Cepstral Coefficients)
        Delta MFCC
        Log Mel-Spectrogram
        Zero-Crossing Rate (ZCR)
        Spectral Centroid 
        Spectral Bandwidth 
        Spectral Rolloff 
        Spectral Flatness
        Spectral Contrast
    2)explorat


     


 
     



     

    
