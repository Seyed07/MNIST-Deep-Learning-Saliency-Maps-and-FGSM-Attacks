# **MNIST Classification and Adversarial Robustness Analysis**

## **📋 Project Overview**
This project focuses on handwritten digit classification using the MNIST dataset, employing a neural network. It also evaluates the model’s robustness under adversarial attacks like **FGSM (Fast Gradient Sign Method)** and explains model sensitivity using **saliency maps**. A robust pipeline for handling data, grid-search-based model optimization, and performance evaluation is implemented.

---

## **🛠️ Project Features**
- **Data Handling**: Automated downloading, preprocessing, and splitting of the MNIST dataset.
- **Model Training**: A fully connected multi-layer perceptron (MLP) trained to achieve over **99% test accuracy**.
- **Hyperparameter Optimization**: Multiple configurations experimented using **grid search** to find optimal hyperparameters.
- **Robustness Testing**:
  - Saliency Maps to highlight the most critical pixels influencing predictions.
  - FGSM adversarial attack analysis to test the model's resilience to input perturbations.
- **Visualizations**: Confusion matrices, saliency maps, adversarial samples, and accuracy/loss progression.

---

## **🔧 Technical Details**
### **1. Dataset Description**
The **MNIST dataset** contains gray-scale images from the digits 0–9:
- **Training Data**: 49,000 samples (70% of the dataset).
- **Validation Data**: 14,000 samples (20% of the dataset).
- **Testing Data**: 7,000 samples (remaining 10%).

Each image is:
- **28x28 pixels** grayscale image.
- Preprocessed by normalizing and converting labels into one-hot encoded vectors for classification.

### **2. Model Overview**
The implemented model is a **Fully Connected Neural Network (MLP)**:
- Input Layer: **784 neurons** for flattened 28x28 images.
- **Hidden Layers**: Configurable through grid search.
  Example: `[512, 256, 128]` neurons, followed by **ReLU activations, dropout**, and optional **L2 regularization**.
- Output Layer: **Softmax activation** for 10 class probabilities.

---

## **📈 Performance Summary**
- **Final Model Testing**:
  - **Test Accuracy**: Achieved over **98%** accuracy on clean data.
  - Results visualized using **accuracy/loss graphs** and confusion matrices.

---

### **3. Adversarial Analysis**
#### **FGSM Attack**
- Generates adversarial examples by adding perturbations to the input image. The strength of the perturbation is controlled by the **epsilon** value.
- Analysis shows significant performance degradation with adversarial images:
  - Clean Accuracy: **99%+**
  - FGSM Attack Accuracy: Drops significantly depending on **epsilon**.

#### **Saliency Maps**
- Visualizes the pixels most contributing to the model’s decision-making using the **gradient of the output w.r.t input**.
- The **15% most critical regions** (top-15 saliency) were identified to analyze model behavior and measure its sensitivity to pixel changes.

#### **Visualization Examples**:
- **Original vs Adversarial Samples**
  - Comparison of predictions before and after FGSM attack for the same image set.
- **Saliency Map Heatmaps**
  - Highlights sensitive areas influencing decision-making.

---

## **🗂️ Project Structure**
```plaintext
root/
├── Q1_keras.ipynb              
├── outputs                
└── README.md                  
```

---

---

## **🔬 Example Visualizations**
### Accuracy/Loss Progression
![Accuracy Graph](example_accuracy_graph.png)

### Confusion Matrix (Original vs Adversarial Data)
#### Original Data
![Confusion Matrix - Original](confusion_matrix_original.png)
#### Adversarial Attack
![Confusion Matrix - Adversarial](confusion_matrix_adversarial.png)

### Saliency Map Heatmap
![Saliency Map](saliency_map.png)

### FGSM Attack Impact
| **Epsilon (Perturbation Strength)** | **Test Accuracy** |
|-------------------------------------|-------------------|
| 0.0 (Clean Data)                    | 98.XX%            |
| 0.1                                 | ~50%              |
| 0.3                                 | ~20%              |

---

## **⚡ Future Work**
- **Adversarial Defense**:
  - Train the model with adversarial examples for robustness.
  - Incorporate recent adversarial training methods.
- **Deployability**:
  - Serve the trained model using TensorFlow.js or a Web API for easy usage.
- **Scalability**:
  - Extend the project to more complex datasets (e.g., CIFAR-10).

---


This README documentation provides a detailed yet concise explanation of your MNIST classification and adversarial attack project. Let me know if you'd like me to refine any section further!
