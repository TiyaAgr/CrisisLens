# CrisisLens
Detecting distress in social media text using NLP
## Overview
CrisisLens is an applied machine learning project focused on identifying distress-related messages from short social media text such as tweets. The motivation is to support applications in disaster response, crisis monitoring, and mental health awareness, where early detection of distress signals can be critical.
The project is built with a progressive ML approach:
* Start with a strong classical baseline
* Analyze limitations
* Improve performance using a transformer-based model
## Problem Statement
Social media platforms often become the first place where people express fear, distress, or urgent needs during disasters and emergencies. Manually monitoring such data is not scalable.
CrisisLens aims to automatically classify whether a given piece of text represents a distress signal or not.
## Project Structure
The repository is organized to clearly separate finalized models from exploratory experiments.
```text
CrisisLens/
├── notebooks/
│   ├── CrisisLens_V1_TFIDF_LogReg.ipynb
│   ├── CrisisLens_V2_DistilBERT.ipynb
│
├── experiments/
│   └── CrisisMapping_Prototype.ipynb
│
├── results/
│   └── metrics.txt
│
├── data/
│   └── README.md
│
├── requirements.txt
└── README.md
```
## CrisisLens V1 - TF-IDF + Logistic Regression
### Approach
* Text vectorization using TF-IDF
* Binary classification using Logistic Regression
* Implemented via a scikit-learn pipeline
### Why this baseline?
* Interpretable and efficient
* Well-suited for short text classification
* Establishes a strong reference point for improvement
### Observed Limitations
* No understanding of semantic context
* Keyword-based errors in ambiguous sentences
* Synonyms treated as unrelated features
## CrisisLens V2 — DistilBERT (Transformer Model)
### Approach
* Fine-tuned DistilBERT (distilbert-base-uncased)
* Tokenization and training using HuggingFace Transformers
* Evaluation using Accuracy and F1-score
### Why DistilBERT?
* Captures contextual and semantic meaning
* Handles ambiguity better than frequency-based methods
* Lightweight compared to full BERT while retaining performance
### Improvements over V1
* Better understanding of sentence-level context
* Reduced false positives caused by keyword overlap
* More robust performance on nuanced distress expressions
## Results (Indicative)
| Model                        | Metric Type  |
| ---------------------------- | ------------ |
| TF-IDF + Logistic Regression | Accuracy, F1 |
| DistilBERT                   | Accuracy, F1 |

Exact metrics depend on dataset split and training configuration and can be reproduced using the provided notebooks.
## Exploratory Prototype (Experiments)
An early exploratory notebook investigates:
* Urgency estimation using sentiment scores
* Keyword-based urgency boosting
* Geolocation and visualization of reports using Folium
This prototype was created to explore downstream applications (e.g., prioritization and visualization) and is not part of the final classification pipeline.
## Future Work
* Handling class imbalance using advanced techniques
* Domain-specific fine-tuning on crisis-focused corpora
* Multilingual distress detection
* Model interpretability and explainability
* Deployment as a real-time inference API
## Tech Stack
* __Languages:__ Python
* __ML / NLP:__ scikit-learn, HuggingFace Transformers, PyTorch
* __Data Processing:__ Pandas, NumPy
* __Experimentation:__ Google Colab
## Dataset
The dataset consists of labeled social media text indicating whether a message represents distress.
Details and source information are documented in data/README.md.
## Key Takeaways
* Demonstrates a __baseline → transformer ML workflow__
* Emphasizes understanding of model behavior and limitations
* Focuses on real-world relevance, not just model performance
* Built with clarity, reproducibility, and learning in mind
