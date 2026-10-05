---
title: "Install from packages"
description: "Install fido-daemon from the Gatebridge apt or dnf repositories on Debian, Ubuntu, Fedora, Rocky, or AlmaLinux."
order: 2
---

Packaged installs of the Gatebridge server program (`fido-daemon`). After install, continue with pairing in the [quickstart](/docs/quickstart/).

A shell script that downloads and runs the same install is planned. Until it ships, use the repository steps below.

## Debian / Ubuntu

Suites: `bookworm` (Debian 12), `trixie` (Debian 13), `noble` (Ubuntu 24.04).

```bash
sudo install -d -m 0755 /etc/apt/keyrings
sudo curl -fsSL https://andreparames.github.io/fido2-android-bridge/fido-daemon.gpg \
  -o /etc/apt/keyrings/fido-daemon.gpg
echo "deb [signed-by=/etc/apt/keyrings/fido-daemon.gpg] https://andreparames.github.io/fido2-android-bridge/debian/trixie/ ./" \
  | sudo tee /etc/apt/sources.list.d/fido-daemon.list
sudo apt update
sudo apt install fido-daemon
```

Replace `trixie` in the sources line with `bookworm` or `noble` as appropriate.

## RHEL / Fedora / Rocky / Alma

```bash
sudo rpm --import https://andreparames.github.io/fido2-android-bridge/RPM-GPG-KEY
sudo tee /etc/yum.repos.d/fido-daemon.repo >/dev/null <<'EOF'
[fido-daemon]
name=fido-daemon
baseurl=https://andreparames.github.io/fido2-android-bridge/repo/fedora/x86_64/
enabled=1
gpgcheck=1
gpgkey=https://andreparames.github.io/fido2-android-bridge/RPM-GPG-KEY
EOF
sudo dnf install fido-daemon
```

On Rocky or AlmaLinux, change `baseurl` to `https://andreparames.github.io/fido2-android-bridge/repo/rockylinux/x86_64/`.

## After install

```bash
fido-daemon --version
```

Then pair with your phone in the [quickstart](/docs/quickstart/). Configuration, systemd, and troubleshooting: [install from source](/docs/installation/).
