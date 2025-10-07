# ML_MultiModal_Analysis
Using DeepLearning for Multi Modal sentiment Analysis 
# Multi-modal Emotion Recognition: Text, Audio, and Video Fusion

## 👨‍💻 Team Information
| Name | SRN | Section |
| :--- | :--- | :--- |
| NS TUSHAR | PES2UG22CS327 | F |
| MRUNAL ANANDACHE | PES2UG22CS323 | F |
| M V PARTH | PES2UG22CS325 | F |
| SHAMBHAVI RAIKAR | PESS2UG22CS919 | F |

---

## 🎯 Project Overview
This project, developed for the **PES University Machine Learning Hackathon**, focuses on building a multi-modal classification model for emotion recognition. We leverage features extracted from **Text**, **Audio**, and **Video** data to capture a comprehensive understanding of emotional states, aiming to enhance prediction accuracy compared to a single-modality approach.

## 🛠️ Data Preprocessing & Feature Extraction

### 1. Text Modality
| Step | Technique/Function | Purpose |
| :--- | :--- | :--- |
| **Cleaning** | Custom function (`Text Preprocessing Function`) | [cite_start]Removal of non-alphabetic characters (punctuation, numbers) and conversion to lowercase to standardize the text data. [cite: 20, 21, 39] |
| **Tokenization** | NLTK's `word_tokenize` | [cite_start]Breaking down the utterance into individual words for word-level analysis. [cite: 23, 40] |
| **Stopword Removal** | NLTK Stopword List | [cite_start]Removing common words (e.g., "the," "is") to reduce noise and enhance semantic focus. [cite: 23, 47] |
| **Feature Extraction** | **`TfidfVectorizer`** | [cite_start]Used to extract meaningful features by calculating the Term Frequency-Inverse Document Frequency of tokens. [cite: 73, 74] |

### 2. Audio Modality
| Feature | Library/Function | Purpose |
| :--- | :--- | :--- |
| **Raw Extraction** | `pydub` | [cite_start]Extracting audio streams from the provided video datasets. [cite: 26] |
| **Waveform Conversion** | `Librosa` | [cite_start]Loading audio files and converting them into numerical arrays. [cite: 51, 52] |
| **MFCC** | `librosa` | Captures the **timbral texture** of the audio, crucial for recognizing speech and emotions. (Mean of the first 13 coefficients used)[cite_start]. [cite: 54, 55, 87] |
| **Chroma** | `librosa` | [cite_start]Related to the **pitch content**, useful for harmony and tonality analysis. [cite: 58, 88] |
| **Spectral Contrast** | `librosa` | [cite_start]Measures amplitude differences between peaks and valleys, capturing **timbral texture**. [cite: 61, 89] |
| **Zero Crossing Rate** | `librosa` | [cite_start]Rate of signal sign change, used for distinguishing between percussive and non-percussive sounds (or speech/music separation). [cite: 64, 90] |
| **Tempo** | `librosa` | [cite_start]Measures the speed (BPM) of the audio, correlating with emotional states. [cite: 67, 91] |

### 3. Video Modality
| Feature | Extraction Method | Purpose |
| :--- | :--- | :--- |
| **Frame Capture** | `extract_video_features` | [cite_start]Captures **5 evenly spaced frames** per video, resized to $64 \times 64$ pixels to reduce computational complexity. [cite: 30, 31] |
| **Padding** | Frame Repetition | [cite_start]Ensures consistency by repeating the last frame if a video has fewer than 5 frames. [cite: 32] |
| **Optical Flow** | Used during feature extraction | [cite_start]Measures **motion between consecutive frames** to capture movement patterns and physical gestures related to emotion. [cite: 93] |
| **Color Histogram** | Used during feature extraction | [cite_start]Provides **color distribution information** as emotions can sometimes be associated with specific color patterns. [cite: 94] |

---

## 융 Fusion and Modeling

### Feature Fusion
[cite_start]We adopted an **Early Fusion** approach[cite: 75, 76].
* [cite_start]Text and video features were combined using `np.hstack()` to create a single feature set[cite: 70].
* [cite_start]Similarly, for the Audio-Text model, both features are concatenated into a single feature vector before model input, allowing the model to learn from both modalities simultaneously[cite: 77, 79, 80].

### Dimensionality Reduction
* [cite_start]**Principal Component Analysis (PCA)** is applied to the audio features after standardization using `StandardScaler`[cite: 95]. [cite_start]This is done to reduce the feature space, mitigate the risk of **overfitting**, and improve the model's generalization performance[cite: 96, 97, 99].

### Model Selection
* [cite_start]A **Random Forest Classifier** was chosen[cite: 100]. It is well-suited for handling high-dimensional data, imbalanced classes, and offers good interpretability.

---

## 📊 Results and Analysis

| Modality Combination | Accuracy Score |
| :--- | :--- |
| Audio-Text Combined Features | [cite_start]**0.50** [cite: 104] |
| Video-Text Combined Features | [cite_start]**0.48** [cite: 105] |

### Monomodal Evaluation (Text)
[cite_start]In the testing phase, an evaluation was also conducted using **only the text modality**[cite: 81]. [cite_start]The trained text model processed the text input, and its performance was assessed using standard classification metrics (accuracy, F1-score, precision)[cite: 84]. [cite_start]This highlights the individual contribution of the text data to the model's overall performance[cite: 83].
