# Multi-modal Emotion Recognition: Text, Audio, and Video Fusion

## 🎯 Project Overview
[cite_start]Developed for the **PES University Machine Learning Hackathon**[cite: 3], this project focuses on building a **multi-modal** classification model for emotion recognition. [cite_start]By leveraging features extracted from **Text, Audio, and Video** data, we aim to capture a comprehensive understanding of emotional states, significantly improving prediction accuracy compared to a single-modality approach[cite: 98].

---

## 👨‍💻 Team Information

| Name | SRN | Section |
| :--- | :--- | :--- |
| NS TUSHAR | PES2UG22CS327 | [cite_start]F [cite: 6, 8, 5] |
| MRUNAL ANANDACHE | PES2UG22CS323 | [cite_start]F [cite: 9, 11, 5] |
| M V PARTH | PES2UG22CS325 | [cite_start]F [cite: 12, 14, 5] |
| SHAMBHAVI RAIKAR | PESS2UG22CS919 | [cite_start]F [cite: 15, 17, 5] |

---

## 🛠️ Data Preprocessing & Feature Extraction

### 1. Text Modality

| Step | Technique | Purpose |
| :--- | :--- | :--- |
| **Cleaning** | [cite_start]Non-alphabetic character removal and lowercasing [cite: 20, 21] | [cite_start]Standardizes text by reducing variations caused by punctuation or capitalization[cite: 23]. |
| **Tokenization** | [cite_start]NLTK `word_tokenize` [cite: 23, 40] | [cite_start]Breaks down text into smaller units (words) for analysis[cite: 40, 46]. |
| **Stopword Removal** | [cite_start]NLTK Stopword List [cite: 23] | [cite_start]Removes common words (e.g., "the", "is") that carry little semantic meaning to reduce noise[cite: 47]. |
| **Features** | [cite_start]**`TfidfVectorizer`** [cite: 74] | [cite_start]Extracts meaningful, weighted features from the cleaned text data[cite: 74, 49]. |

### 2. Audio Modality

| Feature | Library/Concept | Purpose |
| :--- | :--- | :--- |
| **Extraction** | [cite_start]`pydub` [cite: 26] | [cite_start]Extracts the audio component from video datasets[cite: 26]. |
| **Conversion** | [cite_start]`Librosa` [cite: 51] | [cite_start]Loads audio and converts it into numerical waveform arrays[cite: 52]. |
| **MFCC** | (Mean of the first 13 coefficients) [cite_start][cite: 55] | [cite_start]Captures **timbral texture**, crucial for speech and emotion recognition[cite: 55, 87]. |
| **Chroma** | [cite_start]`librosa` [cite: 58] | [cite_start]Represents the **pitch content**, useful for harmony and music analysis[cite: 58, 88]. |
| **Spectral Contrast** | [cite_start]`librosa` [cite: 61] | [cite_start]Measures amplitude differences between peaks/valleys, capturing timbral texture[cite: 61, 89]. |
| **Zero Crossing Rate** | [cite_start]`librosa` [cite: 64] | [cite_start]Rate of signal sign change, useful for distinguishing percussive/non-percussive sounds[cite: 65, 90]. |
| **Tempo** | [cite_start]`librosa` [cite: 67] | [cite_start]Measures the speed (BPM) of the audio, correlating with emotional states[cite: 67, 91]. |

### 3. Video Modality

| Feature | Method | Purpose |
| :--- | :--- | :--- |
| **Frame Capture** | [cite_start]5 evenly spaced frames, resized to $64 \times 64$ pixels [cite: 30, 31] | [cite_start]Reduces computational complexity and ensures consistent input dimensions[cite: 31]. |
| **Padding** | [cite_start]Last frame repetition [cite: 32] | [cite_start]Ensures frame consistency for videos shorter than the required number of frames[cite: 32]. |
| **Optical Flow** | [cite_start]Used during extraction [cite: 93] | [cite_start]Measures motion between frames to capture movement patterns and gestures associated with emotion[cite: 93]. |
| **Color Histogram** | [cite_start]Used during extraction [cite: 94] | [cite_start]Provides color distribution information, which can be useful as an emotional cue[cite: 94]. |

---

## 🔄 Fusion & Modeling

### Feature Fusion Strategy
[cite_start]We implement an **Early Fusion** strategy[cite: 75, 76].
* [cite_start]Modality features (e.g., Text + Video, or Text + Audio) are concatenated horizontally using `np.hstack()`[cite: 70, 77, 79].
* [cite_start]This single, combined feature vector is then fed into the model for training, allowing the model to learn from both modalities simultaneously[cite: 78, 80].

### Dimensionality Reduction
* [cite_start]**Principal Component Analysis (PCA)** is applied to the standardized audio features via `StandardScaler`[cite: 95].
* [cite_start]This reduces the feature space while retaining most of the variance, mitigating the risk of **overfitting** and speeding up training[cite: 96, 99].

### Classifier
* [cite_start]**Random Forest Classifier** [cite: 100] [cite_start]was chosen for its robustness in handling high-dimensional data and potentially imbalanced classes, while also offering high interpretability[cite: 100].

---

## 📊 Performance Analysis

[cite_start]The model was evaluated on a validation set using the Random Forest Classifier trained on combined features[cite: 102, 103].

| Modality Combination | Accuracy Score |
| :--- | :--- |
| Audio + Text Combined Features | [cite_start]**0.50** [cite: 104] |
| Video + Text Combined Features | [cite_start]**0.48** [cite: 105] |

### Monomodal Evaluation
The Text-only model was also evaluated during testing to highlight the individual contribution of the linguistic modality. [cite_start]Its performance was assessed using metrics like accuracy, F1-score, and precision[cite: 84].
