Quora Duplicate Question Detector
---

## Table of Contents
1. [Project Overview](#project-overview)
2. [Features](#features)
3. [Dataset](#dataset)
4. [Project Structure](#project-structure)
5. [Installation](#installation)
6. [Usage](#usage)
7. [Command-line Arguments](#command-line-arguments)
8. [Output](#output)
9. [Example Prediction](#example-prediction)
10. [Future Improvements](#future-improvements)
11. [License](#license)
12. [Acknowledgements](#acknowledgements)

---

## Project Overview
Duplicate question detection is a key challenge in community-driven Q&A platforms like Quora, Stack Overflow, and Reddit.  
When duplicate questions are posted, they fragment the knowledge base and create redundant answers.  
This project replicates the **Quora Question Pairs** competition on Kaggle using a clean, reproducible Python pipeline.

## Main steps:
1. **Preprocessing**: Normalize and clean text.
2. **Feature Engineering**: Create numeric features from tokens and fuzzy matching scores.
3. **Vectorization**: Represent text using TF-IDF with unigrams and bigrams.
4. **Model Training**: Fit a Logistic Regression classifier with balanced class weights.
5. **Evaluation**: Measure performance using ROC-AUC, accuracy, and classification reports.

---

## Features
- **Custom Preprocessing**:
  - Lowercasing, punctuation removal, contraction expansion.
  - Stemming for basic word normalization.
- **Token-level Features**:
  - Common non-stopword ratios.
  - Stopword overlaps.
  - First/last word matches.
  - Absolute and average token length differences.
- **Fuzzy String Features**:
  - Fuzzy ratio, partial ratio.
  - Token sort ratio, token set ratio (optional, requires `fuzzywuzzy`).
- **TF-IDF Representation**:
  - Characterizes semantic similarity using statistical text features.
  - Up to 30,000 features with unigrams and bigrams.
- **Logistic Regression Classifier**:
  - Trained with `class_weight="balanced"` to address dataset imbalance.
- **Caching**:
  - Optional Parquet feature cache to avoid recomputation.

---

## Dataset
- **Source**: [Quora Question Pairs - Kaggle](https://www.kaggle.com/c/quora-question-pairs)
- **Format**:
  - CSV with columns: `id`, `qid1`, `qid2`, `question1`, `question2`, `is_duplicate`
- **Size**:
  - ~400,000 question pairs
  - Target variable: `is_duplicate` (1 = duplicate, 0 = not duplicate)

---


