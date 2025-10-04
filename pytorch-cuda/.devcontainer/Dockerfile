FROM nvidia/cuda:12.1.1-cudnn8-runtime-ubuntu22.04

ENV DEBIAN_FRONTEND=noninteractive \
    PIP_DISABLE_PIP_VERSION_CHECK=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 python3-pip python3-venv \
    git curl ca-certificates build-essential \
 && rm -rf /var/lib/apt/lists/*

# PyTorch (CUDA 12.1 wheels) + data science + dev tooling
RUN python3 -m pip install --upgrade pip && \
    pip3 install --no-cache-dir --index-url https://download.pytorch.org/whl/cu121 \
        torch torchvision torchaudio && \
    pip3 install --no-cache-dir \
        numpy pandas scipy matplotlib seaborn pillow tqdm jupyterlab ipykernel \
        pytorch-lightning \
        black ruff mypy pytest ipdb rich

WORKDIR /workspaces

