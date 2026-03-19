# Error Analysis

## Overview

To understand model limitations, a validation split was created and misclassified examples were analyzed. Around multiple failure cases were observed, highlighting the challenges of working with noisy, real-world emotional data.

---

## Key Failure Patterns

### 1. Semantic Misinterpretation of Text

The model sometimes failed to correctly interpret the emotional tone of the text. For example, reflections indicating calmness or relief were predicted as restless or negative states.

**Reason:**
TF-IDF captures word frequency but lacks deep contextual understanding.

---

### 2. Ambiguous or Mixed Emotions

Some journal entries contained mixed emotional signals, making it difficult to assign a single label.

**Example:**
Text expressing both relaxation and lingering tension.

---

### 3. Conflicting Signals Between Text and Metadata

In several cases, metadata (such as high stress or low energy) contradicted the journal text.

**Example:**
Text suggests calmness, but stress level is high.

**Impact:**
The model struggles to decide which signal to prioritize.

---

### 4. Label Noise and Inconsistency

Some labels appear inconsistent with the input text.

**Example:**
Text indicating uneasiness labeled as "calm".

**Impact:**
This introduces confusion during training and reduces prediction reliability.

---

### 5. Weak or Low-Quality Reflections

Short or vague inputs provide insufficient information for accurate prediction.

**Example:**
"ok", "fine", or very short reflections.

---

## Example Failure Cases

### Case 1

* Text: "after the forest track i feel peaceful and less pulled in every direction"
* Actual: focused
* Predicted: restless

### Case 2

* Text: "I still feel unsettled and fidgety"
* Actual: calm
* Predicted: overwhelmed

---

## Key Insights

* Text alone is not reliable due to ambiguity and noise
* Metadata plays an important supporting role
* Label quality significantly affects performance
* Confidence-based uncertainty helps identify unreliable predictions

---

## Suggested Improvements

* Use contextual embeddings (e.g., BERT) for better semantic understanding
* Apply noise-robust training techniques
* Introduce weighted fusion between text and metadata
* Improve uncertainty calibration
* Use ensemble methods for better generalization

---
