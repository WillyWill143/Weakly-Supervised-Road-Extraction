# Weakly Supervised Road Extraction from Satellite Imagery

This repository contains the implementation for the paper **"Weakly Supervised Road Extraction from Satellite Imagery using Partial Focal Loss and Stratified Point Supervision."**

## Project Overview
This project explores a low-cost alternative to dense road segmentation. Instead of using expensive, pixel-perfect masks, this model trains using **extremely sparse point supervision** (e.g., only 50 or 100 labeled pixels per image).

**Key Features:**
* **Architecture:** DeepLabV3+ with a ResNet34 backbone (pre-trained on ImageNet).
* **Loss Function:** Custom **Partial Focal Cross Entropy (pfCE)** loss to handle unlabeled background pixels and class imbalance.
* **Sampling:** Stratified "smart sampling" to balance road and background points.

## Key Results
* **Stability:** A focal parameter of $\gamma=2$ provided the most stable training performance.
* **Efficiency:** Performance saturates at approximately **100 labeled points per image**. Adding more points beyond this threshold yields diminishing returns.

## Dataset
This model was trained and evaluated on the **DeepGlobe Road Extraction Dataset**, with images resized to 512x512 for optimization.

## Usage & Environment Notes
This code was originally developed and executed in a **Kaggle** environment to utilize GPU acceleration. Please note the following when reviewing or running the notebook:

1.  **File Paths:** The directory paths in the notebook utilize Kaggle's input structure (e.g., `/kaggle/input/...`). You may need to adjust these paths to match your local dataset location.
2.  **Training Loop:** The primary training loop has been **commented out** by default. This is to allow for immediate inference using the saved model weights without re-running the time-consuming training process. Uncomment the training block if you wish to retrain the model from scratch.
