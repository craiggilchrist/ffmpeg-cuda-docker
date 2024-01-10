# Start with the NVIDIA base image with FFMPEG installed.
FROM craiggilchrist/ffmpeg-cuda:latest

# Install python 3.9 prereqs
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        software-properties-common \
    && rm -rf /var/lib/apt/lists/*

# Add the deadsnakes PPA to get python 3.9
RUN add-apt-repository ppa:deadsnakes/ppa

# Install python 3.9, pip, distutils and python3.9-distutils
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        python3.9 \
        python3-pip \
        python3-distutils \
        python3.9-distutils \
    && rm -rf /var/lib/apt/lists/* \
    && ln -s /usr/bin/python3.9 /usr/bin/python

# Install Tesseract OCR and its dependencies
RUN apt-get update \
    && apt-get install -y --no-install-recommends tesseract-ocr libtesseract-dev \
    && rm -rf /var/lib/apt/lists/*