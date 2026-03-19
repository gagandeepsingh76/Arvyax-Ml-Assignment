# Edge Deployment Plan

## Overview

This section outlines how the proposed system can be deployed efficiently in real-world environments, particularly on mobile or edge devices with limited computational resources.

---

## Deployment Approach

The system can be structured into two components:

### 1. On-Device Inference

* Lightweight model for emotional state prediction
* Basic preprocessing (text cleaning, feature extraction)
* Decision engine logic (rule-based)

### 2. Optional Server Support

* Used for model updates or improvement
* Not required for real-time predictions

---

## Model Optimization

To enable efficient on-device execution:

* Replace Random Forest with a lightweight model (e.g., Logistic Regression or small Gradient Boosting model)
* Reduce TF-IDF feature size (e.g., from 300 to 100 features)
* Use model compression techniques such as:

  * Quantization
  * Pruning

---

## Latency Considerations

* TF-IDF vectorization is fast and suitable for real-time inference
* Prediction time is expected to be under a few milliseconds on modern devices
* Rule-based decision engine adds negligible overhead

---

## Memory Constraints

* Keep model size small (<10 MB preferred)
* Limit vocabulary size for TF-IDF
* Avoid large embedding models unless optimized

---

## Offline Capability

The system is designed to work fully offline:

* No dependency on external APIs
* All predictions and decisions handled locally
* Ensures privacy and reliability in low-connectivity environments

---

## Trade-offs

| Aspect             | Trade-off                                        |
| ------------------ | ------------------------------------------------ |
| Model Complexity   | Simpler models may reduce accuracy               |
| Speed vs Accuracy  | Faster inference may slightly impact performance |
| Memory vs Features | Smaller models require fewer features            |

---

## Handling Edge Cases

### 1. Very Short Text

* Rely more on metadata (stress, energy, time)

### 2. Missing Values

* Use default or median-based imputation

### 3. Conflicting Signals

* Combine text and metadata using weighted logic

### 4. Low Confidence Predictions

* Use uncertainty flag to trigger safer recommendations (e.g., rest or pause)

---

## Future Improvements

* Use lightweight transformer models (e.g., DistilBERT) for better text understanding
* Implement on-device personalization
* Add feedback loop to improve model over time
* Convert model to ONNX for optimized inference

---

## Conclusion

The system is designed to be lightweight, fast, and reliable, making it suitable for deployment on mobile and edge devices while maintaining reasonable performance and robustness.
