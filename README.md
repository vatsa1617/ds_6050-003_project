# FracTrack
### Deep Learning for X-Ray Fracture Analysis

FracTrack is a deep learning-based medical imaging project focused on automated abnormality detection in upper-extremity X-ray images. This project compares ResNet-50 and ConvNeXt-Tiny architectures across both single-task and multi-task learning frameworks using the MURA musculoskeletal radiograph dataset.

The primary objective of this work is to investigate whether modern convolutional neural network architectures can improve fracture and abnormality detection performance while maintaining clinically relevant sensitivity.

---

## Project Overview

Musculoskeletal (MSK) conditions affect over 1.7 billion people globally, and radiographic misinterpretations remain a persistent challenge in emergency and orthopedic care. FracTrack explores the use of deep learning models as a supplementary diagnostic support tool for identifying abnormalities in upper-extremity X-rays.

This project evaluates:

- ResNet-50 vs ConvNeXt-Tiny
- Single-task vs multi-task learning
- Effects of data augmentation strategies
- Generalization to external datasets
- Body-part-specific performance variation

---

## Datasets

### MURA Dataset

Primary dataset used for training and evaluation:

- 40,561 upper-extremity X-ray images
- 12,173 patients
- 14,863 studies
- Provided by Stanford University Medical Center

Body parts included:
- Elbow
- Finger
- Forearm
- Hand
- Humerus
- Shoulder
- Wrist

Abnormalities include:
- Fractures
- Hardware
- Degenerative joint disease
- Miscellaneous abnormalities

Dataset source:  
https://stanfordmlgroup.github.io/competitions/mura/

---

### FracAtlas Dataset

Used for external validation and generalization testing.

- Public fracture imaging dataset
- Includes fracture classification and localization labels
- Only hand and shoulder images were used for this project

Dataset source:  
https://www.kaggle.com/datasets/abdohamedelkholy/fracatlas

---

## Model Architectures

### ResNet-50
- ImageNet pretrained backbone
- Partial layer freezing
- Binary abnormality detection
- Multi-task extension for body-part classification

### ConvNeXt-Tiny
- ImageNet pretrained ConvNeXt backbone
- Fine-tuned final layers
- Single-task and multi-task variants
- Adam optimizer
- Transfer learning framework

---

## Experimental Design

The project evaluated:

### 1. Patient Sampling Strategies
Two patient-level data splitting strategies were compared:
- Strategy 1: Treat each study independently
- Strategy 2: One study per patient

### 2. Architecture Comparison
Performance comparison between:
- ResNet-50
- ConvNeXt-Tiny

### 3. Multi-Task Learning
Evaluation of:
- Abnormality detection alone
- Abnormality detection + body-part classification

### 4. Data Augmentation
Compared:
- No augmentation
- Medical-safe augmentation
- Heavy augmentation

### 5. External Validation
Tested model generalization using FracAtlas data.

---

## Key Results

| Model | Accuracy | AUC | F1 Score |
|---|---|---|---|
| ResNet-50 | 64.7% | 0.754 | 0.689 |
| ConvNeXt-Tiny | 71.2% | 0.788 | 0.715 |

### Major Findings

- ConvNeXt-Tiny consistently outperformed ResNet-50
- Multi-task learning reduced abnormality detection performance
- Medical-safe augmentation improved sensitivity
- Model performance varied significantly across anatomical regions
- External validation revealed poor generalization to unseen datasets

---

## Repository Structure

```text
.
├── archived_experiments/
├── csvs/
├── notebooks/
├── outputs/
├── paper/
├── requirements.txt
└── README.md
```

---

## Environment & Compute

Development and experimentation were conducted across:
- Google Colab
- Local Jupyter environments
- University of Virginia Rivanna HPC cluster

Final training and evaluation were primarily performed using Rivanna GPU resources due to improved computational stability and performance.

---

## Installation

Clone the repository:

```bash
git clone https://github.com/vatsa1617/ds_6050-003_project.git
cd ds_6050-003_project
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Usage

Run notebooks through:
- Jupyter Notebook
- Google Colab
- Rivanna GPU environment

Example:

```bash
jupyter notebook
```

---

## Technologies Used

- Python
- PyTorch
- Torchvision
- NumPy
- Pandas
- Scikit-learn
- Matplotlib
- Seaborn
- OpenCV

---

## Limitations

Several limitations were identified during experimentation:

- Significant class imbalance
- Poor body-part classification performance
- Reduced generalization to external datasets
- Variability in image framing across anatomical regions
- Computational limitations for larger foundation models

---

## Future Improvements

Potential future directions include:

- Larger and more diverse training datasets
- Improved class balancing techniques
- Transformer-based medical imaging architectures
- Grad-CAM explainability integration
- Improved external validation pipelines
- Enhanced body-part classification methods

---

## Contributors

- Srivatsa Balasubramanyam
- Claire Sullivan
- Jasmine Waller
- Kristina Quintana

University of Virginia  
School of Data Science

---

## References

- MURA: Large Dataset for Abnormality Detection in Musculoskeletal Radiographs
- FracAtlas Dataset
- YOLO Object Detection Framework
- ConvNeXt Architecture
- ResNet Architecture

---

## Acknowledgements

This project was completed as part of coursework at the University of Virginia School of Data Science.

The authors used Claude to assist with portions of code development and Grammarly for grammar review and editing.
