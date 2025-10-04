DevPod DevContainer Templates

This repo provides ready‑to‑use devcontainer templates for your most-used stacks, designed to run with DevPod locally or on your Tailscale SSH provider (root@100.73.233.42). Pick a stack folder as your workspace root when running DevPod.

Stacks
- pytorch-cuda — CUDA-enabled PyTorch (GPU on remote). Includes numpy/pandas/scipy/matplotlib/jupyter + tooling.
- tinygrad — Minimal Python + tinygrad and common dev tools (CPU by default; can enable GPU).
- python — General Python dev with data/web packages (pandas/numpy/fastapi/flask/etc.).
- cpp — C/C++ with gcc/clang/cmake/ninja/gdb/valgrind/ccache + Conan 2.
- rust — Rust toolchain with clippy/rustfmt and common cargo tools.

Quick start (DevPod CLI)
```bash
# Local (docker-local)
devpod up devpod-devcontainers/python --provider docker-local

# Remote with GPU (tailscale-ssh)
devpod up devpod-devcontainers/pytorch-cuda --provider tailscale-ssh
```

DevPod Desktop
- Create a workspace and select the folder of the stack you want (e.g. devpod-devcontainers/pytorch-cuda).
- Choose `docker-local` for local or `tailscale-ssh` for your Tailscale machine.

GPU notes (PyTorch / optional Tinygrad)
- The `pytorch-cuda` template adds `runArgs: ["--gpus=all", "--shm-size=1g"]` so the container gets your NVIDIA GPUs when run on the remote.
- Your remote host must have NVIDIA drivers + nvidia-container-toolkit installed and configured for Docker.
- To enable GPU for Tinygrad as well, add `"--gpus=all"` to its `runArgs` or run it on a machine without GPU for CPU-only.

Ports
- Python stacks forward common ports: 8888 (Jupyter), 5000 (Flask), 8000 (FastAPI/Uvicorn).

Tips
- If you want per-project Python virtualenvs, keep them in the workspace (e.g. `.venv`) and set VS Code Python: `python.defaultInterpreterPath=.venv/bin/python`.
- To reduce container bloat, the images install essential tooling and commonly used packages only. Adjust Dockerfiles as needed.

