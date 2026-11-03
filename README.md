# Upsun CLI nightly builds

This repository hosts the nightly build of the [Upsun CLI](https://github.com/upsun/cli). It has no code of its own.

The build is made from the `main` branch of [upsun/cli](https://github.com/upsun/cli) every day that `main` has changed, by its [Nightly workflow](https://github.com/upsun/cli/blob/main/.github/workflows/nightly.yml). Each build replaces the assets of the [`nightly` prerelease](https://github.com/upsun/cli-nightly/releases/tag/nightly).

Nightly builds contain unreleased code and may be broken. Use them to try changes before they are released, not in production or automation.

## Install

On Linux, macOS, or the Windows Subsystem for Linux (WSL):

```console
curl -fsSL https://raw.githubusercontent.com/upsun/cli/main/installer.sh | VERSION=nightly bash
```

The installer downloads the binary (its `raw` method), into `/usr/bin` (`/usr/local/bin` on macOS) or a user directory, which may replace an existing install. To keep a stable install alongside it, set another directory, e.g. `INSTALL_DIR=$HOME/.local/bin/nightly`. For the installer's other options, see [docs/install.md](https://github.com/upsun/cli/blob/main/docs/install.md).

To go back to a stable release, reinstall it with your usual install method, and remove the nightly binary if it is in another directory.

## Download

Asset names have `nightly` in place of the version, so these URLs don't change:

```
https://github.com/upsun/cli-nightly/releases/download/nightly/<binary>_nightly_<os>_<arch>.<ext>
```

| Platform | Upsun CLI | Platform.sh CLI |
|---|---|---|
| Linux (x86-64) | `upsun_nightly_linux_amd64.tar.gz` | `platform_nightly_linux_amd64.tar.gz` |
| Linux (ARM64) | `upsun_nightly_linux_arm64.tar.gz` | `platform_nightly_linux_arm64.tar.gz` |
| macOS (universal) | `upsun_nightly_darwin_all.tar.gz` | `platform_nightly_darwin_all.tar.gz` |
| Windows (x86-64) | `upsun_nightly_windows_amd64.zip` | `platform_nightly_windows_amd64.zip` |

The release also has:

- `checksums.txt`: SHA-256 checksums of the archives, e.g. `sha256sum --check --ignore-missing checksums.txt`
- `commit.txt`: the upsun/cli commit the build is from

Assets are replaced one by one, so a download made while a build is being published may not match `checksums.txt`. Retry a few minutes later.

## Versions

A nightly's version is the next patch version, with the date and commit, e.g. `5.15.3-nightly.20261103+abc1234ef`. It sorts after the latest stable release and before the next one, so the CLI's update check tells you when a newer stable release is out.

## Feedback

Report problems in [upsun/cli issues](https://github.com/upsun/cli/issues), with the output of `upsun --version`.
