# Hybrid Candidate Ranking System

## Overview

This project implements a hybrid candidate ranking system that recommends the most relevant candidates for a given job description by combining rule-based scoring with TF-IDF semantic similarity.

The objective is to rank a large pool of candidates according to their relevance and generate the Top 100 recommendations along with reasoning for each recommendation.

---

## Methodology

The ranking pipeline combines multiple signals:

### 1. Skill Matching

* Domain-specific skill weights
* Proficiency level
* Experience duration
* Endorsements

### 2. Career Title Matching

Rewards titles closely aligned with the target role.

### 3. Profile Description Matching

Detects relevant technologies and responsibilities from candidate descriptions.

### 4. Semantic Similarity

* TF-IDF vectorization converts the job description and candidate profiles into vector representations.
* Cosine similarity measures semantic relevance between the job description and each candidate.

### 5. Penalty System

Applies penalties to candidates from clearly irrelevant domains (for example accounting or HR) to reduce false positives.

The final score is computed by combining these components and ranking candidates in descending order.

---

## Pipeline

```text
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

## Project Structure

```text
candidate-ranking-system/

├── README.md
├── requirements.txt
├── main.ipynb
├── submission.csv
├── submission_metadata.yaml
├── sample_candidates.json
```

---

## Input

The system expects candidate data in JSON/JSONL format containing:

* candidate_id
* profile
* career_history
* education
* skills
* certifications
* languages
* redrob_signals

---

## Technologies Used

* Python
* Scikit-learn
* TF-IDF Vectorizer
* Cosine Similarity

---

## Running the Project

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

### 2. Run the notebook

Open:

```text
main.ipynb
```

Execute all cells from top to bottom.

### 3. Output

The notebook generates:

```text
submission.csv
```

---

## Output Format

The generated submission contains:

* rank
* candidate_id
* score
* reasoning

---

## Demo Sandbox

Google Colab notebook:

https://colab.research.google.com/drive/1lf3jRvbo4RPEPV7pPDSWUpJGG8gg0hFp?usp=sharing

---

## Design Goals

* Interpretable ranking
* Hybrid rule-based + semantic matching
* Reproducible pipeline
* Efficient processing of large candidate pools
