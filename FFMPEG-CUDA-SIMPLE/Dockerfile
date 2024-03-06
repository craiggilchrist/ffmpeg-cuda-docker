FROM nvidia/cuda:12.3.1-base-ubuntu22.04

ENV DEBIAN_FRONTEND noninteractive

# Combine apt-get update, install, and cleanup steps
RUN apt-get update && apt-get install -y \
  cuda-toolkit-12-3 \
  build-essential \
  ca-certificates \
  curl \
  fonts-liberation \
  git \
  gnupg2 \
  libasound2 \
  libatk-bridge2.0-0 \
  libatk1.0-0 \
  libatspi2.0-0 \
  libcups2 \
  libgtk-3-0 \
  libmp3lame-dev \
  libnspr4 \
  libnss3 \
  libpng-dev \
  libu2f-udev \
  libvpx-dev \
  libvulkan1 \
  libx264-dev \
  libx265-dev \
  libxcomposite1 \
  libxdamage1 \
  nasm \
  pkgconf \
  unzip \
  wget \
  xdg-utils \
  yasm \
  zip \
  zlib1g-dev \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/*

# Install nv-codec-headers and FFMPEG in one layer, cleanup after
RUN git clone https://github.com/FFmpeg/nv-codec-headers.git && cd nv-codec-headers && git checkout n12.1.14.0 && make install && cd .. && rm -rf nv-codec-headers \
  && git clone https://git.ffmpeg.org/ffmpeg.git ffmpeg && cd ffmpeg && git checkout n6.1 \
  && ./configure --enable-nonfree --enable-cuda --enable-cuvid --enable-nvenc --enable-nonfree --enable-libnpp --enable-opencl --enable-gpl \
  --enable-libmp3lame --enable-libx264 --enable-libx265 --enable-libvpx \
  --extra-cflags=-I/usr/local/cuda/include --extra-ldflags=-L/usr/local/cuda/lib64 \
  && make -j$(nproc) && make install && cd .. && rm -rf ffmpeg
