FROM mcr.microsoft.com/devcontainers/rust:1

RUN rustup component add rustfmt clippy && \
    cargo install --locked cargo-edit cargo-watch cargo-nextest cargo-audit || true

RUN apt-get update && apt-get install -y --no-install-recommends \
    pkg-config build-essential cmake git \
 && rm -rf /var/lib/apt/lists/*

WORKDIR /workspaces

