FROM mcr.microsoft.com/devcontainers/cpp:ubuntu-24.04

RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential clang clang-tidy clang-format lldb gdb valgrind \
    cmake ninja-build ccache pkg-config python3-pip \
 && pip3 install --no-cache-dir 'conan>=2,<3' \
 && rm -rf /var/lib/apt/lists/*

ENV CC=clang CXX=clang++

WORKDIR /workspaces

