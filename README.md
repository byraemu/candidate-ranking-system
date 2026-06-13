
# Hybrid Candidate Ranking System

## Overview

This project implements a **hybrid candidate ranking system** that recommends the most relevant candidates for a given job description by combining **rule-based scoring** with **TF-IDF semantic similarity**.

The objective is to rank a large pool of candidates according to their relevance and generate the **Top 100 recommendations** along with reasoning for each recommendation.

---

# Methodology

The ranking pipeline combines multiple signals:

* **Skill Matching**

  * Domain-specific skill weights
  * Proficiency level
  * Experience duration
  * Endorsements

* **Career Title Matching**

  * Rewards titles closely aligned with the target role.

* **Profile Description Matching**

  * Detects relevant technologies and responsibilities from candidate descriptions.

* **Semantic Similarity**

  * TF-IDF vectorization converts the job description and candidate profiles into vector representations.
  * Cosine similarity measures semantic relevance between the job description and each candidate.

* **Penalty System**

  * Applies penalties to candidates from clearly irrelevant domains (for example accounting or HR) to reduce false positives.

The final score is computed by combining these components and ranking candidates in descending order.

---

# Pipeline

```
Job Description
        │
        ▼
Candidate Feature Extraction
        │
        ▼
Rule-based Scoring
        │
        ▼
TF-IDF Semantic Similarity
        │
        ▼
Penalty Adjustment
        │
        ▼
Final Score
        │
        ▼
Ranked Candidates
        │
        ▼
submission.csv
```

---

# Project Structure

```
candidate-ranking-system/

├── README.md
├── requirements.txt
├── main.ipynb
├── submission.csv
├── submission_metadata.yaml

├── data/
│     └── sample_candidates.json
```

---

# Technologies Used

* Python
* Scikit-learn
* TF-IDF Vectorizer
* Cosine Similarity

---

# Running the Project

1. Install dependencies

```
pip install -r requirements.txt
```

2. Open and execute

```
main.ipynb
```

3. The notebook generates the ranked output:

```
submission.csv
```

---

# Output Format

The generated submission contains:

* Rank
* Candidate ID
* Score
* Reasoning

---
## Demo Sandbox

Google Colab notebook:
(https://colab.research.google.com/drive/1lf3jRvbo4RPEPV7pPDSWUpJGG8gg0hFp?usp=sharing)

---
# Design Goals

* Interpretable ranking
* Hybrid rule-based + semantic matching
* Reproducible pipeline
* Efficient processing of large candidate pools

---

# Future Improvements

* Sentence Transformer embeddings
* Learning-to-Rank models
* Dynamic skill weighting
* Feedback-driven ranking optimization

