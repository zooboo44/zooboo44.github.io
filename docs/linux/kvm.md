---
title: KVM
date: 2025-09-18
---

## Purpose
Unfortunately, sometimes I am forced to use Windows for various programs (CAD, Adobe, Microsoft, etc.) thus I need access to a Windows machine. I could dual boot but my use of Windows will be temporary and short lived (hopefully). I could run windows in a typical VM (VMware or VirtualBox) - but whats the fun in that. The purpose of using KVM is to deepen my understanding of Linux systems, KVM, QEMU, IOMMU, and most importantly, VFIO. My goal is to passthrough components like storage and GPU to the Windows VM to get near native performance. I will use Looking Glass as my "Viewport" into the Windows VM. Looking Glass uses shared memory segment which enables extremely high throughput low latency guest to host communication.

## Configuration and Installation

1. QEMU, KVM, Virt-manager dependencies

    ```
     yay -S qemu virt-manager virt-viewer dnsmasq vde2 bridge-utils openbsd-netcat ebtables iptables libguestfs dmidecode swtpm
    ```

1. Configure GPU passthrough with [quickpassthrough](https://github.com/HikariKnight/quickpassthrough)
    1. Download latest release
    1. Extract
        ```
        tar -xf archive.tar --one-top-level=quickpassthrough
        ```
    1. Run script
        ```
        ./quickpassthrough
        ```
1. Download Windows ISO
1. Create VM
    1. CPU Topology
        - Manually set CPU topology
        - Set sockets, cores, and threads appropriately
    1. Memory
        - Ensure `Enabled shared memory` is unchecked
    1. Remove `Tablet` device
    1. TPM
        - Emulated
        - Model: TIS
        - Version: 2.0
    1. Passthrough ALL devices related to GPU that was passedthrough
1. Install Looking Glass

## Resources
1. [GPU Passthrough](https://github.com/HikariKnight/quickpassthrough)
1. [VFIO Setup docs](https://github.com/HikariKnight/vfio-setup-docs)
1. [Looking Glass Docs](https://looking-glass.io/docs)