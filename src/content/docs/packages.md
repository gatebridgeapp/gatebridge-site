---
title: "Install from packages"
description: "Install fido-daemon from the Gatebridge apt or dnf repositories on Debian, Ubuntu, Fedora, Rocky, or AlmaLinux."
order: 2
---

Packaged installs of the Gatebridge server program (`fido-daemon`). After install, continue with pairing in the [quickstart](/docs/quickstart/).

## One-line installer

Detects the distro, adds the repository, and installs the package:

```bash
curl -fsSL https://packages.gatebridge.app/install.sh | sudo sh
```

On Ubuntu 22.04 it offers to install `python3.11` first if needed.

## Debian / Ubuntu (manual)

Suites: `bookworm` (Debian 12), `trixie` (Debian 13), `noble` (Ubuntu 24.04), `jammy` (Ubuntu 22.04).

```bash
sudo install -d -m 0755 /etc/apt/keyrings
sudo curl -fsSL https://packages.gatebridge.app/fido-daemon.gpg \
  -o /etc/apt/keyrings/fido-daemon.gpg
echo "deb [signed-by=/etc/apt/keyrings/fido-daemon.gpg] https://packages.gatebridge.app/debian/trixie/ ./" \
  | sudo tee /etc/apt/sources.list.d/fido-daemon.list
sudo apt update
sudo apt install fido-daemon
```

Replace `trixie` in the sources line with `bookworm`, `noble`, or `jammy` as appropriate.

## RHEL / Fedora / Rocky / Alma (manual)

```bash
sudo rpm --import https://packages.gatebridge.app/RPM-GPG-KEY
sudo tee /etc/yum.repos.d/fido-daemon.repo >/dev/null <<'EOF'
[fido-daemon]
name=fido-daemon
baseurl=https://packages.gatebridge.app/repo/fedora/x86_64/
enabled=1
gpgcheck=1
gpgkey=https://packages.gatebridge.app/RPM-GPG-KEY
EOF
sudo dnf install fido-daemon
```

On Rocky or AlmaLinux, change `baseurl` to `https://packages.gatebridge.app/repo/rockylinux/x86_64/`.

## After install

```bash
fido-daemon --version
```

Then pair with your phone in the [quickstart](/docs/quickstart/). Configuration, systemd, and troubleshooting: [install from source](/docs/installation/).
