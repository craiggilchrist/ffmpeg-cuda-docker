# Start with the FFMPEG CUDA base image.
FROM craiggilchrist/ffmpeg-cuda:12.3

# Install .NET runtime
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
       dotnet-runtime-7.0 \
    && rm -rf /var/lib/apt/lists/*