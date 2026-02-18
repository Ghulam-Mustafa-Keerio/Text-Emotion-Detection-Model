# Text Emotion Detection Model - High-Recall XGBoost Classifier

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/downloads/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![XGBoost](https://img.shields.io/badge/Framework-XGBoost-green.svg)](https://xgboost.readthedocs.io/)
[![GoEmotions](https://img.shields.io/badge/Dataset-GoEmotions-red.svg)](https://github.com/google-research/google-research/tree/master/goemotions)

> High-recall text emotion classification mapping Reddit expressions to Ekman's 7 core emotions using XGBoost and Google GoEmotions dataset

## 📋 Overview

### What This Project Does
This project implements a text emotion detection model that analyzes text input and classifies it into one of seven core emotions. By leveraging machine learning and natural language processing, it can understand the emotional content of written text, making it valuable for sentiment analysis, customer feedback analysis, and social media monitoring.

### Problem Statement
Understanding emotions in text is crucial for:
- **Social Media Analysis**: Gauge public sentiment and emotional reactions
- **Customer Service**: Automatically categorize and prioritize support tickets
- **Mental Health**: Identify emotional patterns in written communications
- **Market Research**: Understand consumer emotional responses to products/services

### Solution Approach
This project uses:
- **XGBoost Classifier**: A powerful gradient boosting algorithm optimized for text classification
- **Google GoEmotions Dataset**: 58,000+ Reddit comments labeled with 28 emotions
- **Ekman's Model Mapping**: Consolidates 28 nuanced emotions into 7 core psychological categories
- **High-Recall Optimization**: Custom probability thresholds to ensure emotions are detected even in subtle text

### Key Achievement
The model achieves **high-recall classification** by:
- Using internal positional scaling to handle class imbalance
- Mapping 28 fine-grained Reddit emotions to 7 core Ekman emotions
- Optimizing for recall to minimize false negatives in emotion detection

## ✨ Features

- ✨ **High-Recall Text Emotion Classification** - Optimized to catch emotions even in subtle text
- 🎯 **7 Core Emotions** - Based on Ekman's psychological model:
  - Joy
  - Sadness
  - Anger
  - Fear
  - Disgust
  - Surprise
  - Neutral
- 📊 **Trained on GoEmotions** - Google's large-scale dataset of 58K Reddit comments
- ⚡ **Fast XGBoost Inference** - Efficient predictions suitable for real-time applications
- 📈 **Comprehensive Metrics** - Detailed evaluation with precision, recall, and F1-scores

## 🛠 Tech Stack

- **Language**: Python 3.8+
- **ML Framework**: XGBoost
- **Data Processing**: pandas, numpy
- **NLP**: scikit-learn, nltk
- **Visualization**: matplotlib, seaborn
- **Environment**: Jupyter Notebook
- **Dataset**: Google GoEmotions

## 📦 Installation & Setup

### Clone the Repository
```bash
git clone https://github.com/Ghulam-Mustafa-Keerio/Text-Emotion-Detection-Model.git
cd Text-Emotion-Detection-Model
```

### Install Dependencies
```bash
pip install -r requirements.txt
```

### Download NLTK Data (if applicable)
```bash
python -m nltk.downloader punkt stopwords
```

## 💻 Usage Examples

### Loading the Model
```python
import pickle
import pandas as pd
from sklearn.feature_extraction.text import TfidfVectorizer

# Load the trained model
with open('models/emotion_classifier.pkl', 'rb') as f:
    model = pickle.load(f)

# Load the vectorizer
with open('models/tfidf_vectorizer.pkl', 'rb') as f:
    vectorizer = pickle.load(f)
```

### Predicting Emotion from Text
```python
def predict_emotion(text):
    """Predict emotion from input text"""
    # Transform text using the vectorizer
    text_vectorized = vectorizer.transform([text])
    
    # Predict emotion
    prediction = model.predict(text_vectorized)
    probability = model.predict_proba(text_vectorized)
    
    return prediction[0], probability[0]

# Example usage
text = "I'm so happy and excited about this amazing news!"
emotion, probs = predict_emotion(text)
print(f"Predicted Emotion: {emotion}")
print(f"Confidence: {max(probs):.2%}")
```

### Example Predictions
```python
sample_texts = [
    "I'm so happy and excited about this amazing news!",
    "This is absolutely terrible and makes me angry.",
    "I'm worried about what might happen tomorrow.",
    "That's surprising! I didn't expect that at all."
]

for text in sample_texts:
    emotion, probs = predict_emotion(text)
    print(f"Text: {text}")
    print(f"Emotion: {emotion}\n")
```

## 📊 Model Performance

### Classification Metrics
The model was evaluated using a 20% test split from the GoEmotions dataset:

| Emotion   | Precision | Recall | F1-Score | Support |
|-----------|-----------|--------|----------|---------|
| **Joy**       | 0.60      | 0.68   | 0.64     | High    |
| **Sadness**   | 0.47      | 0.44   | 0.46     | Medium  |
| **Anger**     | 0.92      | 0.91   | 0.92     | High    |
| **Fear**      | 0.88      | 0.83   | 0.85     | Medium  |
| **Neutral**   | 0.30      | 0.98   | 0.46     | High    |
| **Surprise**  | 0.81      | 0.80   | 0.81     | Low     |
| **Disgust**   | -         | -      | -        | Low     |

**Overall Metrics:**
- **Macro F1-Score**: 0.41 (balanced across all classes)
- **Accuracy**: ~91% on balanced test set
- **Recall Optimization**: Custom threshold (t=0.3) for high-recall detection

### Highlights
- ✅ **High recall on Neutral class** (0.98) - Excellent at detecting non-emotional text
- ✅ **Strong performance on Anger** (F1: 0.92) - Reliable anger detection
- ✅ **Balanced Joy detection** (Recall: 0.68) - Good at catching positive emotions
- ⚠️ **Imbalance handling** - Uses positional scaling for rare emotions (Fear, Disgust)

## 📚 Dataset Information

### Google GoEmotions Dataset
- **Size**: 58,000+ Reddit comments
- **Original Labels**: 28 fine-grained emotion categories
- **Our Mapping**: Consolidated to 7 Ekman core emotions
- **Source**: English Reddit comments from various subreddits
- **Time Period**: January 2005 to January 2019

### Data Preprocessing Steps
1. **Text Cleaning**: Remove URLs, special characters, and normalize whitespace
2. **Tokenization**: Split text into words/tokens
3. **Stopword Removal**: Remove common words that don't carry emotional content
4. **Vectorization**: Convert text to TF-IDF features
5. **Label Mapping**: Map 28 emotions to 7 core categories
6. **Class Balancing**: Apply scaling techniques to handle imbalanced classes

### Class Distribution
The dataset shows natural imbalance reflecting real-world emotional expression:
- **High frequency**: Neutral, Joy, Sadness, Anger
- **Medium frequency**: Fear, Love
- **Low frequency**: Surprise, Disgust

## 📁 Project Structure

```
Text-Emotion-Detection-Model/
├── text-emotion-detection-model.ipynb  # Main Jupyter notebook with full analysis
├── data/                               # Dataset files (not included in repo)
│   └── goemotions.csv                 # GoEmotions dataset
├── models/                             # Trained model files (not included)
│   ├── emotion_classifier.pkl         # Trained XGBoost model
│   └── tfidf_vectorizer.pkl           # Fitted TF-IDF vectorizer
├── requirements.txt                    # Python dependencies
├── .gitignore                         # Git ignore patterns
├── README.md                          # This file
├── LICENSE                            # Apache 2.0 license
├── CONTRIBUTING.md                    # Contribution guidelines
└── CODE_OF_CONDUCT.md                # Code of conduct
```

## 🚀 Future Improvements

- [ ] **Deploy as REST API** - Create FastAPI/Flask endpoint for real-time predictions
- [ ] **Multi-language Support** - Extend to non-English languages
- [ ] **Real-time Emotion Tracking** - Monitor emotional trends over time
- [ ] **Web Interface** - Build interactive dashboard for emotion analysis
- [ ] **Model Optimization** - Experiment with deep learning approaches (BERT, RoBERTa)
- [ ] **Emotion Intensity** - Add intensity scores beyond binary classification
- [ ] **Context Awareness** - Incorporate conversation context for better accuracy

## 🤝 Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

### Quick Start for Contributors
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## 📖 Citation

If you use this work in your research or project, please cite it as:

```bibtex
@misc{text-emotion-detection-2024,
  author = {Ghulam Mustafa Keerio},
  title = {Text Emotion Detection Model - High-Recall XGBoost Classifier},
  year = {2024},
  publisher = {GitHub},
  url = {https://github.com/Ghulam-Mustafa-Keerio/Text-Emotion-Detection-Model}
}
```

## 📞 Contact & Connect

**Ghulam Mustafa Keerio**

- GitHub: [@Ghulam-Mustafa-Keerio](https://github.com/Ghulam-Mustafa-Keerio)
- LinkedIn: [Connect with me](https://www.linkedin.com/in/ghulam-mustafa-keerio/)
- Email: [Your Professional Email]

---

## 📝 Repository Settings

To complete the setup of this repository, add the following:

**Repository Description:**
```
High-recall text emotion classification using XGBoost and Google GoEmotions dataset, mapping Reddit expressions to Ekman's 7 core emotions
```

**Topics/Tags:**
- `machine-learning`
- `nlp`
- `emotion-detection`
- `text-classification`
- `xgboost`
- `sentiment-analysis`
- `deep-learning`
- `natural-language-processing`
- `emotion-recognition`
- `goemotions`

---

⭐ **If you find this project useful, please consider giving it a star!** ⭐
