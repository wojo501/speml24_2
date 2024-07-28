# speml_2
Security, Privacy and Explainability in Machine Learning Project 2

## Concept
https://www.overleaf.com/project/667698126de13b05d1732edb

## CIFAR - 10 database
https://www.cs.toronto.edu/~kriz/cifar.html
10 classes, 6000 img/class

## How to run project?
```
python3.11 -m venv venv
source venv/bin/activate
pip install numpy ipykernel tensorflow-federated matplotlib
```

## Troubleshooting
Tensorflow Federated has a Serialisation Limit of 100 MB by default.
If Data to Federated Client is increases (e.g by reducing nr of workers) the error `ValueError: Serialized size of Dataset (537613688 bytes) exceeds maximum allowed` might be thrown.

This can be fixed by changing the limit in file <pythonenv>/lib/python3.11/site-packages/tensorflow_federated/python/core/impl/executors/value_serialization.py

See: https://stackoverflow.com/questions/76407619/tensorflow-federated-increase-default-serialization-limit-bytes