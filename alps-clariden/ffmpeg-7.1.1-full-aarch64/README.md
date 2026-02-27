# FFmpeg Runtime (Alps Clariden)

This folder stores a full FFmpeg 7.1.1 runtime built for linux_aarch64.

Path:

- `/capstor/store/cscs/swissai/infra01/MLLM/wheelhouse/alps-clariden/ffmpeg-7.1.1-full-aarch64`

Usage:

```bash
export FFMPEG_ROOT=/capstor/store/cscs/swissai/infra01/MLLM/wheelhouse/alps-clariden/ffmpeg-7.1.1-full-aarch64
export PKG_CONFIG_PATH=$FFMPEG_ROOT/lib/pkgconfig:${PKG_CONFIG_PATH:-}
export LD_LIBRARY_PATH=$FFMPEG_ROOT/lib:${LD_LIBRARY_PATH:-}

$FFMPEG_ROOT/bin/ffmpeg -version
$FFMPEG_ROOT/bin/ffmpeg -protocols | rg 'file|pipe'
```

Build notes:

- version: `7.1.1`
- arch: `aarch64`
- shared libs enabled
- includes standard protocols/demuxers/decoders (non-skeleton build)
