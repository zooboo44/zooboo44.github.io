---
title: KVM
date: 2025-09-18
---

## Purpose
Unfortunately, sometimes I am forced to use Windows for various programs (CAD, Adobe, Microsoft, etc.) thus I need access to a Windows PC. I could dual boot but my use of Windows will be temporary and short lived (hopefully). I could run windows in a typical VM (VMware or VirtualBox) - but whats the fun in that. The purpose of using KVM is to deepen my understanding of Linux systems, KVM, QEMU, IOMMU, and most importantly, VFIO. My goal is to passthrough components like storage and GPU to the Windows VM to get near native performance. I will use Looking Glass as my "Viewport" into the Windows VM. Looking Glass uses shared memory segment which enables extremely high throughput low latency guest to host communication.

## Configuration
## Resources