FROM mcr.microsoft.com/devcontainers/python:3.12

ENV PIP_DISABLE_PIP_VERSION_CHECK=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

RUN pip3 install --no-cache-dir --upgrade pip && \
    pip3 install --no-cache-dir \
      numpy pandas scipy matplotlib seaborn plotly \
      jupyterlab ipykernel \
      fastapi uvicorn flask gunicorn requests httpx pydantic[dotenv] \
      black ruff mypy pytest pytest-cov tox pre-commit \
      rich typer uv

WORKDIR /workspaces

