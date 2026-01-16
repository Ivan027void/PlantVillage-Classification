# 🌿 Plant Leaf Disease Classification
**CNN vs CNN (Augmented) vs MobileNetV2 (Transfer Learning)**

## Project Overview

This project investigates how **data augmentation** and **transfer learning** affect the performance of convolutional neural networks for **plant leaf disease classification**.

Three models are compared:

1. **CNN (clean data)** — baseline model without augmentation
2. **CNN (augmented data)** — same architecture with data augmentation
3. **MobileNetV2 (augmented, pretrained)** — transfer learning approach

The goal is to understand the **trade-offs** between:

* Simple training vs augmented training
* Custom CNN vs pretrained lightweight models

---

## 🎯 Research Objectives

### Primary Objective

To evaluate the impact of **data augmentation** and **transfer learning** on CNN performance for plant disease classification.

### Specific Objectives

1. Establish a strong **baseline** using a simple CNN without augmentation.
2. Measure the **augmentation** affects generalization performance.
3. Assess the benefit of **pretrained models** (MobileNetV2).
4. Handle **class imbalance** using weighted loss and macro F1-score.
5. Provide a **reproducible experimental workflow**.

---

## Dataset

* **Total images**: 
* **Number of classes**: 15
* **Classes include**:
* **Dataset Source** :[PlantVillage Dataset](https://www.kaggle.com/datasets/emmarex/plantdisease) 
  * Pepper: healthy, bacterial spot
  * Potato: healthy, early blight, late blight
  * Tomato: bacterial spot, early blight, late blight, leaf mold, septoria leaf spot, spider mites, target spot, yellow leaf curl virus, mosaic virus, healthy

---

##  Models

| Model                   | Description                               |
| ----------------------- | ----------------------------------------- |
| CNN (clean)             | Simple CNN trained on original images     |
| CNN (augmented)         | Same CNN with real-time data augmentation |
| MobileNetV2 (augmented) | Pretrained MobileNetV2 + augmentation     |

---

## ⚙️ Experimental Setup

* **Framework**: TensorFlow / Keras
* **Training environment**: Google Colab (CPU/GPU T4)
* **Loss function**: Categorical Crossentropy with **class weights**
* **Optimizer**: Adam
* **Metrics**:

  * Accuracy
  * Macro F1-score
  * Confusion Matrix
  * Classification Report

**Why macro F1?**
Accuracy alone can be misleading in imbalanced datasets. Macro F1 gives equal importance to each class.

---

## 📊 Results Summary

### Overall Performance

| Model                   | Accuracy   | Macro F1   | Key Strength                    |
| ----------------------- | ---------- | ---------- | ------------------------------- |
| CNN (clean)             | 0.8935     | 0.8682     | Strong baseline, fast training  |
| CNN (augmented)         | **0.9083** | 0.8924     | Best raw accuracy               |
| MobileNetV2 (augmented) | 0.9019     | **0.8934** | Best class-balanced performance |

---

## 🔍 Key Findings

### 1. CNN Clean vs CNN Augmented

* Augmentation **slows training** but improves **generalization**.
* Validation performance improves even when the dataset is already clean.
* Shows that augmentation is still valuable in controlled datasets.

### 2. CNN Augmented vs MobileNetV2

* CNN augmented gives the **highest accuracy**.
* MobileNetV2 gives the **best macro F1**, meaning:

  * Better handling of minority classes
  * More stable predictions across categories
* Trade-off:

  * CNN is simpler and faster
  * MobileNetV2 is more robust but heavier

### 3. Class Imbalance Handling

* Weighted loss prevents the model from ignoring small classes.
* Pretrained features in MobileNetV2 improve recall on rare classes.
* Confirms that **metric choice matters** as much as model choice.

---

## Model recommendations

| Scenario                          | Recommended Model       |
| --------------------------------- | ----------------------- |
| Quick baseline / fast experiments | CNN (clean)             |
| Best overall accuracy             | CNN (augmented)         |
| Best balance across all classes   | MobileNetV2 (augmented) |

---

## 📁 Repository Structure

```
├── notebook.ipynb
├── all_models_and_histories.zip
└── README.md
```

---

## How to Reproduce

1. Clone this repository
2. Open the notebook in **Google Colab**
3. Enable GPU (optional but faster)
4. Run all cells:

   * Data loading
   * Model building
   * Training
   * Evaluation
5. Compare results in the **Results** section

---

## 📘 Learning Reflection

This project helped me understand how **experimental design** and **model comparison** work in practice.

Key learning outcomes:
* How **data augmentation** affects overfitting and generalization
* How **transfer learning** improves performance on imbalanced data
* Why **macro F1-score** is important beyond accuracy
* How to interpret **confusion matrices** and class-level behavior
* How to turn experimental results into **structured analysis**

* Shorten this README into a **lighter version** for portfolio, or
* Adapt it into a **formal project report** style.
