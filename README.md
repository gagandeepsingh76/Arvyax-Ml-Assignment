# ArvyaX Machine Learning Assignment

## Overview

This project presents an end-to-end machine learning system designed to understand human emotional states from noisy, real-world inputs and provide meaningful, actionable guidance.

Unlike traditional classification tasks, this system focuses on:

* Handling messy and ambiguous text
* Integrating contextual signals
* Making decisions (what to do and when)
* Managing uncertainty in predictions

---

## Problem Approach

The system is structured into four key layers:

### 1. Emotional Understanding

A machine learning model predicts:

* Emotional state (classification)
* Intensity (1–5 scale, treated as regression)

Textual reflections are converted into features using TF-IDF, and combined with contextual metadata such as sleep, stress, energy, and time of day.

---

### 2. Decision Engine (What + When)

A rule-based decision layer converts predictions into actionable recommendations.

Examples:

* High stress + low energy → rest (now)
* High energy + morning → deep work (now)
* Moderate stress → breathing (within 15 min)

This ensures the system moves beyond prediction to real-world guidance.

---

### 3. Uncertainty Modeling

Each prediction includes:

* Confidence score (based on model probability)
* Uncertainty flag (triggered when confidence < 0.6)

This allows the system to acknowledge when it is unsure, improving reliability.

---

### 4. Robustness Handling

The system is designed to handle:

* Short or vague inputs
* Missing values
* Conflicting signals between text and metadata

---

## Feature Engineering

### Text Features

* TF-IDF vectorization (max 300 features)

### Metadata Features

* Stress level
* Energy level
* Sleep hours
* Time of day
* Previous mood
* Reflection quality
* Face emotion hint

Categorical features were encoded using Label Encoding, and missing values were handled using median (numerical) and "unknown" (categorical).

---

## Model Choice

* Random Forest Classifier for emotional state
* Random Forest Regressor for intensity

Reason:

* Handles mixed data types well
* Robust to noise
* Works effectively without heavy tuning

---

## Ablation Insight

Two approaches were considered:

* Text-only model
* Text + metadata model

The combined approach performed better due to the noisy nature of textual data, where contextual signals provided additional clarity.

---
## Repository Structure

```
arvyax-ml-assignment/
│
├── arvyax_ml_pipeline.ipynb    # End-to-end ML pipeline
├── predictions.csv             # Final output predictions
├── README.md                   # Project overview and approach
├── ERROR_ANALYSIS.md           # Analysis of model failures
├── EDGE_PLAN.md                # Deployment and edge considerations
```



## Output

The final output includes:

* predicted_state
* predicted_intensity
* confidence
* uncertain_flag
* what_to_do
* when_to_do

All results are stored in `predictions.csv`.

---

## How to Run

1. Open the notebook `arvyax_ml_pipeline.ipynb`
2. Upload the training and test datasets
3. Run all cells sequentially
4. The final predictions will be saved as `predictions.csv`

---

## Key Highlights

* End-to-end pipeline from raw input to actionable output
* Combines ML with decision logic
* Handles uncertainty explicitly
* Designed with real-world constraints in mind

---

## Future Improvements

* Use contextual embeddings (BERT) for better text understanding
* Improve handling of conflicting signals
* Enhance decision engine with learned policies
* Deploy lightweight version for on-device inference

---
