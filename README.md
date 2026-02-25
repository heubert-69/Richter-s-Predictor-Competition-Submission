🏗 Earthquake Damage Grade Prediction

🌍 Overview

This project predicts building damage grades after an earthquake using supervised machine learning.

The objective is to classify buildings into ordinal damage levels (e.g., low, medium, high damage) using structural, geographic, and socio-economic features.

Given the humanitarian impact of disaster response, the modeling approach emphasizes:

Robust cross-validation

Probabilistic calibration

Ensemble learning

Ethical reliability (minimizing misclassification risk)


🎯 Problem Type

Task: Multiclass Classification (Ordinal Target)

Evaluation Metric: Quadratic Weighted Kappa (QWK)

Classes: 3 damage levels


🧠 Modeling Strategy
1️⃣ Validation Strategy

We use:

StratifiedKFold (5 splits)

Out-of-Fold (OOF) predictions

Averaged test-time predictions

This ensures:

Balanced class representation per fold

Reduced variance

Reliable generalization estimation


2️⃣ Models Used

The ensemble includes:

Logistic Regression

Random Forest

Gradient Boosting

Multilayer Perceptron

XGBoost

LightGBM

Special handling:

XGBoost and LightGBM use zero-based labels for compatibility.


3️⃣ Softmax Probability Ensemble

Instead of hard voting, we combine probability outputs:

𝑃𝑓𝑖𝑛𝑎𝑙 = ∑ 𝑤𝑖 ⋅ 𝑃𝑖

	​
Where:

𝑃𝑖 = model probability output

𝑤𝑖 = optimized model weight


Final prediction:

argmax(P_final)


This improves:

Calibration

Stability

Leaderboard robustness


🧪 Key Engineering Decisions

Zero-based label adjustment for boosting models

Out-of-fold prediction storage

Averaged test-time inference

Weighted probability ensemble

Clean submission alignment (no row mismatch)


🤝 Ethical Considerations

Earthquake damage modeling affects:

Resource allocation

Emergency response prioritization

Human safety

Therefore:

Overfitting was strictly controlled

Cross-validation integrity preserved

No data leakage tolerated



🚀 Future Improvements

Ordinal regression approaches

Stacking meta-learner

Regime-aware CV grouping

Probability calibration (Platt / Isotonic)

Bayesian ensembling

Geospatial feature engineering
