
# 🎙️ Speech Diarization with Transformer Attractors (EEND-TA)

This project explores **end-to-end neural diarization (EEND)** using **Transformer Attractors** to segment and label speaker turns in an audio stream. It builds on advanced diarization methods aimed at robustly identifying **"who spoke when"** in multi-speaker conversations, using modern deep learning architectures.

## 📌 Overview

Speech diarization is critical for organizing, analyzing, and summarizing audio data — especially in meetings, podcasts, interviews, and surveillance applications. This project:
- Implements and experiments with the **EEND-TA** architecture
- Trains and evaluates the model using the **VoxConverse dataset**
- Compares speaker segmentation accuracy across varying speaker overlaps
- Analyzes transformer-based attention patterns for diarization

## 🚀 Key Features

- ✅ Transformer-based model using **attractors** to identify speakers
- ✅ End-to-end pipeline for diarization: preprocessing, training, and evaluation
- ✅ Visualization of speaker segments and diarization error rate (DER)
- ✅ Multi-GPU training support
- ✅ Modular code structure for experimentation and extension

## 🧠 Techniques & Tools

- 📚 **Transformer Encoders**
- 🎯 **Attractor mechanisms** for speaker separation
- 📈 Diarization metrics like **DER** and **Jaccard Error Rate**
- 🧰 Tools: `PyTorch`, `NumPy`, `LibROSA`, `Scikit-learn`, `matplotlib`

## 📂 Project Structure

```plaintext
Speech_Diarization/
├── configs/               # Configuration files
├── data/                  # Data processing scripts
├── models/                # Transformer and attractor-based models
├── utils/                 # Evaluation and helper functions
├── notebooks/             # Jupyter notebooks for exploration
├── train.py               # Main training script
├── evaluate.py            # Diarization evaluation
└── README.md              # Project documentation
```

## 🧪 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/Speech_Diarization.git
cd Speech_Diarization
```

### 2. Set up the environment

```bash
pip install -r requirements.txt
```

### 3. Download and prepare the VoxConverse dataset

Follow instructions from: https://github.com/joonson/eend

### 4. Train the model

```bash
python train.py --config configs/train_config.yaml
```

### 5. Evaluate

```bash
python evaluate.py --checkpoint checkpoints/model.pth
```

## 📊 Results

- Achieved **X.XX% DER** on VoxConverse test set
- Successfully diarized overlapping speech segments
- Improved attention focus using transformer attractors

## ✍️ Related Blog

Read the blog post explaining the motivation and process behind this project:

**🔗 [“Will You Shut Up, Man?” – A Journey into Speech Diarization](https://medium.com/@venkatachalam.sps/will-you-shut-up-man-b94690fc9049)**

## 👨‍💻 Author

**Venkatachalam Subramanian Periya Subbu**  
Data Scientist
[LinkedIn](https://www.linkedin.com/in/venkatachalam-subramanian-periya-subbu/) | [Medium](https://medium.com/@venkatachalam.sps)
**Gopi Maguluri**  
Data Scientist
[LinkedIn](https://www.linkedin.com/in/gopimaguluri2267/)
**Raghava Srinivasan**  
Data Engineer
[LinkedIn](https://www.linkedin.com/in/raghava-srinivasan/)
