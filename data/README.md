# Dataset Description - CrisisLens

This directory contains the datasets used for training and evaluating
the CrisisLens distress tweet classification models.


## Files

- `train.csv`  
  Labeled dataset used for training and validation.

- `test.csv`  
  Unlabeled dataset used for inference.


## Data Schema

### train.csv

| Column Name | Description |
|------------|------------|
| id | Unique identifier for each tweet |
| keyword | Disaster-related keyword associated with the tweet (may be missing) |
| location | Location mentioned in the tweet (may be missing or noisy) |
| text | Raw tweet text |
| target | Binary label indicating distress |
| | 0 → Not a distress-related tweet |
| | 1 → Distress-related tweet |

### test.csv

| Column Name | Description |
|------------|------------|
| id | Unique identifier for each tweet |
| keyword | Disaster-related keyword |
| location | Location mentioned in the tweet |
| text | Raw tweet text |


## Task Definition

The objective is to classify whether a given tweet expresses
**distress or crisis-related information**, such as:
- Natural disasters
- Infrastructure damage
- Medical emergencies
- Requests for urgent assistance

This is formulated as a **binary text classification problem**.


## Feature Usage

- Only the `text` column is used for model training.
- `keyword` and `location` are retained for potential future extensions
  (e.g., geospatial analysis, metadata-based modeling).


## Preprocessing Notes

- Minimal preprocessing is applied to preserve semantic meaning.
- No manual feature engineering is performed.
- Text representation is handled by:
  - TF-IDF vectorization (CrisisLens V1)
  - DistilBERT tokenizer (CrisisLens V2)


## Ethical Considerations

This dataset contains distress-related and sensitive content.
Model predictions are probabilistic and should **not** be treated as
definitive assessments.

The system is intended to assist analysis, not replace human judgment.


## Usage Disclaimer

This dataset is used strictly for academic and research purposes.
Any real-world deployment would require rigorous validation
and human oversight.

