# Soplos Kernels

[![License: GPL-3.0+](https://img.shields.io/badge/License-GPL--3.0%2B-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

Pre-compiled Linux kernels for Soplos Linux, optimized for different use cases.

## Available Kernels

| Package | Description | Patches |
| :--- | :--- | :--- |
| `linux-soplos` | Standard Soplos Linux kernel | — |
| `linux-soplos-bore` | Optimized for gaming and low latency | BORE |
| `linux-soplos-bore-ntsync` | Optimized for gaming and low latency with Wine/Proton support | BORE, NTSYNC |
| `linux-soplos-zen` | Optimized for desktop and gaming | Zen |
| `linux-soplos-ntsync` | Improved Wine/Proton compatibility | NTSYNC |
| `linux-soplos-rt` | Full real-time preemption for audio/video production | PREEMPT_RT |
| `linux-soplos-x3d` | Optimized for AMD CPUs with 3D V-Cache (5800X3D, 7800X3D…) | BORE, NTSYNC |

## Hardware Levels

Each kernel variant is available in four hardware levels optimized for different CPU generations:

| Suffix | Architecture | Description |
| :--- | :--- | :--- |
| `-v1` | x86-64 | All x86-64 CPUs — maximum compatibility |
| `-v2` | x86-64-v2 | SSE4.2+ — most CPUs since ~2009 |
| `-v3` | x86-64-v3 | AVX2+ — modern hardware since ~2013 (Haswell / Zen+) |
| `-v4` | x86-64-v4 | AVX-512 — latest generation CPUs |

The `linux-soplos-x3d` variant is only available from v3 onwards, as AMD X3D CPUs are Zen 3 or newer.

If in doubt, use `-v1` for maximum compatibility or install via [Soplos Kernel Installer](https://github.com/SoplosLinux/soplos-kernel-installer), which detects the optimal level automatically.

## Installation

Add the Soplos kernels repository:

```bash
sudo mkdir -p /usr/share/keyrings
curl -fsSL https://raw.githubusercontent.com/SoplosLinux/soplos-kernels/main/public.key | sudo gpg --dearmor -o /usr/share/keyrings/soplos-kernels.gpg

sudo tee /etc/apt/sources.list.d/soplos-kernels.sources > /dev/null << 'EOF'
Types: deb
URIs: https://raw.githubusercontent.com/SoplosLinux/soplos-kernels/main/
Suites: stable
Components: main
Signed-By: /usr/share/keyrings/soplos-kernels.gpg
EOF

sudo apt update
```

Install a kernel:

```bash
# Standard kernel (replace -v3 with your hardware level)
sudo apt install linux-soplos-v3

# BORE kernel
sudo apt install linux-soplos-bore-v3

# BORE + NTSYNC kernel
sudo apt install linux-soplos-bore-ntsync-v3

# Zen kernel
sudo apt install linux-soplos-zen-v3

# NTSYNC kernel
sudo apt install linux-soplos-ntsync-v3

# Real-time kernel (PREEMPT_RT)
sudo apt install linux-soplos-rt-v3

# AMD X3D V-Cache kernel (v3 or v4 only)
sudo apt install linux-soplos-x3d-v3
```

## Updates

Kernels are distributed as metapackages. When a new version is released, a simple `sudo apt upgrade` will update the kernel automatically.

## Compatibility

Compatible with all Soplos Linux distributions:
- Soplos Tyron
- Soplos Tyson
- Soplos Boro

## Build Tool

These kernels are compiled using [Soplos Kernel Installer](https://github.com/SoplosLinux/soplos-kernel-installer), the official graphical kernel manager for Soplos Linux.

## Developer

Developed by Sergi Perich
Website: https://soplos.org
Contact: info@soploslinux.com

## License

Licensed under [GPL-3.0+](https://www.gnu.org/licenses/gpl-3.0.html).
