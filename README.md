# 🖼️ Image Classification on CIFAR-10: From Scratch to Transfer Learning

**How far can we push accuracy on CIFAR-10 by evolving from a simple CNN to cutting-edge pretrained models?**

---

## 📋 Project Overview

This project explores the performance evolution from custom-built CNNs to modern transfer learning models on the CIFAR-10 dataset. Unlike many projects that stop at a single CNN, this work systematically compares multiple architectural improvements and regularization techniques before benchmarking against pretrained models.

---

## 🎯 Research Question

**What happens when we compare custom-built CNNs against modern transfer learning models on CIFAR-10?**

We answer this by exploring a step-by-step evolution of improvements:

1. Baseline CNN (from scratch) — a simple ConvNet to establish a starting point
2. Deeper CNN — added more convolutional layers and dropout to extract richer features
3. BatchNorm, Dropout & Regularization — introduced Batch Normalization, GlobalAveragePooling and L2 weight decay
4. Early Stopping — tuned training with early stopping to avoid overfitting
5. Data Augmentation — applied random rotations, flips and shifts to improve robustness
6. Transfer Learning (MobileNetV2 variants) — benchmarked several MobileNetV2 head/fine-tuning strategies

---

## 📊 Dataset

**Dataset:** CIFAR-10  
**Size:** 60,000 color images (32x32 pixels) across 10 balanced classes:  
✈️ airplane | 🚗 automobile | 🐦 bird | 🐱 cat | 🦌 deer | 🐶 dog | 🐸 frog | 🐴 horse | 🚢 ship | 🚚 truck  

**Split:** 50,000 training images + 10,000 testing images  

**Challenges:**
- Low-resolution images → harder to extract strong features
- Some categories are very similar (cat vs dog, car vs truck)

---

## 🛠️ Methodology & Models

### 🔹 Custom CNNs

| Model | Architecture | Test Accuracy | Training Accuracy |
|-------|-------------|---------------|-------------------|
| **Baseline CNN** | Conv2D(32) → MaxPool → Conv2D(64) → MaxPool → Dense(128) → Softmax | ~68.9% | ~84% |
| **Deeper CNN + Dropout** | Added Conv2D(128), Dense(256), Dropout(0.5) | 73.4% | 85% |
| **CNN + BatchNorm + GAP** | Added BatchNormalization + GlobalAveragePooling | 73.1% | 91% |
| **CNN + Regularizer (L2)** | Added weight decay regularization | 72.5% | 93% |
| **CNN + Early Stopping** | Hyperparameter tuning + early stopping | 72.9% | 94% |
| **CNN + Data Augmentation** | Rotations, flips, shifts | **76.9%** ✅ | 74% |

### 🔹 Transfer Learning

| Model | Architecture | Test Accuracy |
|-------|-------------|---------------|
| **MobileNetV2.1** | MobileNetV2 → GAP → Dense(128, ReLU) → Dense(10, Softmax) | **86.6%** ✅ |
| **MobileNetV2.2** | MobileNetV2 → GAP → Dropout(0.3) → Dense(10, Softmax) | 85.6% |
| **MobileNetV2.3** | Same as V2.2, batch size 64 | 85.6% |

---

## 📈 Key Insights

- 📈 Custom CNNs improved step by step, but plateaued around ~77%
- 🧠 Transfer learning (MobileNetV2) significantly outperformed scratch CNNs
- 🔍 MobileNetV2.1 achieved state-of-the-art performance on CIFAR-10 at 86.6%
- 🐱🐶 Most misclassifications: cats vs dogs, cars vs trucks

---

🙋🏽‍♀️ **About Me**

- **Rocío Zahory Vásquez Romero**  
- Senior Auditor | Data Science & Machine Learning Enthusiast  
- Email: rocio.vasquez@usach.cl  
- LinkedIn: [https://www.linkedin.com/in/rocio-zahory-vasquez-romero-3621ab1a7/](https://www.linkedin.com/in/rocio-zahory-vasquez-romero-3621ab1a7/)

---
⚡ **How to Run**

1. Clone the repo:  
```bash
git clone https://github.com/nataliadominguez99/Image-classification-using-CNN-and-Transfer-Learning.git
cd Image-classification-using-CNN-and-Transfer-Learning

2.Install dependencies:
pip install -r requirements.txt

3. Run the main notebook: 
jupyter notebook "ProjectCifar.ipynb"


