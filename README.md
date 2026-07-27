# Desibait: Detecting Engagement Bait Comments on South Asian Youtube

## Problem Statement

Engagement bait comments—like "Legends watching in 2026", "Maa ki lambi umar ke liye like karo", and "5 minute wali gang?" flood YouTube comment sections. While not harmful like spam, these comments drown out genuine feedback, questions, and discussions. The existing "Top" and "Newest" filters fail to detect them, making it difficult for creators and audiences to find meaningful engagement.
This project builds a system to detect engagement bait in South Asian YouTube comments, with a focus on **Hinglish** (Hindi written in Latin script), a major challenge for existing English-centric filters.

## Dataset

- **576 labeled comments** from South Asian YouTube videos
- English, Hinglish, and code‑mixed text
- Labels: **0 (genuine)** and **1 (bait)**

## Approach

### Phase 1: Rule‑Based Baseline
- Regex patterns derived from frequency analysis (unigrams, bigrams, trigrams)
- 25+ patterns targeting direct requests, identity/group bait, temporal bait, religious/emotional bait.

### Phase 2: Machine Learning
- Logistic Regression with TF‑IDF features
- Custom stopword list combining English and Hinglish stopwords
- 80/20 train‑test split with stratification

## Results

| Metric | Phase 1 | Phase 2 |
|--------|---------|---------|
| Accuracy | 82.3% | **84.5%** |
| Precision | 87.9% | **90.2%** |
| Recall | 69.0% | **72.5%** |
| F1 | 77.3% | **80.4%** |

**ML improved recall by 3.5%.**

## Challenges Faced

- **Data scarcity** - limited Hinglish engagement bait examples
- **Handling Implicit Bait** - applying Pragmatics principles
- **Imbalanced dataset** - addressed through augmentation
- **Label ambiguity** - documented clear criteria for edge cases
- **Hinglish stopwords** - built a custom stopword list from data

## Novelty

To the best of my knowledge, this is the **first systematic attempt to detect engagement bait in Hinglish YouTube comments**. While existing work has focused on spam detection or English‑centric bait, the **transliterated Hindi (Roman-script Hinglish)** present in South Asian YouTube comment sections presents unique challenges that this project addresses.

## Future Work

- Expand the dataset to 2,000+ comments for Deep Learning approaches
- Explore language‑adapted models (like HingRoBERTa)

## Acknowledgements

The data augmentation strategy is based on the **EDA (Easy Data Augmentation)** framework proposed by Wei and Zou (2019):

> Wei, J., & Zou, K. (2019). *EDA: Easy Data Augmentation Techniques for Boosting Performance on Text Classification Tasks.* Proceedings of the 2019 Conference on Empirical Methods in Natural Language Processing and the 9th International Joint Conference on Natural Language Processing (EMNLP-IJCNLP), 6382–6388.


## Files

- `desibait.ipynb` — Full project notebook
- `dataset_final.csv` — Labeled dataset
- `requirements.txt` — Python dependencies
