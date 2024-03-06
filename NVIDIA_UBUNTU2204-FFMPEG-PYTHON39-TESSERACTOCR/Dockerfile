# Start with the NVIDIA base image with FFMPEG installed.
FROM craiggilchrist/ffmpeg-cuda:12.3.1-runtime-ubuntu22.04

# Install python 3.9 prereqs, Python 3.9, pip, distutils, python3.9-distutils, Tesseract OCR, and its dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
        software-properties-common \
        tesseract-ocr \
        libtesseract-dev \
    && add-apt-repository ppa:deadsnakes/ppa \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
        python3.9 \
        python3-pip \
        python3-distutils \
        python3.9-distutils \
    # Clean up in the same layer to reduce image size
    && rm -rf /var/lib/apt/lists/* \
    # Symlink python3.9 to python for convenience
    && ln -s /usr/bin/python3.9 /usr/bin/python
