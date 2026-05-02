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

## Installation

Add the Soplos kernels repository:

```bash
curl -fsSL https://raw.githubusercontent.com/SoplosLinux/soplos-kernels/main/soplos-kernels.gpg | sudo tee /usr/share/keyrings/soplos-kernels.gpg > /dev/null

echo "deb [signed-by=/usr/share/keyrings/soplos-kernels.gpg] https://raw.githubusercontent.com/SoplosLinux/soplos-kernels/main stable main" | sudo tee /etc/apt/sources.list.d/soplos-kernels.list

sudo apt update
```

Install a kernel:

```bash
# Standard kernel
sudo apt install linux-soplos

# BORE kernel
sudo apt install linux-soplos-bore

# BORE + NTSYNC kernel
sudo apt install linux-soplos-bore-ntsync

# Zen kernel
sudo apt install linux-soplos-zen

# NTSYNC kernel
sudo apt install linux-soplos-ntsync

# Real-time kernel (PREEMPT_RT)
sudo apt install linux-soplos-rt
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
