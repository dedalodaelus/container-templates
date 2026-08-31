ARG CUDA_IMAGE=nvidia/cuda:13.0.3-devel-ubuntu24.04
FROM ${CUDA_IMAGE}

ENV DEBIAN_FRONTEND=noninteractive \
    PYTHONDONTWRITEBYTECODE=1 \
    PIP_NO_CACHE_DIR=1 \
    XDG_CACHE_HOME=/cache \
    HF_HOME=/cache/huggingface \
    TRITON_CACHE_DIR=/cache/triton \
    PATH=/opt/venv/bin:$PATH

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        python3 \
        python3-venv \
        python3-pip \
        ca-certificates \
        curl \
        git \
        build-essential \
        ninja-build && \
    rm -rf /var/lib/apt/lists/*

RUN python3 -m venv /opt/venv && \
    /opt/venv/bin/pip install --upgrade pip uv && \
    /opt/venv/bin/uv pip install \
        --python /opt/venv/bin/python \
        "freetoken[accel]"

RUN mkdir -p /cache

EXPOSE 1919

ENTRYPOINT ["ft"]
CMD ["serve"]