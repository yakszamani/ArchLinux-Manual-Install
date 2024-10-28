# Arch Linux Manual Installation Guide

Welcome to the Arch Linux Manual Installation Guide repository! This guide will walk you through a step-by-step manual installation process for Arch Linux, covering topics such as partitioning, encryption, and LVM setup. For detailed instructions, please refer to the attached PDF document, which provides a comprehensive breakdown of the installation process.

[📄 Download the Installation Guide PDF](https://github.com/yakszamani/ArchLinux-Manual-Install/blob/main/Installing%20Arch%20Linux.pdf)

---
## Overview
Arch Linux is a highly customizable and lightweight Linux distribution, but its installation process can be challenging for new users. This repository provides a detailed manual installation guide, designed to simplify the process for anyone who wants to install Arch Linux with encryption, LVM, and other advanced configurations.

### Key Feautures:
Detailed instructions on partitioning and setting up filesystems
LUKS encryption for secure data storage
Logical Volume Management (LVM) setup for flexible partition management
Installing essential packages, including the kernel, GRUB, and NetworkManager
Troubleshooting tips for common issues

## Table of Contents
1. [Prerequisites](https://github.com/yakszamani/ArchLinux-Manual-Install/blob/main/Installing%20Arch%20Linux.pdf)
2. [Arch Linux ISO & Boot Media Setup](#arch-linux-iso--boot-media-setup)
3. [Partitioning & Filesystem Setup](#partitioning--filesystem-setup)
4. [Encryption and LVM Setup](#encryption-and-lvm-setup)
5. [Installing and Configuring Packages](#installing-and-configuring-packages)
6. [Final Steps](#final-steps)
7. [Troubleshooting](#troubleshooting)
8. [Contributing](#contributing)

---

## Prerequisites
Before starting, ensure you have:
- Arch Linux ISO downloaded from [archlinux.org](https://archlinux.org/download/)
- A tool like **Rufus** or **USBImager** for creating bootable media
- Basic understanding of partitioning and file systems

## Arch Linux ISO & Boot Media Setup
1. Download the ISO.
2. Create a bootable USB using **Rufus** or **USBImager**.

[More details in PDF](https://github.com/yakszamani/ArchLinux-Manual-Install/blob/main/Installing%20Arch%20Linux.pdf)

---

## Disk Partitioning and Filesystem Setup

1. **Partition your disk**:
   - EFI partition (1GB)
   - Root partition (remainder)
   - Optional: Swap partition

2. **Format the partitions**:
   - EFI: `mkfs.fat -F32 /dev/sdX1`
   - Root: `mkfs.ext4 /dev/sdX2`
[More details is located in the PDF](#details)

## Encryption and LVM Setup
1. Encrypt the main disk:
    ```bash
    cryptsetup luksFormat /dev/sdX
    cryptsetup open /dev/sdX lvm
    ```

2. Set up LVM:
    ```bash
    pvcreate /dev/mapper/lvm
    vgcreate volgroup0 /dev/mapper/lvm
    ```

3. Create logical volumes for root and home.

[More details is located in the pdf](#details)

---

## Installing and Configuring Packages
Install essential packages:
```bash
pacstrap /mnt base linux linux-firmware
```
---
## Partitioning & Filesystem Setup
1. Set locale, time zone, and other essential configurations.
2. Install GRUB and enable NetworkManager.
3. Reboot to enjoy your fresh Arch Linux installation!
   
---

## **Troubleshooting**
- **Black screen at boot**: Check if GRUB is installed correctly and ensure the EFI partition is mounted.
- **Issues with LVM**: Verify logical volume creation and activation commands.
---

## **Contributing**
We welcome contributions! If you'd like to suggest improvements, report bugs, or contribute code, feel free to open an issue or submit a pull request.

---
## **License**
This repository is licensed under the MIT License. See the LICENSE file for more details.

This README.md provides an overview of the Arch Linux manual installation steps, while the attached PDF guide offers in-depth details for each step. If you have any questions or feedback, feel free to reach out!
