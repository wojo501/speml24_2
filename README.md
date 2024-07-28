# speml_2
Security, Privacy and Explainability in Machine Learning Project 2

## Concept
https://www.overleaf.com/project/667698126de13b05d1732edb

## CIFAR - 10 database
https://www.cs.toronto.edu/~kriz/cifar.html
10 classes, 6000 img/class

## How to run project?
Option A: Run in devcontainer in your favorite IDE https://containers.dev/
Option B: Manual Install

1. Install ffmpeg V4.4 (dependency of syft 0.2.9):

```
wget https://ffmpeg.org/releases/ffmpeg-4.4.tar.bz2
tar xjf ffmpeg-4.4.tar.bz2
cd ffmpeg-4.4
./configure --prefix=/usr/local --disable-debug --disable-doc --disable-ffplay --enable-shared --enable-avresample --enable-gpl --disable-x86asm
make
sudo make install
sudo ldconfig
```

2. create conda environment with:
```conda env create -f environment.yml```

for updating environment run:
```conda env update -f environment.yml```

if this is not working use command:
```conda create --name speml24_2 --file packages.txt```

3. create .env file in speml24_2 directory with:
WANDB_KEY = "" 
<!-- key from wandb -->
ENTITY=""
<!-- name of your wandb user -->


TO-DO:
1. comparison between traditional and federated approach
2. report 
