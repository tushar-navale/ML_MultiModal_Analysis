Multi-modal Emotion Recognition: Text, Audio, and Video
👥 Team
Name	SRN	Section
NS Tushar	PES2UG22CS327	F
Mrunal Anandache	PES2UG22CS323	F
M V Parth	PES2UG22CS325	F
Shambhavi Raikar	PESS2UG22CS919	F
🚀 Project Overview
We developed a multi-modal emotion recognition model for the PES University ML Hackathon using features from text, audio, and video. Fusing these modalities enhances emotion classification accuracy over individual channels.

💾 Data Processing & Feature Extraction
Text
Cleaned (lowercase, remove non-letters)

Tokenized using NLTK

Stopword removal

Features via TfidfVectorizer

Audio
Extracted from videos (pydub)

Converted to waveforms (librosa)

Extracted features: MFCC, Chroma, Spectral Contrast, Zero Crossing Rate, Tempo

Video
Captured 5 evenly spaced frames per video (64×64 px)

Padded short videos at the end

Extracted optical flow and color histogram features

🔗 Feature Fusion & Modeling
Early fusion: Concatenate features from multiple modalities before training

PCA to reduce audio feature dimensionality and prevent overfitting

Random Forest used for classification

📊 Results
Modalities	Accuracy
Audio + Text	0.50
Video + Text	0.48
Text-only models evaluated as well (accuracy, F1-score, precision) and showed meaningful contributions.
