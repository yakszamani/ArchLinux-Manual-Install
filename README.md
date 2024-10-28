# Arch Linux Manual Installation Guide

This repository contains a comprehensive step-by-step guide to manually installing Arch Linux. It covers partitioning, encryption, Logical Volume Management (LVM), and essential configurations.

## Table of Contents
1. [Prerequisites](#prerequisites)
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

[More details](#details)

---

## Partitioning & Filesystem Setup
Using `cfdisk`, create three partitions:
1. EFI partition (1GB)
2. Root partition (remainder)
3. Swap partition (optional)

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

[More details](#details)

---

## Installing and Configuring Packages
Install essential packages:
```bash
pacstrap /mnt base linux linux-firmware
