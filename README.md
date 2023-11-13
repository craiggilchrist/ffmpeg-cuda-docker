# ffmpeg-cuda-docker
 Docker base images with CUDA support for various functions.

 ## Image details
 The docker images are based on the latest nvidia/cuda ubuntu 22.04 image and includes ffmpeg cloned and built from [https://git.ffmpeg.org/ffmpeg.git](https://git.ffmpeg.org/ffmpeg.git). FFMPEG is built with the following options:
 - enable-nonfree
 - enable-cuda
 - enable-cuvid
 - enable-nvenc
 - enable-nonfree
 - enable-libnpp
 - enable-opencl
 - enable-gpl
 - enable-libmp3lame
 - enable-libx264
 - enable-libx265
 - enable-libvpx
 - extra-cflags=-I/usr/local/cuda/include
 - extra-ldflags=-L/usr/local/cuda/lib64

 ## Docker hub list
 The following images are available in docker hub:
 - [craiggilchrist/ffmpeg-cuda:12.3](https://hub.docker.com/repository/docker/craiggilchrist/ffmpeg-cuda/general) - nvidia/cuda:12.3.0-devel-ubuntu22.04 base image with FFMPEG installed. Corresponds to the [FFMPEG-CUDA-12.3/Dockerfile](FFMPEG-CUDA-12.3/Dockerfile)
 - [craiggilchrist/ffmpeg-cuda-net-7.0:12.3](https://hub.docker.com/repository/docker/craiggilchrist/ffmpeg-cuda-net-7.0/general) - ncraiggilchrist/ffmpeg-cuda:12.3 base image with the .NET 7.0 runtime installed. Corresponds to the [FFMPEG-CUDA-12.3-NET-7.0/Dockerfile](FFMPEG-CUDA-12.3-NET-7.0/Dockerfile)