# Neural Network Fundamentals - MNIST
[Readme Spanish version](README_es.md)

This repository contains a **Neural Network** project implemented from scratch in **NumPy**, focused on the MNIST dataset for digit recognition. The goal is to delve into each part of the network architecture, manually implementing the **forward pass** and **backward pass** without using high-level frameworks like TensorFlow or PyTorch.

![alt text](image.png)

---

## File and Folder Structure

```
NeuralNetwork-Fundamentals-MNIST/
├─ MNIST_db/
│  ├─ process_MNIST.ipynb
│  └─ raw/
│     ├─ t10k-images-idx3-ubyte.gz
│     ├─ t10k-labels-idx1-ubyte.gz
│     ├─ train-images-idx3-ubyte.gz
│     └─ train-labels-idx1-ubyte.gz
├─ README.md
├─ RedNeuronal.ipynb
├─ get_images_script.py
```

- **`RedNeuronal.ipynb`**  
  The main notebook where:
  - MNIST data is loaded (using `get_images_script.py`).
  - Data is normalized and split into training, validation, and test sets.
  - Classes `Linear`, `ReLU`, `Sequential_layers`, and the auxiliary `np_tensor` are defined.
  - The neural network is trained.
  - Results and accuracy are evaluated.

- **`get_images_script.py`**  
  This script contains the function `get_images(mnist_raw_path)`, responsible for loading the MNIST files from the folder `MNIST_db/raw/` and returning NumPy arrays with images and labels.

- **`MNIST_db/raw/`**  
  This folder contains the compressed MNIST files (`.gz`):  
  - `train-images-idx3-ubyte.gz`, `train-labels-idx1-ubyte.gz`  
  - `t10k-images-idx3-ubyte.gz`, `t10k-labels-idx1-ubyte.gz`

- **`MNIST_db/process_MNIST.ipynb`**  
  An additional (optional) notebook which may contain some preprocessing or details on how to obtain the `.gz` files and convert them into arrays.

---

## Usage Instructions

1. **Clone** the repository:
   ```bash
   git clone https://github.com/PabloSanchez87/NeuralNetwork-Fundamentals-MNIST.git
   ```
2. **Install** the required dependencies (ideally within a virtual environment):
   ```bash
   pip install numpy matplotlib jupyterthemes
   ```
3. **Verify** that the MNIST files (`.gz`) are in the `MNIST_db/raw` folder.  
4. **Open** the main notebook:
   ```bash
   jupyter notebook RedNeuronal.ipynb
   ```
5. **Run** the notebook cells in order:
   - It will load and decompress the MNIST images.
   - It will show the normalization process and the network architecture.
   - It will begin training, and you can watch the cost and accuracy progress on-screen.

---

## Neural Network Overview

- **Architecture**:  
  - A dense `Linear(784, 200)` layer with a `ReLU` activation.  
  - A dense `Linear(200, 10)` layer for classification into 10 digit classes (0-9).

- **Loss Function**:  
  - `softmax` + cross-entropy.

- **Manual Backprop**:
  - Each gradient is implemented in `Linear.backward` and `ReLU.backward`.
  - A `np_tensor` class is used to manage the `.grad` attribute, simplifying gradient calculations without automatic frameworks.

- **Training**:
  - A mini-batch generator (`create_minibatches`) is defined to process data in batches.
  - In each epoch, gradients are calculated and weights are updated with **gradient descent**.

---

## Expected Results

When running the code in `RedNeuronal.ipynb`, you will see output similar to:
```
Epoch 1 - Cost: 0.35, accuracy: 0.90
Epoch 2 - Cost: 0.27, accuracy: 0.92
...
Epoch 20 - Cost: 0.10, accuracy: 0.96
```
The network can reach around **96-97%** accuracy on the validation set with this simple architecture.

---

## Customization

- **Layers**: You can add more `Linear` + `ReLU` layers to build a deeper network.
- **Hyperparameters**: Adjust the learning rate, mini-batch size (`mb_size`), number of epochs, etc.
- **Preprocessing**: Modify normalization or apply data augmentation techniques (less common in MNIST but still possible).

---

## Acknowledgments

- Special thanks to the [Pepe Cantoral PhD](https://www.youtube.com/@PepeCantoralPhD) YouTube channel for providing helpful videos and insights that guided the creation of this project.

---

## Contributions

If you would like to **contribute**, feel free to open an issue for suggestions or submit a pull request with improvements or fixes.

---
