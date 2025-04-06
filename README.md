# CASSPNet: Continual Authentication through Sensor and Scroll Patterns

CASSPNet is a novel deep learning framework designed for continuous user authentication on mobile devices. By leveraging both classical and quantum-enhanced neural network architectures, the system provides robust and accurate binary classification to distinguish between legitimate users and imposters. This repository contains the implementation details, experimental evaluations, and architectural design as described in our research paper.

---

## Overview
Traditional authentication methods like passwords are vulnerable due to their single point-of-entry nature. CASSPNet overcomes these limitations by continuously authenticating users through behavioral patterns derived from sensor and touch-screen data. This approach not only strengthens security but also adapts over time using an online learning strategy to mitigate issues like catastrophic forgetting and model drift.

## Key Features
- **Continual Authentication:** Provides continuous user verification throughout a mobile application's session.
- **Hybrid Architecture:** Integrates quantum neural networks with classical deep learning models.
- **Online Learning:** Uses a Stochastic Gradient Descent (SGD) based online classifier for incremental data updates.
- **Robust Performance:** Achieves high accuracy and low Equal Error Rates (EER) in binary classification tasks.
- **Comparative Analysis:** Evaluates multiple architectures including QCNN, QLSTM, and a vanilla LSTM, demonstrating state-of-the-art performance.

## Dataset
The system is evaluated using the DAKOTA dataset, which includes:
- Data from **45 participants** over **15 sessions** (1.5 minutes each).
- Sensor data (accelerometer, gyroscope, magnetometer) and touch-screen scroll data.
- **126 features** extracted through statistical analysis on sensor axes and detailed scroll event metrics.
- Data augmentation through oversampling techniques (ADASYN, SMOTE, and SVMSMOTE) to address class imbalance.

  ![Graphs](https://github.com/user-attachments/assets/1967170d-fb4d-4907-81d6-28e4fa7ecdef)


## Model Architecture

![All_models](https://github.com/user-attachments/assets/54b6f358-0c16-4d25-99ec-4728ec692e02)

### Quantum-Classical Neural Network (QCNN)
- **Hybrid Model:** Combines classical feed-forward layers with a quantum circuit.
- **Quantum Circuit:** Utilizes PennyLane with 4 qubits and parameterized rotations (e.g., `qml.RX`, `qml.RY`) to extract quantum-enhanced features.
- **Classical Component:** Consists of two dense layers with dropout regularization and a sigmoid output layer for binary classification.

### Quantum-LSTM Neural Network (QLSTM)
- **Sequential Processing:** Integrates a quantum feature extraction layer with a classical LSTM to handle temporal dependencies.
- **Hybrid Integration:** Leverages the strengths of both quantum computing and recurrent neural networks to improve performance on sequential data.

### Long Short-Term Memory (LSTM)
- **Vanilla LSTM Model:** Serves as a baseline model to capture temporal patterns in sequential sensor and touch data.
- **Hyper-parameter Optimization:** Employs random optimization techniques (MLROSe) for tuning hidden units, dropout rate, learning rate, and batch size.
- **Regularization and Early Stopping:** Uses dropout layers and early stopping to prevent overfitting.

## Methods and Techniques
- **Data Pre-processing:** 
  - Extraction of 126 features from raw sensor and scroll data.
  - Oversampling techniques to address the imbalanced nature of binary classification.
- **Online Learning:** 
  - Incorporates an online classifier using the SGD algorithm to continuously update the model with new data samples.
  - Periodic retraining of the DNN to integrate newly accumulated data while preserving previously learned information.

## Experimental Results
The experimental evaluation shows that:
- **QCNN-based model:** Achieved an accuracy of **99.91%** with an Equal Error Rate (EER) of **0.7%**.
- **QLSTM-based model:** Attained an accuracy of **99.83%** with an EER of **0.26%**.
- **LSTM-based model:** Achieved an accuracy of **99.74%** with an EER of **0.35%**.
  
  ![Screenshot 2025-04-06 230143](https://github.com/user-attachments/assets/a48d64bd-1d12-4ab5-bd4c-f1d7078b435f)

These results demonstrate the system's high reliability and improved performance over state-of-the-art approaches, especially in mitigating issues like catastrophic forgetting and model drift.
