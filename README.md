# Insomnia Detection Using PPG

## Dataset Description
The dataset used in this study is the **Cyclic Alternating Pattern (CAP) Sleep Database**, a publicly available resource containing polysomnography (PSG) recordings collected at the **Sleep Disorders Centre at Ospedale Maggiore in Parma, Italy**. The CAP dataset is hosted on Physionet and consists of **108 full-night PSG recordings**, featuring a range of physiological signals including EEG, EOG, EMG, ECG, and photoplethysmography (PPG). The dataset has been widely utilized for research in sleep disorders such as insomnia, nocturnal frontal lobe epilepsy, and REM behavior disorder!

### Photoplethysmography (PPG) Data
For this study, **PPG signals** from the CAP dataset were used to develop an insomnia detection model. PPG is a non-invasive optical measurement technique that detects changes in blood volume caused by heartbeats. Unlike traditional PSG, which requires a laboratory setup, PPG enables convenient, at-home sleep monitoring using wearable devices such as smartwatches and fitness trackers.

The dataset includes:
- **PPG recordings sampled at 128 Hz** from the plethysmography (PLETH) channel.
- **9 insomnia patients** with **10,205 valid PPG epochs**.
- **4 normal individuals** serving as controls with **4,674 valid PPG epochs**.
- Each PPG epoch is **30 seconds long**, containing **3,840 samples**.
- **Class-balancing techniques** were applied to ensure an equal number of insomnia and normal epochs during training.

The CAP dataset provides a robust foundation for deep learning models to classify insomnia patients based on physiological signal variations. Unlike PSG-based methods that require multiple electrodes and specialized equipment, PPG offers a user-friendly alternative suitable for long-term monitoring.

## Methods
This study employs deep learning models to classify insomnia using **single-channel PPG signals**. The models used include:

### Model Architectures
- **1D Convolutional Neural Network (1D-CNN)**: Serves as a baseline model, extracting spatial features from PPG signals.
- **CNN + Gated Recurrent Unit (CNN-GRU)**: Enhances temporal dependency learning, capturing long-term variations in heart rate patterns.
- **CNN + Self-Attention Mechanism**: Focuses on key signal features by dynamically assigning importance to different time steps, improving interpretability.

### Preprocessing
- **Noise removal and artifact rejection** to enhance signal clarity.
- **Segmentation into 30-second epochs** to standardize input size.
- **Class balancing through up-sampling** to prevent model bias.

### Training Strategy
- Models were trained using the **binary cross-entropy loss function**.
- Optimization was performed with the **Adam optimizer (learning rate = 0.001)**.
- **Early stopping** was implemented to prevent overfitting.
- Performance was evaluated using **accuracy, precision, recall, and F1-score**.

## Results
The proposed deep learning models achieved high classification performance on the CAP dataset, demonstrating the feasibility of PPG-based insomnia detection.

### Model Performance
#### CNN-GRU Model (Best Performer)
- **Accuracy:** 96.00%
- **Precision:** 97.26%
- **Recall:** 94.03%
- **F1-Score:** 95.62%

#### CNN-Self Attention Model
- **Accuracy:** 91.00%
- **Precision:** 92.00%
- **Recall:** 90.00%
- **F1-Score:** 91.00%

#### 1D-CNN Model
- **Accuracy:** 90.59%
- **Precision:** 96.00%
- **Recall:** 85.00%
- **F1-Score:** 90.00%

The **CNN-GRU model** outperformed the other models, effectively capturing both spatial and temporal features from PPG signals. The **Self-Attention model** provided enhanced interpretability but had slightly lower accuracy. The **1D-CNN baseline model** performed well but was less effective in modeling temporal dependencies.

These results highlight the **potential of PPG-based insomnia detection as a viable alternative to PSG**, enabling **continuous, non-invasive sleep monitoring using wearable devices**.

