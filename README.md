# Breast Cancer Detection Using ViT-CoMer-Lite

A deep learning project for binary classification of breast histopathology images using a lightweight Vision Transformer and convolutional feature extraction approach.

## Overview

Breast cancer histopathology classification involves identifying tissue patterns associated with cancerous and non-cancerous regions. This project explores **ViT-CoMer-Lite**, a lightweight hybrid deep learning model designed to combine local visual feature extraction with global contextual representation.

The model is trained on the Breast Histopathology Images dataset to classify image patches as either IDC-positive (cancerous) or IDC-negative (non-cancerous).

The project includes image preprocessing, data augmentation, two-phase training, model evaluation, confusion matrix analysis, ROC analysis, and sample prediction visualization.

## Objectives

- Develop a deep learning model for breast histopathology image classification.
- Combine convolutional feature extraction with transformer-inspired representation learning.
- Apply preprocessing and data augmentation to improve model generalization.
- Evaluate classification performance using multiple metrics.
- Document the training and inference workflow for reproducibility.

## Tech Stack

- **Language:** Python
- **Deep Learning:** TensorFlow, Keras
- **Model Architecture:** ViT-CoMer-Lite, EfficientNet-based feature extraction
- **Domain:** Computer Vision and Medical Image Analysis
- **Image Processing:** Image resizing, normalization, and data augmentation
- **Data Analysis:** NumPy, Pandas
- **Visualization:** Matplotlib, Seaborn
- **Evaluation:** Scikit-learn
- **Environment:** Kaggle Notebooks with GPU acceleration

## Dataset

**Breast Histopathology Images**

The dataset contains 277,524 RGB image patches extracted from breast biopsy slides. Each image is labeled according to the presence or absence of Invasive Ductal Carcinoma (IDC).

| Class | Label | Number of images |
|---|---|---:|
| Non-cancerous tissue | IDC-negative (0) | 198,738 |
| Cancerous tissue | IDC-positive (1) | 78,786 |
| **Total** | | **277,524** |

### Dataset links

- [Kaggle dataset used in this project](https://www.kaggle.com/datasets/akhiamma/akhiammaa)
- [Original Breast Histopathology Images dataset](https://www.kaggle.com/datasets/paultimothymooney/breast-histopathology-images)

The dataset is not included in this repository because of its size. Download it from Kaggle and configure the notebook to use the extracted dataset directory.

## Data Preprocessing

The documented preprocessing pipeline includes:

- Resizing images from 50 × 50 to 224 × 224 pixels.
- Normalizing pixel values to the range [0, 1].
- Splitting the data into 70% training, 15% validation, and 15% testing.
- Applying rotations, horizontal and vertical flips, zoom, brightness adjustment, and channel shifts.
- Using class weights to account for the imbalance between IDC-positive and IDC-negative samples.

## Model Architecture

The ViT-CoMer-Lite approach combines convolutional feature extraction with global representation learning.

The documented architecture includes:

1. **Feature extraction:** An EfficientNet-based CNN backbone extracts hierarchical image features.
2. **Convolutional feature refinement:** A convolutional layer refines local feature representations.
3. **Global pooling:** Global Average Pooling produces a compact feature representation.
4. **Classification head:** Dense layers and dropout support classification while helping control overfitting.
5. **Output layer:** A sigmoid activation produces a score for binary classification.

*Note: Confirm the exact EfficientNet variant and architecture configuration against the final notebook before reproducing the implementation.*

## Training Strategy

The documented training workflow uses two phases:

**Phase 1 — Warm-up**
- Freeze the backbone layers.
- Train the newly added classification layers.
- Duration: 3 epochs.
- Learning rate: 1e-4.

**Phase 2 — Fine-tuning**
- Unfreeze selected backbone layers for further optimization.
- Use a smaller learning rate of 1e-5.
- Duration: 5 epochs.

Additional documented settings include:
- Input image size: 224 × 224
- Batch size: 8
- Optimizer: Adam
- Loss function: Binary Crossentropy
- Environment: Kaggle GPU, with an NVIDIA Tesla T4 used in the documented setup

## Results and Evaluation

The project report documents the following final test-set metrics:

| Metric | Reported result |
|---|---:|
| Accuracy | 94% |
| Precision | 92% |
| Recall (Sensitivity) | 90% |
| F1-score | 91% |

The evaluation workflow also includes:

- Confusion matrix analysis
- ROC curve analysis
- Training-loss visualization
- Sample prediction visualization

These metrics describe the results reported in the project documentation. Re-run the notebook to independently reproduce them.

## Getting Started

### Requirements

- Python 3.10 or later
- TensorFlow 2.18.0, as specified in the reproducibility guide
- Keras and the supporting libraries listed in `requirements.txt`
- A GPU-enabled environment recommended for training
- Sufficient disk space for the dataset

### Running on Kaggle

1. Download the dataset using one of the Kaggle links above.
2. Open the project notebook in Kaggle.
3. Attach the Breast Histopathology Images dataset through **Add Data**.
4. Enable GPU acceleration in the notebook settings.
5. Verify the dataset path and configuration.
6. Run the notebook cells sequentially.
7. Review the generated evaluation metrics and visualizations.

Training may require substantial memory and computation because of the dataset size. If necessary, adjust the batch size and other settings, then document any changes.

## Generated Outputs

The documented workflow generates evaluation and model artifacts, including:

- Confusion matrix visualization
- ROC curve visualization
- Training history plots
- Sample prediction visualizations
- Trained model checkpoint

The original guide lists the output directory as `/kaggle/working/`. Exact filenames depend on the notebook implementation.

## Project Resources

- **Dataset:** [Breast Histopathology Images on Kaggle](https://www.kaggle.com/datasets/akhiamma/akhiammaa)
- **Original dataset:** [Paultimothymooney's Kaggle dataset](https://www.kaggle.com/datasets/paultimothymooney/breast-histopathology-images)
- **ViT-CoMer research paper:** [arXiv:2304.04996](https://arxiv.org/abs/2304.04996)

## Authors

- **Janagam Akhila**
-

Academic project: MA-305

## Disclaimer

This project is an academic research prototype for histopathology image classification. It is not a clinically validated diagnostic system and must not be used as a substitute for professional medical evaluation.

---

*The dataset and trained model artifacts are not bundled with this repository. Refer to the dataset links and notebook instructions to reproduce the workflow.*
