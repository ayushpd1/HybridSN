# HybridSN: 3D–2D CNN for Hyperspectral Image Classification

This repository contains a high-performance implementation of HybridSN, a spectral-spatial 3D–2D CNN architecture designed for high-dimensional hyperspectral imagery (HSI) classification. The model effectively captures both local spatial patterns and spectral correlations, achieving state-of-the-art results on the Indian Pines dataset.

## 📖 Project Overview

Developing effective classifiers for HSI is challenging due to the high dimensionality of spectral data and the limited availability of labeled samples. This implementation utilizes a hybrid approach:

- **3D CNN**: Extracts joint spectral-spatial features from the raw HSI data cubes.
- **2D CNN**: Further refines spatial abstractions before final classification.
- **Optimized Workflow**: Incorporates Principal Component Analysis (PCA) and strategic patch extraction to enhance training efficiency.

## 🧠 Model Architecture

The architecture comprises three 3D convolutional layers followed by two 2D convolutional layers, utilizing batch normalization and dropout for regularization.

| Layer Type | Kernel Size | Filters | Description |
| :--- | :--- | :--- | :--- |
| **3D Conv 1** | (7, 3, 3) | 8 | Initial spectral-spatial feature extraction |
| **3D Conv 2** | (5, 3, 3) | 16 | Intermediate spectral-spatial learning |
| **3D Conv 3** | (3, 3, 3) | 32 | Deep spectral-spatial abstraction |
| **2D Conv 1** | (3, 3) | 64 | Spatial feature refinement |
| **2D Conv 2** | (3, 3) | 64 | Final spatial feature mapping |

## ⚙️ Preprocessing Workflow

The preprocessing pipeline is designed to reduce redundancy and prepare structured input for the hybrid network:

- **Exploratory Data Analysis (EDA)**: Understanding class distributions and spectral signatures.
- **PCA Dimensionality Reduction**: Reducing the spectral bands (e.g., from 200 to 30) while preserving 99% of the variance to improve computational efficiency.
- **Patch Extraction**: Segmenting the HSI cube into overlapping 25x25 spatial patches for localized learning.
- **Data Augmentation**: Implementing random flips and rotations to improve model generalization.

## 📊 Performance & Evaluation

The model was evaluated on the Indian Pines dataset using a systematic 10% training and 90% testing split.

### Metrics
Through systematic hyperparameter tuning (Adam optimizer, `1e-3` learning rate, and `ReduceLROnPlateau` scheduler), the following results were achieved:

- **Overall Accuracy (OA)**: `99.12%`
- **Average Accuracy (AA)**: `99.14%`
- **Kappa Score**: `0.99`

### Training Performance
The model exhibits stable convergence with early stopping implemented to prevent overfitting.

### Classification Results
The classified output demonstrates high fidelity to the ground truth with minimal noise in class boundaries.

## 🛠 Requirements

- Python 3.11+
- PyTorch
- Scikit-learn
- SciPy
- tqdm

## 🚀 Usage

Follow the steps below to run the project pipelines:

1. **Preprocessing**:  
   Run `Preprocessing.ipynb` to apply PCA and generate spectral patches.
2. **Training**:  
   Run `Training.ipynb` to train the HybridSN model and save the best checkpoints.
3. **Testing**:  
   Use `Testing.ipynb` to evaluate the model on the test set and generate performance metrics.

