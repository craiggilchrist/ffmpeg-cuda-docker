# Start with the NVIDIA base image with FFMPEG installed.
FROM jrottenberg/ffmpeg:5.0-nvidia2004

# Install python 3.9 prereqs
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        software-properties-common \
    && rm -rf /var/lib/apt/lists/*

# Add the deadsnakes PPA to get python 3.9
RUN add-apt-repository ppa:deadsnakes/ppa

# Install python 3.9 and pip
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        python3.9 \
        python3-pip \
    && rm -rf /var/lib/apt/lists/*