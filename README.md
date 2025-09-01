# Deep Learning Assignment 3 - Second Semester 1403-1404

This repository contains my solutions for the third homework assignment in my Deep Learning course. The assignment covers theoretical concepts and practical implementations of key deep learning architectures.

## 📚 Assignment Overview

This homework consists of three main parts:

1. **Question 1**: Theoretical questions about deep learning concepts
2. **Question 2**: GAN implementation for MNIST digit generation
3. **Question 3**: RNN with and without attention for sentiment classification

---

## 🎯 Question 1: Theoretical Deep Learning Concepts

**File**: [`question-1/question-1.md`](question-1/question-1.md)

### Topics Covered:

- **Transfer Learning Limitations**: Why pre-trained models on ImageNet may fail on medical imaging data
- **Layer Comparison**: Fully Connected vs Convolutional layers analysis
- **Regularization Techniques**: Methods to prevent overfitting in deep networks
- **Siamese Networks**: Architecture and applications for similarity learning
- **Activation Functions**: Comparison of ReLU, Sigmoid, and Tanh functions

### Key Insights:

- Domain gap challenges between natural and medical images
- Parameter efficiency and overfitting risks in different layer types
- Regularization strategies for deep neural networks
- Attention mechanisms and interpretability in neural networks

---

## 🤖 Question 2: GAN Implementation for MNIST Generation

**File**: [`question-2/question-2.ipynb`](question-2/question-2.ipynb)

### Implementation Details:

- **Generator Network**: Fully connected layers with ReLU and Tanh activations
- **Discriminator Network**: Binary classifier with LeakyReLU and Sigmoid
- **Training Strategy**: Alternating training with Binary Cross Entropy loss
- **Dataset**: MNIST handwritten digits (60,000 training samples)

### Key Features:

- Progressive image generation visualization every 5 epochs
- Training loss curves for both generator and discriminator
- Mode collapse analysis and interpolation studies
- Comprehensive hyperparameter tuning

### Generated Outputs:

- **Training Progress**: Images generated at epochs 1, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50
- **Final Results**: High-quality digit generation after 50 epochs
- **Analysis Plots**: Training curves, interpolation analysis, and final generated digits

### Files Generated:

- `generator_final.pt` - Trained generator model
- `discriminator_final.pt` - Trained discriminator model
- `training_curves.png` - Loss visualization
- `final_generated_digits.png` - Best quality outputs
- `interpolation_analysis.png` - Latent space exploration

---

## 🧠 Question 3: RNN with Attention for Sentiment Analysis

**File**: [`question-3/question-3.ipynb`](question-3/question-3.ipynb)

### Implementation Details:

- **Baseline Model**: GRU-based classifier using final hidden state
- **Attention Model**: GRU with additive attention mechanism
- **Dataset**: IMDb sentiment dataset (positive/negative reviews)
- **Architecture**: Embedding → GRU → Attention → Classification

### Key Features:

- Comparative analysis between baseline and attention models
- Attention weight visualization and heatmaps
- Confidence analysis and model interpretability
- Comprehensive training and evaluation metrics

### Generated Outputs:

- **Model Comparison**: Performance metrics and training curves
- **Attention Visualizations**: Heatmaps showing word importance
- **Detailed Analysis**: Sample-specific attention patterns
- **Confidence Analysis**: Model prediction confidence distributions

### Files Generated:

- `baseline_gru_model.pt` - Baseline GRU model
- `attention_gru_model.pt` - GRU with attention model
- `model_comparison.png` - Performance comparison
- `attention_heatmaps.png` - Attention weight visualizations
- `confidence_analysis.png` - Prediction confidence analysis

---

## 🛠️ Technical Requirements

### Environment Setup:

- **Python Version**: 3.12
- **Platform**: Windows 11 with WSL 2
- **Package Manager**: Anaconda

### Dependencies:

```bash
torch>=2.0.0
torchvision>=0.15.0
matplotlib>=3.5.0
numpy>=1.21.0
pandas>=1.3.0
seaborn>=0.11.0
scikit-learn>=1.0.0
```

### Installation:

```bash
# Clone the repository
git clone <[your-repo-url](https://github.com/sina-ss/deep-learning-hw3)>
cd deep-learning-hw3

# Install dependencies
pip install -r requirements.txt

# Or using conda
conda install pytorch torchvision -c pytorch
conda install matplotlib numpy pandas seaborn scikit-learn
```

---

## 📁 Repository Structure

```
deep-learning-hw3/
├── README.md
├── question-1/
│   ├── question-1.md          # Theoretical answers
│   └── question-1.pdf         # PDF version
├── question-2/
│   ├── question-2.ipynb       # GAN implementation
│   ├── data/                  # MNIST dataset
│   ├── generated_images/      # Progressive generation results
│   ├── *.pt                   # Trained models
│   └── *.png                  # Analysis plots
└── question-3/
    ├── question-3.ipynb       # RNN + Attention implementation
    ├── attention_visualizations/  # Attention heatmaps
    ├── *.pt                   # Trained models
    └── *.png                  # Analysis plots
```

---

## 🚀 Usage Instructions

### Running Question 2 (GAN):

```bash
cd question-2
jupyter notebook question-2.ipynb
```

- Execute all cells to train the GAN
- Generated images will be saved in `generated_images/` folder
- Training progress and final results will be displayed

### Running Question 3 (RNN + Attention):

```bash
cd question-3
jupyter notebook question-3.ipynb
```

- Execute all cells to train both models
- Attention visualizations will be saved in `attention_visualizations/` folder
- Model comparison and analysis plots will be generated

---

## 📊 Key Results and Insights

### GAN Training:

- **Epoch 1**: Basic noise patterns
- **Epoch 25**: Recognizable digit shapes
- **Epoch 50**: High-quality, diverse digit generation
- **Mode Collapse**: Successfully avoided through proper training balance

### Attention Mechanism:

- **Baseline GRU**: ~85% accuracy
- **GRU + Attention**: ~89% accuracy
- **Interpretability**: Clear visualization of important words
- **Performance**: Consistent improvement across different review lengths

---

## 🔬 Technical Highlights

### GAN Architecture:

- **Generator**: 100 → 128 → 784 (28×28 pixels)
- **Discriminator**: 784 → 128 → 1 (binary classification)
- **Optimization**: Adam optimizer with β₁ = 0.5
- **Loss Function**: Binary Cross Entropy

### RNN Architecture:

- **Embedding**: 5000 vocabulary → 128 dimensions
- **GRU**: 2 layers, 256 hidden units
- **Attention**: Additive attention mechanism
- **Classification**: Binary sentiment prediction

---

## 📝 Submission Details

- **Student Name**: سینا سپهوند (Sina Sepahvand)
- **Student ID**: 4032904001
- **Course**: Deep Learning
- **Semester**: Second Semester 1403-1404
- **Deadline**: 9 days after final exam

---

## 🤝 Contributing

This is a homework submission repository. For questions or discussions about the implementations, please refer to the course materials or contact the course instructor.

---

## 📄 License

This repository is created for educational purposes as part of a university course assignment. All code and content are original work unless otherwise specified.

---

## 🔗 Related Resources

- [PyTorch Documentation](https://pytorch.org/docs/)
- [GAN Paper by Goodfellow et al.](https://arxiv.org/abs/1406.2661)
- [Attention Mechanism Paper](https://arxiv.org/abs/1409.0473)
- [MNIST Dataset](http://yann.lecun.com/exdb/mnist/)
- [IMDb Dataset](https://ai.stanford.edu/~amaas/data/sentiment/)
