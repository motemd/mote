# mote

**A native live Markdown editor for Linux.** Edit in place like Typora, without a web engine: nothing runs while you read, typing uses a fraction of one core, and the file on disk stays exactly what you typed.

Website and docs: **[motemd.com](https://motemd.com)** · Public beta, free until 1.0.

This repository is the product home — releases, issues, discussions and the security policy. The source is not public; the [benchmark harness](https://motemd.com/benchmarks) is.

## Install

| Form | Where it runs | How |
|---|---|---|
| **apt repository** (.deb) | Ubuntu 24.04+, Debian 13+ | see below |
| **.deb** | Ubuntu 24.04+, Debian 13+ | [Releases](https://github.com/motemd/mote/releases) → `sudo apt install ./mote_<version>_amd64.deb` |
| **AppImage** | Ubuntu 22.04+, any glibc 2.35+ distribution | download, `chmod +x`, run |
| **Terminal install** (tarball, no root) | Ubuntu 22.04+, any glibc 2.35+ distribution | `curl -fsSL https://get.motemd.com/install.sh \| sh` |
| **Flatpak** | any distribution | Flathub — submitted, pending review |

```sh
# apt repository (Ubuntu 24.04+ / Debian 13+)
sudo install -d -m 0755 /etc/apt/keyrings
curl -fsSL https://get.motemd.com/mote.asc | sudo tee /etc/apt/keyrings/mote.asc >/dev/null
echo "deb [signed-by=/etc/apt/keyrings/mote.asc] https://get.motemd.com/apt beta main" | sudo tee /etc/apt/sources.list.d/mote.list
sudo apt update && sudo apt install mote

# AppImage (Ubuntu 22.04+; no installation)
curl -LO https://github.com/motemd/mote/releases/download/v0.9.0-beta.1/mote-0.9.0-beta.1-x86_64.AppImage
chmod +x mote-0.9.0-beta.1-x86_64.AppImage && ./mote-0.9.0-beta.1-x86_64.AppImage

# Tarball into ~/.local (no root) — verifies the checksum and signature
curl -fsSL https://get.motemd.com/install.sh | sh
# remove: ~/.local/opt/mote/install.sh --uninstall
```

The `.deb` uses the system GTK 4.14 / libadwaita 1.5. The AppImage and tarball bundle the same toolkit (built on Ubuntu 22.04, glibc 2.35), so older distributions run the same binary with the same behaviour. Use `beta` above while 0.9.x is the only channel; `stable` appears with 1.0.

## Verify a download

Every release ships `SHA256SUMS` and a detached signature by the release key (ed25519, fingerprint `2E25 9EF2 B369 0ECE 0B3F 56D9 6658 9312 CB84 475F`).

```sh
curl -fsSL https://get.motemd.com/mote.asc | gpg --import
gpg --verify SHA256SUMS.asc SHA256SUMS && sha256sum -c SHA256SUMS
```

## Requirements

Linux x86_64. X11 or Wayland. Korean and other IME input through ibus or fcitx5. macOS and Windows are in development.

## Feedback

- Bugs: [Issues](https://github.com/motemd/mote/issues) — please include the version (`mote --version`), your distribution and session (X11/Wayland), and a small `.md` that shows the problem.
- Questions and ideas: [Discussions](https://github.com/motemd/mote/discussions).
- Security: see [SECURITY.md](SECURITY.md).
- Release feed: [releases.atom](https://github.com/motemd/mote/releases.atom).

## Licence

mote is proprietary software, free of charge during the public beta. Use is governed by the [terms of service](https://motemd.com/terms). Bundled font: Pretendard (SIL Open Font License 1.1).
