# CSE440 NLP Project Outline and EDA Summary

## What the project requires
- Extensive EDA
- Three preprocessing variants: no preprocessing, extreme preprocessing, optimum preprocessing
- TF-IDF with one ML model and one deep neural network
- Skip-gram with SimpleRNN, GRU, LSTM, Bidirectional SimpleRNN, Bidirectional GRU, and Bidirectional LSTM
- Accuracy, macro F1, confusion matrix, and classification report
- Best-vs-worst comparison and full report justification

## What I found in your dataset
- Train rows: 104,763
- Test rows: 12,000
- Missing text/labels: 0 in both splits
- Train class distribution: {'Science and Technology': 34.77, 'Sports': 32.62, 'Business': 17.72, 'World News': 14.89}
- Test class distribution: {'Science and Technology': 25.0, 'World News': 25.0, 'Business': 25.0, 'Sports': 25.0}
- Exact duplicate train rows: 31,208
- Exact duplicate test rows: 0
- HTML wrappers present: 100.00% of train rows
- Broken entities present: 32.16% of train rows
- Backslash artifacts present: 10.48% of train rows
- Average cleaned text length: 38.38 words, 229.42 characters

## Recommended optimum preprocessing
- remove HTML
- remove `News Headlines:` prefix
- normalize broken entities
- fix backslash artifacts
- lowercase
- remove Reuters/AP/AFP source tags
- keep numbers
- keep most stopwords
- do not stem

## Extra recommendation
Because Science and Technology and Sports contain many exact duplicate training texts, run one additional experiment with a deduplicated training set and compare validation macro F1.