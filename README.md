SRTOMACH TUMOUR DETECTION USING CNN + DEEP Q-LEARNING (DQN)

This project presents a hybrid Deep Learning + Reinforcement Learning approach for detecting stomach tumors from endoscopic images.
A CNN model (MobileNetV2) is used to extract high-level features from images, and a Deep Q-Network (DQN) learns to classify them as:
 - Tumor
 - Non-Tumor
The DQN agent is trained using a custom medical-focused reward system, enabling it to prioritize saving patients' lives by minimizing missed tumors (false negatives).
Dataset

SOURCE: Kaggle – Endoscopic Stomach Tumor Dataset
Two classes:
 - Tumor
 - Non-Tumor
All images were:
 - Resized (224×224)
 - Normalized
 - Augmented (rotation, zoom, flips)
Stratified split ensured balanced training and testing sets.

MODEL ARCHITECTURE:
1️) CNN Feature Extractor
Backbone: MobileNetV2 (pretrained on ImageNet)
Output: Feature vector for each image
Purpose: Reduce complexity & improve learning efficiency

2️) Deep Q-Network (DQN) Classifier
Input: CNN feature vector
Output: Action (0 = Non-Tumor, 1 = Tumor)
Fully connected layers with ReLU activations

REWARD SYSTEM (Medical-Sensitive)

To reduce the risk of missing a tumor:
Outcome	Reward
 True Positive	+5
 True Negative	+2
 False Positive	–3
 False Negative	–10
False negatives are heavily penalized because missing a tumor is medically dangerous.

RESULTS
✔ CNN Performance
~96% accuracy

Clean separation of classes
Balanced confusion matrix

✔ DQN Agent Performance
Gradually increased rewards during training

Final test accuracy: ~93–95%
Confusion matrix shows very low false negatives → primary project goal achieved

KEY FEATURES :
 - CNN for feature extraction
 - Reinforcement learning-based medical classification
 - Custom reward shaping for real medical priorities
 - Confusion matrix + training visualization
 - End-to-end automated tumor detection pipeline
