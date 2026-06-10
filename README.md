# Wheelhouse

This is my personal general wheelhouse repository for prebuilt Python wheels.
This copy is used to store wheels for the Alps Clariden cluster.

## Layout

- `aarch64/torchcodec-0.8.0-cp312-cp312-linux_aarch64.whl`
- `aarch64/ffmpeg-7.1.1-full-aarch64/`

## TorchCodec 0.8.0 (linux_aarch64, cp312)

Wheel file:

- `aarch64/torchcodec-0.8.0-cp312-cp312-linux_aarch64.whl`

Compatibility:

- Platform: `linux_aarch64`
- Python: `3.12` (`cp312`)
- Built and tested with: `torch 2.9.0a0+50eac811a6.nv25.09`

## Install

Install from local clone path:

```bash
uv pip install --python /opt/venv/bin/python --no-deps \
  ./aarch64/torchcodec-0.8.0-cp312-cp312-linux_aarch64.whl
```

If you are already in this folder:

```bash
uv pip install --python /opt/venv/bin/python --no-deps \
  aarch64/torchcodec-0.8.0-cp312-cp312-linux_aarch64.whl
```

`--no-deps` is intentional so your existing `torch` install is not replaced.

## Verify

```bash
/opt/venv/bin/python -c "import torch, torchcodec; print('torch', torch.__version__); print('torchcodec', torchcodec.__version__)"
```

Expected:

- `torch` prints your current environment version
- `torchcodec` prints `0.8.0+...`

## xIELU CUDA 0.1.0 (linux_aarch64, cp313)

Fused CUDA xIELU activation for Apertus (forward + backward, learnable
alpha_p/alpha_n). Source: nathanrchn/kernels @ 185b512 + contiguity fix
(vendored in Nemo-RL `docker/xielu`). Kernel contract: bf16 only,
`numel % 128 == 0`; the Megatron-Bridge Apertus XIELU module guards both
and falls back to eager with a warning.

Wheel file:

- `aarch64/xielu-0.1.0-cp313-cp313-linux_aarch64.whl`

Compatibility:

- Platform: `linux_aarch64` (GH200, sm_90)
- Python: `3.13` (`cp313`)
- Built and tested with: `torch 2.10.0+cu129` (nemo-rl v0.6.0 image,
  `/opt/nemo_rl_venv`); also validated against `torch 2.10.0a0+nv25.11`

## Install

```bash
uv pip install --python /opt/nemo_rl_venv/bin/python --no-deps \
  ./aarch64/xielu-0.1.0-cp313-cp313-linux_aarch64.whl
```

## Verify

```bash
/opt/nemo_rl_venv/bin/python -c "import torch; from xielu import xielu; x=torch.randn(256,device='cuda').bfloat16(); a=torch.full((1,),0.5,device='cuda',dtype=torch.bfloat16); print('xielu ok', xielu(x,a,a,0.5,-1e-6).shape)"
```
