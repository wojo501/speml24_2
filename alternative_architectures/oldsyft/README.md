## OldSyft Architecture
Pysyft removed out of the box support for federated learning in 0.3 (See https://github.com/OpenMined/PySyft/issues/7384)
Current version of Pysyft is 0.8.x.

Therefore we create an old environment (state-of-the-art about 2018) based on Python 3.8 and Pytorch 0.4, where Federated Learning was still supported

## How to run project?
Unfortunately modern resolvers like conda, but also pip cannot resolve this setup because of a dependency to ffmpeg 4.4.
Therefore we prepare a compiled version of ffmpeg for installation in a devcontainer.

### Option A: Devcontainer
Run this subfolder in a devcontainer in your favorite IDE with devcontainer support https://containers.dev/. All files are provided here.

As a post command installation of the environment is executed with mamba (a drop in replacement for conda)
The base environment should then be ready to run the fed_learning notebook with your ide.

###  Option B: Manual Install
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

## Wandb Support
For Wandb support create .env file with:
WANDB_KEY = "" 
<!-- key from wandb -->
ENTITY=""
<!-- name of your wandb user -->