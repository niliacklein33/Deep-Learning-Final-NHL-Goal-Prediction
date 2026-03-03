# Predicting NHL Goal Probability Using Spatial Deep Learning

## Overview

This project compares machine learning models to predict whether an NHL shot results in a goal using spatial shot data.

The central question is:

Can a convolutional neural network (CNN) learn goal probability from spatial structure more effectively than traditional engineered-feature models?

Using NHL shot-level event data (2020–2025 seasons), I evaluate logistic regression, a multilayer perceptron (MLP), and a spatial CNN under a time-based train/test split.


---

## Dataset

- Source: Kaggle NHL clean shots dataset  
- ~500,000 shot attempts  
- Features: shot coordinates, event type, game metadata  
- Target: binary goal outcome (~7% positive rate)

All shots were normalized so teams attack the same net to preserve spatial consistency.

---

## Models

**Logistic Regression**  
Uses engineered features (distance and angle).

**MLP (Neural Network)**  
Adds nonlinear feature interactions.

**Spatial CNN (3-channel)**  
Treats the rink as a 2D grid and learns spatial scoring patterns directly.

---

## Results

| Model | ROC-AUC | PR-AUC |
|-------|---------|--------|
| Logistic Regression | ~0.71 | ~0.14 |
| MLP | ~0.716 | ~0.147 |
| CNN (3-channel) | ~0.717 | ~0.152 |

Because goals are rare, PR-AUC is prioritized.

The final selected model is a moderately sized 3-channel CNN with tuned learning rate.

---

## Key Insights

- Distance and angle capture strong predictive signal.
- CNN provides incremental gains by modeling spatial geometry.
- Representation design had more impact than increasing network depth.
- Performance is constrained by missing contextual features.

---

## Repository Contents

- `notebook.ipynb` – Full analysis and modeling
- `presentation.pptx` – Project slides
- `video_presentation.mp4` – Recorded walkthrough
