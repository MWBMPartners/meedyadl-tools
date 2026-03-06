# MeedyaDL Tools Mirror

Pre-built tool binaries for the MeedyaDL dependency manager's mirror fallback system.

## Purpose

When MeedyaDL's primary upstream download sources fail (404, timeout, naming changes, etc.), the dependency manager falls back to downloading pre-built binaries from this repository's GitHub Releases.

## Asset Naming Convention

Assets follow a standardized naming pattern:

```
{tool_id}-{os}-{arch}.{ext}
```

| Field     | Values                                      |
|-----------|---------------------------------------------|
| `tool_id` | `ffmpeg`, `mp4decrypt`, `nm3u8dlre`, `mp4box` |
| `os`      | `linux`, `windows`, `macos`                 |
| `arch`    | `x86_64`, `aarch64`                         |
| `ext`     | `.tar.gz` (Linux/macOS), `.zip` (Windows)   |

### Current Assets

| Tool | Linux x86_64 | Linux aarch64 | Windows x86_64 | macOS x86_64 | macOS aarch64 |
|------|:---:|:---:|:---:|:---:|:---:|
| MP4Box | Yes | Yes | Yes | Yes | Yes |
| FFmpeg | Yes | Yes | Yes | Yes | - |
| mp4decrypt | Yes | - | Yes | Yes (universal) | Yes (universal) |
| N_m3u8DL-RE | Yes | Yes | Yes | - | - |

## Automated Builds

A GitHub Actions workflow (`.github/workflows/build-tools.yml`) automates the download, packaging, and upload of all tool binaries:

- **Weekly schedule** — runs every Sunday at 04:00 UTC to pick up upstream updates
- **Manual dispatch** — trigger via GitHub UI or CLI with optional per-tool filter:
  ```bash
  gh workflow run "Build Tools" --repo MWBMPartners/meedyadl-tools -f tool=all
  gh workflow run "Build Tools" --repo MWBMPartners/meedyadl-tools -f tool=mp4box
  ```

### Build Sources

| Tool | Source |
|------|--------|
| MP4Box | `apt install gpac` (Linux), Homebrew (macOS), GPAC NSIS installer (Windows) |
| FFmpeg | johnvansickle.com static builds (Linux), BtbN/FFmpeg-Builds (Windows), evermeet.cx (macOS) |
| mp4decrypt | nicoboss/bento4-binaries GitHub Releases |
| N_m3u8DL-RE | nilaoda/N_m3u8DL-RE GitHub Releases |

## Release Tag

MeedyaDL's `tool-versions.toml` references the `latest` release tag. All mirror assets are uploaded to this release.

## Related

- [MeedyaDL](https://github.com/MWBMPartners/MeedyaDL) — The main application
- `tool-versions.toml` in MeedyaDL defines the mirror configuration
