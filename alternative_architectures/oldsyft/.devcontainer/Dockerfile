FROM mcr.microsoft.com/devcontainers/python:3.8

# Copy the environment.yml file into the container
# COPY environment.yml /tmp/environment.yml

# Create the conda environment
# RUN mamba env create -f /tmp/environment.yml

# RUN apt-get update && apt-get install -y \
#     libavcodec-dev \
#     libavformat-dev \
#     libavutil-dev \
#     libavfilter-dev \
#     libswscale-dev \
#     libswresample-dev \
#     libavdevice-dev
    
COPY ffmpeg-4-compiled.tar.gz /tmp/ffmpeg-4-compiled.tar.gz
RUN tar -xzf /tmp/ffmpeg-4-compiled.tar.gz -C /tmp && \
    cd /tmp/ffmpeg-4.4 && \
    make install && \
    ldconfig

ENV DISPLAY=:0