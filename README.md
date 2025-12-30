# Multi-Modal Stacked Ensemble for Diabetic Retinopathy Grading with XAI

This repository contains a state-of-the-art framework for Diabetic Retinopathy (DR) grading. The project moves beyond traditional image-only classification by integrating retinal fundus images with clinical patient metadata (HbA1c, Age, etc.) using a Multi-Modal Stacked Ensemble architecture. To ensure clinical trust, the system incorporates Explainable AI (XAI) techniques like Grad-CAM and SHAP.


# 🌟 Key Features
# Multi-Modal Data Fusion: Combines visual features from fundus images with clinical indicators (HbA1c, SBP, Diabetes Duration, Age).

Stacked Ensemble Learning: Utilizes a "committee" of 5 diverse base learners (CNNs and MLPs) whose outputs are optimized by an XGBoost meta-learner.

Explainable AI (XAI): * Grad-CAM: Visual heatmaps to identify retinal lesions (exudates, hemorrhages).

SHAP: Quantifies the impact of clinical metadata versus visual features on the final diagnosis.

Production-Ready Pipeline: Includes Early Stopping, Learning Rate Scheduling, and Stratified K-Fold validation.

# 🏗️ Architecture Overview
# The system operates in three distinct stages:

Feature Extraction (Base Learners): Five models process the data in parallel:

EfficientNet-B0 & EfficientNet-B3: Image-only experts.

FusionModel (ResNet50 + MLP): Combined image and metadata expert.

MetaFCNN: Tabular data expert.

CustomCNN: Structural diversity baseline.

The Stack (Meta-Learner): An XGBoost model trained on the Out-of-Fold (OOF) predictions from the base learners to produce the final DR grade (0-4).

Explanation: Post-hoc analysis using Grad-CAM and SHAP values for clinical validation.
