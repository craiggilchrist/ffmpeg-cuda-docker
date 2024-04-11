# Start with the NVIDIA base image with FFMPEG installed.
FROM jrottenberg/ffmpeg:7.0-nvidia2204

# Install wget
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        wget \
    && rm -rf /var/lib/apt/lists/*

# Add the Microsoft package repository.
RUN wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb \
    && dpkg -i packages-microsoft-prod.deb \
    && rm packages-microsoft-prod.deb

# Install .NET runtime
RUN apt-get update \
    && apt-get install -y --no-install-recommends dotnet-runtime-8.0 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/*