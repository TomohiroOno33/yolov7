FROM nvcr.io/nvidia/pytorch:21.08-py3

WORKDIR /workdir

ENV DEBIAN_FRONTEND=noninteractive

# nvidia-container-runtime
ENV NVIDIA_VISIBLE_DEVICES ${NVIDIA_VISIBLE_DEVICES:-all}
ENV NVIDIA_DRIVER_CAPABILITIES ${NVIDIA_DRIVER_CAPABILITIES:+$NVIDIA_DRIVER_CAPABILITIES,}graphics

# install apt
RUN apt update && \
    apt install -y --no-install-recommends \
    zip htop screen libgl1-mesa-glx && \
    rm -rf /var/lib/apt/lists/*

# install pip
ADD requirements.txt /workdir
RUN pip install -U pip && \
    pip install -r requirements.txt && \
    rm requirements.txt