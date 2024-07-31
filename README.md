# SPEML 2024 Group 16
Security, Privacy and Explainability in Machine Learning Project 2

## Dataset
CIFAR10
https://www.cs.toronto.edu/~kriz/cifar.html
10 classes, 6000 img/class

## Overview
Goal of the project is to compare centralised and federated learning for image classification.

## Architecture
Usage of Tensorflow Federated Learning Library (https://www.tensorflow.org/federated) with a simple CNN architecture:

1. Conv2D Layer: 20 filters of size 5x5, ReLU activation, input shape (32, 32, 3).
2. MaxPooling2D Layer: Pooling size 2x2.
3. Conv2D Layer: 50 filters of size 5x5, ReLU activation.
4. MaxPooling2D Layer: Pooling size 2x2.
5. Flatten Layer: Converts the 2D feature maps to 1D feature vectors.
6. Dense Layer: 500 neurons, ReLU activation.
7. Dense Layer: 10 neurons, Softmax activation for classification.

## Experiments
- Comparing Federated Learning to Centralised Learning
    - With different Optimizers
    - With different Hyperparameters (Federated Batch Size and Nr of Federated Clients)
- Differential Privacy (https://www.tensorflow.org/federated/tutorials/federated_learning_with_differential_privacy)
- Model and Update Compression (https://www.tensorflow.org/federated/tutorials/tff_for_federated_learning_research_compression)

## How to run project?
Requirements: Python 3.11

1. **Prepare Virtual Environment**

    ```
    python3.11 -m venv .venv
    source .venv/bin/activate
    pip install -r requirements.txt
    ```

2. **Run the Notebooks**

    With your favourite IDE or jupyter.

   - [Centralized Learning CIFAR-10 Notebook](./code/centralised_cifar10.ipynb)
   - [Federated Learning CIFAR-10 Notebook](./code/federated_cifar10.ipynb)

3. **Options**

    All Notebooks provide Hyperparameters in the second cell which can be changed to reproduce the experiments.
    
    Settings for Additional Experiments are marked in commented out code with the comment "EXPERIMENT"

4. **Reporting**

    All Notebooks provide logging to WANDB (https://wandb.ai/) which is turned off by default

## Troubleshooting
### Vscode
If using vscode it might throw the error on executing a cell: ``The file '.venv/lib/python3.11/site-packages/typing_extensions.py' seems to be overriding built in modules and interfering with the startup of the kernel. Consider renaming the file and starting the kernel again.
Click here for more info.``

Instead of renaming,``pip install -U typing-extensions`` also suffices

### Tensorflow
Tensorflow Federated has a Serialisation Limit of 100 MB by default.
If data to federated client is increased (e.g by reducing nr of workers below 10) the error `ValueError: Serialized size of Dataset (537613688 bytes) exceeds maximum allowed` might be thrown.

This can be fixed by changing the limit in file \<pythonenv\>/lib/python3.11/site-packages/tensorflow_federated/python/core/impl/executors/value_serialization.py

See: https://stackoverflow.com/questions/76407619/tensorflow-federated-increase-default-serialization-limit-bytes