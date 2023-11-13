# Start with the NVIDIA base image.
FROM nvidia/cuda:12.3.0-devel-ubuntu22.04

# Ignore input prompts.
ENV DEBIAN_FRONTEND noninteractive

# Update NVIDIA keys and sources as required for the specific CUDA and Ubuntu version
RUN apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/3bf863cc.pub

# Install necessary dependencies
RUN apt-get update && apt-get install -y \
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
  zlib1g-dev

# Clone and install nv-codec-headers
RUN git clone https://github.com/FFmpeg/nv-codec-headers.git && cd nv-codec-headers && git checkout n12.1.14.0 && make install && cd ..

# Clone, configure, and install FFMPEG
RUN git clone https://git.ffmpeg.org/ffmpeg.git && cd ffmpeg && git checkout n6.1 \
  && ./configure --enable-nonfree --enable-cuda --enable-cuvid --enable-nvenc --enable-nonfree --enable-libnpp --enable-opencl --enable-gpl \
  --enable-libmp3lame --enable-libx264 --enable-libx265 --enable-libvpx \
  --extra-cflags=-I/usr/local/cuda/include --extra-ldflags=-L/usr/local/cuda/lib64 \
  && make -j$(nproc) && make install && cd .. && ffmpeg -codecs 

# Cleanup
RUN rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* ./nv-codec-headers ./ffmpeg