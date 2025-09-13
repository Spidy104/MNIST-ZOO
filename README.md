# MNIST Model Zoo 🧠✨

A collection of models trained on the MNIST handwritten digit dataset, comparing different neural architectures and training objectives:

- **MLP** — classic fully-connected baseline  
- **Sparse Autoencoder + Classifier** — learns sparse representations with KL sparsity penalty  
- **Denoising Autoencoder + Classifier** — learns robust features by reconstructing clean digits from noisy inputs  
- **CNN** — convolutional baseline, the strongest performer  

---

## Results (Validation Accuracies)

| Model           | Accuracy (%) |
|-----------------|--------------|
| MLP             | 95.54        |
| Sparse AE + clf | 76.89        |
| DAE + clf       | 96.70        |
| CNN             | **99.25**    |

The CNN achieves the best accuracy, as expected, but the autoencoders provide insights into representation learning and robustness.

---

## Repository Structure

```
.
├── notebook*.ipynb          # Jupyter notebooks for training and evaluation
├── *.pth        # Saved model weights for the various models
├── data/              # MNIST dataset (auto-downloaded)
├── README.md
└── .gitignore
```

---

## How to Run

1. **Install dependencies:**
   ```bash
   pip install torch torchvision matplotlib seaborn scikit-learn
   ```

2. **Open the notebook:**
   ```bash
   jupyter notebook
   ```

3. **Run cells** to train models or load pre-trained checkpoints.

---

## What You'll See

### Visuals
* **Loss & accuracy curves** for each model during training
* **Reconstruction plots** showing how autoencoders learn to recreate digits
* **Confusion matrices** revealing where models struggle most
* **Bar chart comparison** of final validation accuracies across all models

### Key Insights
* **CNNs dominate** on image tasks due to translation invariance and local feature detection
* **Denoising autoencoders** learn surprisingly robust features, nearly matching MLP performance
* **Sparse autoencoders** sacrifice accuracy for interpretable representations
* **MLPs** provide a solid baseline but can't compete with convolutional architectures

---

## Model Details

### MLP (Multi-Layer Perceptron)
- Simple feedforward network with ReLU activations
- Flattens 28×28 images to 784-dimensional vectors
- Good baseline but ignores spatial structure

### Sparse Autoencoder + Classifier
- Two-stage training: first learn sparse features, then classify
- KL divergence penalty encourages sparse activations
- Lower accuracy but potentially more interpretable features

### Denoising Autoencoder + Classifier  
- Trained to reconstruct clean images from noisy versions
- Learns robust feature representations
- Strong performance showing the value of denoising objectives

### CNN (Convolutional Neural Network)
- Leverages spatial structure with convolutions and pooling
- Translation-invariant feature detection
- State-of-the-art results on MNIST

---

## Next Steps

* Try **Fashion-MNIST** to see how the models generalize beyond digits
* Add **robustness checks** (evaluate under noise, occlusion, rotations)
* Experiment with **deeper CNNs** or regularization tricks for >99.4% accuracy
* Implement **Vision Transformers** for comparison with modern architectures
* Add **model interpretability** tools (GradCAM, feature visualization)

---

## Requirements

- Python 3.7+
- PyTorch
- torchvision
- matplotlib
- seaborn
- scikit-learn
- jupyter

---

## License

MIT License - feel free to use this code for learning and experimentation!