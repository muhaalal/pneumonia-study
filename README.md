# Exploring Failure Modes of CNNs in Chest X-Ray Pneumonia Classification

## Overview
This project investigates the limitations and failure modes of convolutional neural networks (CNNs) in medical imaging. Rather than focusing solely on diagnostic performance, this study analyzes where and why a CNN misclassifies chest X-rays in pneumonia detection.

## Motivation
Deep learning models are increasingly being applied in medical imaging. However, false positives and false negatives carry critical clinical risk. Understanding model limitations is critical before deployment into the real world. This project explores model limitations rather than raw accuracy.

## Dataset
- Public Chest X-Ray Pneumonia Dataset (Kaggle)
- Binary classification: NORMAL vs PNEUMONIA
- Predefined train/validation split
- 5,000+ images

## Model
- Architecture: ResNet18
- Transfer learning (pretrained on ImageNet)
- Implemented using FastAI (built on PyTorch)
- Fine-tuned for 5 epochs
- Input resolution: 224×224


## Results
The model achieved a validation accuracy of 87.5%, with zero false negatives but two false positives.

### Figure 1: Confusion Matrix
Confusion matrix summarizing model performence on the validation set, showing true positives, true negatives, false positives, and false negatives for pneumonia classification.

## Failure Analysis
Rather then focusing on accuracy and further optimizing the model, the study focused on the misclassifed examples.

### Figure 2: False Positive #1
Pediatric chest X-ray incorrectly classified as pneumonia. Motion blur, low contrast, and pediatric anatomy likely contributed to the error.

### Figure 3: False Positive #2
Pediatric chest X-ray falsely classified as pneumonia. Diffuse gray regions resembling pneumonia-like opacities, combined with dataset bias toward adult anatomy, likely influenced the model’s prediction.

## Key Observations
- Pediatric anatomy may differ significantly from adult-dominated datasets.
- Motion blur and low contrast can mimic pathological features
- CNNs may rely on texture patterns rather than clinical reasoning.
- Although the model achieved a validation accuracy of 87.5%, high accuracy alone does not guarantee clinical reliability.

## Limitations
- Potential dataset bias toward specific age groups
- Sensitivity to image acquisition variability (blur, contrast)
- No clinical validation or radiologist oversight
- Limited training duration (5 epochs)

## Conclusion
This study demonstrates that CNNs must be evaluated beyond accuracy. Analyzing failure modes provides insights into potential risks, biases, and limitations prior to real-world deployment.
