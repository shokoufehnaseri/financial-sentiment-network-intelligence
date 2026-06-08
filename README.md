# Influence-Aware Financial Sentiment Analysis and Stock Trend Prediction

A large-scale financial market intelligence framework that combines Financial Natural Language Processing (NLP), Social Network Analysis, and Machine Learning to predict stock market trends from social media data.

This project was developed as part of a Master's thesis in Data Science and investigates how investor sentiment extracted from Twitter can be enhanced through user influence modeling and integrated with historical market data for stock trend prediction.

---

## Overview

Financial markets are increasingly influenced by information disseminated through social media platforms. However, not all opinions contribute equally to market dynamics. This project proposes an influence-aware sentiment analysis framework that combines:

* Financial sentiment extraction using FinBERT
* Weak supervision and human-annotated fine-tuning
* Large-scale sentiment inference on millions of tweets
* Twitter user influence modeling using PageRank
* Historical stock market data integration
* Machine learning and ensemble learning for trend prediction
* Explainable AI using SHAP

The framework processes more than 3.6 million stock-related tweets and evaluates whether influence-weighted sentiment provides additional predictive power for stock market forecasting.

---

## Research Contributions

### Financial NLP Pipeline

* Financial tweet preprocessing and normalization
* Weak-label generation using VADER
* Two-stage FinBERT fine-tuning
* Large-scale sentiment classification

### Influence-Aware Sentiment Modeling

* Construction of Twitter interaction networks
* User influence estimation using PageRank
* Sentiment weighting based on user influence

### Stock Market Prediction

* Integration of sentiment signals with historical stock data
* Feature engineering for financial forecasting
* Comparison of multiple machine learning models
* Statistical significance testing
* SHAP-based explainability analysis

---

## Methodology

### Stage 1 — Data Collection

Two major data sources were used:

#### Financial Tweet Datasets

* Labeled financial tweets
* Unlabeled financial tweets

#### Market Intelligence Dataset

* Company-related tweets (~4 million tweets)
* Company metadata
* Historical stock prices

---

### Stage 2 — Tweet Preprocessing

Financial tweets were cleaned and normalized using a custom preprocessing pipeline:

* URL removal
* Mention removal
* Hashtag normalization
* Emoji removal
* Financial abbreviation expansion
* Text normalization
* Stopword filtering

---

### Stage 3 — Two-Stage FinBERT Fine-Tuning

#### Step 1: Weak Supervision

Base FinBERT was first fine-tuned using sentiment labels generated automatically through VADER.

Result:

**FinBERT-Weak**

#### Step 2: Human-Labeled Refinement

The FinBERT-Weak model was subsequently fine-tuned using manually annotated sentiment labels.

Result:

**FinBERT-Gold**

The final FinBERT-Gold model was selected for large-scale sentiment inference.

---

### Stage 4 — Large-Scale Sentiment Inference

The final FinBERT-Gold model was applied to approximately 3.6 million stock-related tweets.

Due to dataset size, tweets were divided into 20 chunks and processed independently.

Outputs:

* Positive sentiment
* Neutral sentiment
* Negative sentiment

---

### Stage 5 — User Influence Modeling

A Twitter interaction network was constructed.

PageRank was used to estimate user influence scores.

Influence-weighted sentiment was computed as:

Weighted Sentiment = Sentiment × User Influence Score

This produced an influence-aware sentiment signal.

---

### Stage 6 — Dataset Construction

The following information sources were merged:

* Historical stock prices
* Predicted sentiment
* Influence-weighted sentiment
* Company information

The resulting dataset was used for stock trend prediction.

---

### Stage 7 — Stock Trend Prediction

Several machine learning models were evaluated:

* Logistic Regression
* Support Vector Machine (SVM)
* Random Forest
* Multi-Layer Perceptron (MLP)
* XGBoost
* LightGBM
* CatBoost
* Ensemble Models

---

### Stage 8 — Explainability

Model behavior was analyzed using:

* SHAP values
* Feature importance analysis
* Statistical significance testing

---

## Repository Structure

```text
.
├── data
│   ├── raw
│   ├── processed
│   ├── intermediate
│   └── final
│
├── notebooks
│   ├── 01_prepare_labeled_tweets.ipynb
│   ├── 02_prepare_unlabeled_tweets.ipynb
│   ├── 03_prepare_company_tweets.ipynb
│   ├── 04_finetune_finbert_weak$gold.ipynb
│   ├── 05_split_large_dataset_into_chunks.ipynb
│   ├── 06_large_scale_sentiment_inference.ipynb
│   ├── 07_pagerank_network_analysis.ipynb
│   ├── 08_build_prediction_dataset.ipynb
│   └── 09_stock_trend_prediction_final.ipynb
│
│
├── src
│   └── preprocess_tweet.py
│
├── models
│   ├── finbert_final_finetuned
│   ├── finbert_weak_finetuned
│   ├── results_weak
│   └── results_gold
│
├── figures
│
├── .gitignore
│
└── README.md
```

---

## Technologies

### NLP

* FinBERT
* Hugging Face Transformers
* VADER

### Machine Learning

* Scikit-learn
* XGBoost
* LightGBM
* CatBoost

### Network Analysis

* NetworkX
* PageRank

### Explainable AI

* SHAP

### Data Processing

* Pandas
* NumPy

### Visualization

* Matplotlib
* Seaborn

---

## Results

The project demonstrates that combining:

* Financial sentiment analysis
* Social influence modeling
* Historical market information

can improve stock trend prediction compared to using sentiment or price information alone.

Furthermore, influence-weighted sentiment provides additional information beyond conventional sentiment aggregation.

---

## Author

Shokoufeh Naseri

M.Sc. Data Science
University of Warsaw

M.Sc. Applied Mathematics

Research Interests:

* Natural Language Processing
* Financial AI
* Explainable AI
* Machine Learning
* Data Mining
* Social Network Analysis
