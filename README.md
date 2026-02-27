# Wheelhouse

This is my personal general wheelhouse repository for prebuilt Python wheels.
This copy is used to store wheels for the Alps Clariden cluster.

## TorchCodec 0.8.0 (linux_aarch64, cp312)

Wheel file:

- `torchcodec-0.8.0-cp312-cp312-linux_aarch64.whl`

Compatibility:

- Platform: `linux_aarch64`
- Python: `3.12` (`cp312`)
- Built and tested with: `torch 2.9.0a0+50eac811a6.nv25.09`

## Install

Install from local clone path:

```bash
uv pip install --python /opt/venv/bin/python --no-deps \
  ./torchcodec-0.8.0-cp312-cp312-linux_aarch64.whl
```

If you are already in this folder:

```bash
uv pip install --python /opt/venv/bin/python --no-deps \
  torchcodec-0.8.0-cp312-cp312-linux_aarch64.whl
```

`--no-deps` is intentional so your existing `torch` install is not replaced.

## Verify

```bash
/opt/venv/bin/python -c "import torch, torchcodec; print('torch', torch.__version__); print('torchcodec', torchcodec.__version__)"
```

Expected:

- `torch` prints your current environment version
- `torchcodec` prints `0.8.0+...`
