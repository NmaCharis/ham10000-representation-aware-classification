# HAM10000 Representation-Aware Classification Study

## Overview

This repository documents an exploratory machine-learning study examining class-representation imbalance in the HAM10000 dermoscopic image dataset.

The study evaluates how different training approaches affect performance across dominant and underrepresented lesion categories.

The experimental approaches include:

- Baseline convolutional neural network (CNN)
- Inverse-frequency class weighting
- MobileNetV2 transfer learning
- MobileNetV2 combined with class weighting
- Class-specific model evaluation
- Confusion-matrix analysis
- Precision, recall, F1-score, and macro-averaged evaluation metrics

## Research Question

How does lesion-class representation imbalance affect image-classification performance, and how do class weighting and transfer learning alter performance across underrepresented lesion categories?

## Dataset

The study uses the publicly available HAM10000 dataset:

**Human Against Machine with 10,000 training images**

The dataset contains 10,015 dermoscopic images representing seven lesion categories:

- akiec — Actinic keratoses and intraepithelial carcinoma
- bcc — Basal cell carcinoma
- bkl — Benign keratosis-like lesions
- df — Dermatofibroma
- mel — Melanoma
- nv — Melanocytic nevi
- vasc — Vascular lesions

The dataset is highly imbalanced, with the `nv` category substantially more represented than several other lesion categories.

## Experimental Approaches

### 1. Baseline CNN

A baseline convolutional neural network was developed to establish an initial performance benchmark.

Approximate results:

- Validation accuracy: 0.57
- Macro F1-score: 0.15

Class-level evaluation showed weak recall for several underrepresented lesion categories.

### 2. Class-Weighted CNN

Inverse-frequency class weighting was applied to increase the influence of underrepresented categories during model training.

Approximate results:

- Validation accuracy: 0.43
- Macro F1-score: 0.30

The model improved recall for several underrepresented categories while reducing aggregate accuracy.

### 3. MobileNetV2 Transfer Learning

MobileNetV2 pretrained on ImageNet was used as a transfer-learning base.

Approximate results:

- Validation accuracy: 0.75
- Macro F1-score: 0.39

This approach achieved the strongest aggregate accuracy, although class-imbalance effects remained.

### 4. MobileNetV2 + Class Weighting

A hybrid experiment combined transfer learning with inverse-frequency class weighting.

Approximate results:

- Validation accuracy: 0.59
- Macro F1-score: 0.43

This approach produced the strongest macro F1-score among the evaluated models and improved recall for several underrepresented lesion categories.

## Comparative Summary

| Model | Accuracy | Macro F1 | Underrepresented-Class Recall Profile |
|---|---:|---:|---|
| Baseline CNN | 0.57 | 0.15 | Very weak |
| Weighted CNN | 0.43 | 0.30 | Substantially improved |
| MobileNetV2 Transfer Learning | 0.75 | 0.39 | Mixed; improved for some classes |
| MobileNetV2 + Class Weighting | 0.59 | 0.43 | Stronger across several underrepresented classes |

## Important Scope and Limitations

This repository examines **lesion-class representation imbalance** within the HAM10000 dataset.

It does not establish:

- demographic fairness
- racial or ethnic fairness
- skin-tone fairness
- equivalent performance across demographic groups
- clinical effectiveness
- diagnostic suitability
- medical-device functionality
- regulatory approval or certification

The models are experimental and are not intended for medical diagnosis, treatment decisions, clinical assessment, or patient care.

## Relationship to MelaninCare AI and MelanoScan AI

This HAM10000 experiment is **separate from MelaninCare AI and MelanoScan AI**.

The experimental models in this repository:

- do not power MelaninCare AI;
- do not power MelanoScan AI;
- are not validation models for either consumer-facing concept; and
- should not be interpreted as establishing the performance of either system.

MelaninCare AI is a separate structured-input, non-clinical consumer education and cosmetic decision-support prototype.

MelanoScan AI is a separate planning-stage concept. Any potential future visual-reference functionality remains conceptual and has not been technically implemented or validated.

## Technical White Paper

This repository supports the technical white paper:

**Addressing Representation Imbalance in Dermatological Image Classification: A Representation-Aware Transfer Learning Study**

Author: **Chidinma Charity Igwe**

## Intended Use

This repository is provided for technical, educational, research, and portfolio documentation purposes only.

It is not intended for clinical or diagnostic use.

## Dataset Reference

Tschandl, P., Rosendahl, C., & Kittler, H. (2018).  
*The HAM10000 dataset, a large collection of multi-source dermatoscopic images of common pigmented skin lesions.*  
Scientific Data, 5, 180161.  
https://doi.org/10.1038/sdata.2018.161
