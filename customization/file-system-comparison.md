---
title: File system comparison
description: Comparison the different file systems that we offer
published: true
date: 2022-12-17T13:57:23.647Z
tags: installation, customization, file system, filesystem
editor: markdown
dateCreated: 2021-10-05T10:11:41.501Z
---

# Introduction
Linux offers many different file systems. A file system determines how files are read/accessed on your disk. The default is ext4.

Ext4, in most cases leads to the best results in terms of compatibility and stability but misses modern features like snapshot support and compression.

# Legend

**CoW**: Copy on write, a technique to greatly reduce disk space usage in trade off for performance.

**Journaling**: A file system that keeps track of changes not yet committed to the file system so that in case of a power failure it gets back online faster and is less likely to suffer from data corruption.

**Compression**: Compresses files on your disk to make them take up less space.

**Encryption**: Encrypts your disk securing it with an extra safety measure.

**Snapshots**: Are a way to roll back your system to an earlier state when something goes wrong. It's not a replacement for a proper backup solution.

**Quota**: Set limits on how much disk space users/projects or programs can use.

# Comparison
Find an overview of the different features each file system offers 

| Features | Ext4 | BcacheFS | BTRFS | JFS | XFS | ReiserFS | F2FS | ZFS |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Snapshot | ❌   | ✅   | ✅   | ❌   | ❌   | ❌   | ❌   | ✅   |
| Compression | ❌   | ✅   | ✅   | ✅   | ❌   | ❌   | ✅   | ✅   |
| Journaling | ✅   | ✅   | ❌   | ✅   | ✅   | ❌   | ❌   | ❌   |
| Encryption | ✅   | ✅   | ✅   | ✅   | ✅   | ✅   | ✅   | ✅   |

## Ext4
**Ext4** is the default Linux file system. It has high compatibility & stability due to being the most used options. (If you use Dropbox, Ext4 is the only file system on Linux officially supported)

**Special features**
-   Unlimited subdirectories
-   Backwards combability with ext3
-   Metadata checksumming
-   Encryption
-   Quotas

## BTRFS
**Btrfs** is a CoW filesystem for Linux aimed at implementing advanced features while also focusing on fault tolerance, repair and easy administration.

**Special features**
-   Raid support
-   Compression
-   CoW

## BcacheFS
**Bcachefs** is a next-generation CoW filesystem that aims to provide features from Btrfs and ZFS with a cleaner codebase, more stability, greater speed and a GPL-compatible license.

**Special features**
-   Copy on write (CoW) - like ZFS or BTRFS
-   Full data and metadata check summing
-   Multiple devices, including replication and other types of RAID
-   Caching
-   Compression
-   Encryption
-   Snapshots

## JFS
**JFS** is a stable, feature-rich file system that has not been publicized as much as some of the other Linux file systems. With optimizations, JFS is stable, CPU efficient and fast. In particular, VMWare sessions stand to benefit enormously from a properly optimized and defragmented, underlying JFS file system.

**Special features**
-   Performance tuned for Linux.
-   Original design goals: Performance, Robustness, SMP.

## XFS
**XFS** is a high-performance journaling file system created by *Silicon Graphics, Inc.* It is particularly proficient at parallel IO due to its allocation group based design. This enables extreme scalability of IO threads, filesystem bandwidth, file and filesystem size when spanning multiple storage devices.

**Special features**
-   Capacity
-   Journaling
-   Allocation groups
-   Striped allocation
-   Extent-based allocation
-   Variable block sizes
-   Delayed allocation
-   Sparse files

## ZFS
**ZFS** is an open-source storage platform. It includes the functionality of both traditional file systems and volume managers. 

**Special features**
-   Protection against data corruption. Integrity checking for both data and metadata.
-   Continuous integrity verification and automatic “self-healing” repair
-   Data redundancy with mirroring, RAID-Z1/2/3 and DRAID
-   Space-saving with transparent compression using LZ4, GZIP or ZSTD
-   Hardware-accelerated native encryption
-   Efficient storage with snapshots and copy-on-write clones
-   Efficient local or remote replication — send only changed blocks with ZFS send and receive

## F2FS
**F2FS** (Flash-Friendly File System) is a flash file system initially developed by Samsung Electronics for the Linux kernel.

**Special features**
-   Roll-back and roll-forward recovery
-   Transparent file compression using LZO or LZ4 (with Linux 5.6), or zstd (with Linux 5.7)
-   Offline resizing (shrinking not supported.)
-   Filesystem-level encryption

## ReiserFS

**ReiserFS** is a general-purpose, journaling file system without quota support.

**Special features**
-   Tail packing