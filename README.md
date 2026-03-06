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

### Example Assets

```
ffmpeg-linux-x86_64.tar.gz
ffmpeg-windows-x86_64.zip
mp4decrypt-macos-aarch64.zip
nm3u8dlre-linux-x86_64.tar.gz
mp4box-linux-aarch64.tar.gz
mp4box-windows-x86_64.zip
```

## Release Tag

MeedyaDL's `tool-versions.toml` references the `latest` release tag. All mirror assets should be uploaded to this release.

## Adding Assets

1. Build or obtain the tool binary for the target platform
2. Package it in a `.tar.gz` (Unix) or `.zip` (Windows) archive
3. Name it following the convention above
4. Upload to the `latest` GitHub Release

## Related

- [MeedyaDL](https://github.com/MWBMPartners/MeedyaDL) - The main application
- `tool-versions.toml` in MeedyaDL defines the mirror configuration
