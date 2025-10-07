# 🎭 Multi-modal Emotion Recognition: Text, Audio, and Video

## 👥 Team

| Name | SRN | Section |
|------|------|----------|
| NS Tushar | PES2UG22CS327 | F |
| Mrunal Anandache | PES2UG22CS323 | F |
| M V Parth | PES2UG22CS325 | F |
| Shambhavi Raikar | PESS2UG22CS919 | F |

---

## 🚀 Project Overview

This project was developed for the **PES University ML Hackathon**, focusing on **multi-modal emotion recognition** using **text, audio, and video** features.  
By fusing these three modalities, we achieved improved emotion classification accuracy compared to models trained on individual channels.

---

## 💾 Data Processing & Feature Extraction

### 📝 Text
- Cleaned (lowercased, removed non-letter characters)  
- Tokenized using **NLTK**  
- Removed stopwords  
- Extracted features via **TF-IDF Vectorizer**

### 🎵 Audio
- Extracted audio from videos using **pydub**  
- Converted to waveforms using **librosa**  
- Extracted features:
  - MFCC  
  - Chroma  
  - Spectral Contrast  
  - Zero Crossing Rate  
  - Tempo  

### 🎥 Video
- Captured **5 evenly spaced frames** per video (64×64 px)  
- Padded short videos at the end  
- Extracted **optical flow** and **color histogram** features  

---

## 🔗 Feature Fusion & Modeling

- **Early Fusion:** Concatenated features from multiple modalities before training  
- **PCA:** Applied to reduce audio feature dimensionality and prevent overfitting  
- **Classifier:** Random Forest  

---

## 📊 Results

| Modalities | Accuracy |
|-------------|-----------|
| Audio + Text | **0.50** |
| Video + Text | **0.48** |

Text-only models were also evaluated (accuracy, F1-score, precision) and showed meaningful contributions.

---

## 🧠 Key Insights
- Multi-modal fusion improves robustness and overall performance.  
- Audio features (MFCC, Chroma) contributed significantly to emotion prediction.  
- PCA effectively reduced dimensionality without major performance loss.  

---

## 🏁 Future Work
- Integration with transformer-based text encoders (e.g., BERT).  
- Deep CNN/LSTM architectures for video and audio feature learning.  
- Real-time emotion recognition deployment.  

---
