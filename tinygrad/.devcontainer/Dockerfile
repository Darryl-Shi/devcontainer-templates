FROM python:3.12-slim

ENV DEBIAN_FRONTEND=noninteractive \
    PIP_DISABLE_PIP_VERSION_CHECK=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

RUN apt-get update && apt-get install -y --no-install-recommends \
    git build-essential pkg-config python3-dev \
 && rm -rf /var/lib/apt/lists/*

# Tinygrad + useful deps
RUN pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir tinygrad numpy pillow rich ipdb pytest ruff black mypy

# Optional: enable OpenCL support (uncomment if desired)
# RUN apt-get update && apt-get install -y --no-install-recommends \
#     ocl-icd-opencl-dev clinfo && \
#     rm -rf /var/lib/apt/lists/*

WORKDIR /workspaces

