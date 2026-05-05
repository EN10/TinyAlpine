# TinyAlpineLinux

TinyAlpineLinux is an experimental minimal Linux distribution based on Alpine Linux. It is built from the Alpine 3.23 minimal root filesystem and is intended for use in tiny containers, minimal chroots, and embedded setups.

This project is a follow-on to https://github.com/EN10/TinyBoxLinux and continues the same lightweight bootable Linux exploration.

## Source

This project starts from the Alpine Linux mini root filesystem:

- `https://dl-cdn.alpinelinux.org/alpine/v3.23/releases/x86_64/alpine-minirootfs-3.23.4-x86_64.tar.gz`

Download information is available from the Alpine Linux website:

- https://www.alpinelinux.org/downloads

## Purpose

- Provide a small, minimal base system
- Keep the filesystem lightweight for container and chroot use
- Serve as a simple starting point for custom Tiny Linux builds

## Usage

1. Download the Alpine mini root filesystem.
2. Extract it into your container or chroot directory.
3. Add the provided `init` file into the root filesystem.
4. Pack the root filesystem into an initramfs image:

   ```sh
   find . | cpio -o -H newc | gzip > ../initramfs.cpio.gz
   ```

5. Customize the minimal system as needed.

## Booting with QEMU

On Windows, you can boot the kernel and initramfs with QEMU:

```bat
.qemu-system-x86_64 -kernel .\bzImage -initrd initramfs.cpio.gz
```

## Notes

- This is an experimental build with the smallest practical footprint.
- It is not a full distribution; it is a minimal base system for further customization.
- Use this project as a starting point for lightweight Linux environments.

## Current files

- `bzImage` — 2.8M
- `initramfs.cpio.gz` — 3.6M
