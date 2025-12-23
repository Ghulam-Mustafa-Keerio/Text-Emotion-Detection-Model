# 🎭 EmotionFlow: 7-Emotion NLP Detector

A high-recall text classification engine built on **XGBoost** and the **Google GoEmotions** dataset. This project maps 28 nuanced Reddit expressions down to the 7 core Ekman emotions (Joy, Anger, Fear, Sadness, Surprise, Disgust, and Neutral).

## 🚀 Key Features
- **Imbalance Handling:** Uses internal positional scaling to detect rare emotions like Fear and Disgust.
- **Ekman Mapping:** Bridges modern social media slang with psychological core emotions.
- **Optimized Recall:** Tuned with a custom probability threshold ($t=0.3$) to ensure emotions are caught even in subtle text.

## 📊 Performance Analysis
The model was evaluated using a 20% test split from GoEmotions. By grouping 28 labels into 7, we achieved a balanced **Macro F1-Score of 0.41**.

### Results Highlights
| Emotion | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- |
| **Joy** | 0.60 | 0.68 | 0.64 |
| **Sadness** | 0.47 | 0.44 | 0.46 |
| **Neutral** | 0.30 | 0.98 | 0.46 |

## 🛠️ Installation
```bash
git clone [https://github.com/yourusername/emotion-flow.git](https://github.com/yourusername/emotion-flow.git)
cd emotion-flow
pip install -r requirements.txt
