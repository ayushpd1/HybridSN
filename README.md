HybridSN: Hyperspectral Image Classification

📌 Overview

This project implements HybridSN (Hybrid Spectral–Spatial Convolutional Neural Network) for Hyperspectral Image (HSI) classification.
The model combines 3D-CNN layers (to extract spectral–spatial features) with 2D-CNN layers (for spatial refinement), achieving state-of-the-art results.

📂 Dataset
	•	Indian Pines dataset (AVIRIS sensor) was used.
	•	Size: 145 × 145 pixels with 220 spectral bands (after removing noisy bands → 200).
	•	Classes: 16 land-cover categories.

⚙️ Preprocessing
	•	Exploratory Data Analysis (EDA) to understand class distribution.
	•	Principal Component Analysis (PCA) to reduce dimensionality.
	•	Patch Extraction with window size (e.g., 25×25) for training.
	•	Train/Test split with stratified sampling.

🏗️ Model Architecture (HybridSN)
	•	Input: PCA-reduced HSI patches.
	•	3D CNN layers: Capture joint spectral–spatial information.
	•	2D CNN layers: Refine spatial features.
	•	Fully Connected Layers: Perform classification into land-cover classes.

📊 Results

On the Indian Pines dataset:
	•	Overall Accuracy (OA): 99.12%
	•	Average Accuracy (AA): 99.14%
	•	Kappa Coefficient: 0.9900
