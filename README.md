---
title: NLPDisasterTweets
emoji: 🚨
colorFrom: red
colorTo: gray
sdk: docker
app_port: 8501
tags:
- streamlit
pinned: false
short_description: App to classify tweets as real disasters (1) or non-disaster
license: mit
---

# 🚨 Disaster Tweet Classifier (TF-IDF + Logistic Regression)

This app classifies tweets as **Disaster (1)** or **Non-Disaster (0)**.

## What this project does
Many tweets contain disaster-related words but do not describe real disasters.  
This project trains a classical NLP model to detect real disaster tweets.

## Model
- **Text features:** TF-IDF (unigrams + bigrams)
- **Classifier:** Logistic Regression
- **Metric:** F1-score
- **Threshold tuning:** optimized on validation set (**threshold = 0.43**)
- Best validation F1-score: **~0.78**

## Files in this repo
Place these files in the repository root:
- `app.py`
- `final_clf.pkl` (trained pipeline: TF-IDF + Logistic Regression)
- `threshold.pkl` (float threshold, e.g. 0.43)
- `requirements.txt`

## How to run locally
```bash
pip install -r requirements.txt
streamlit run app.py
How the prediction works
User enters tweet text (optional: keyword and location)

The app builds full_text using:

text + [KEY] keyword + [LOC] location

The same cleaning rules are applied

The model outputs a probability

The final label is computed using the saved threshold

Notes
This is a classical ML baseline (fast + strong).

The same artifacts can be reused in any deployment setting.