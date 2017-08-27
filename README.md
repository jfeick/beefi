# beefi
beefi - create BootablE EFIstub kernel images

## Synopsis
```
beefi [ -u ] [ -c CMDLINE ] [ -k KERNEL ] [ -i INITRD ] [ -h ] [ --version ]
```

## Description
beefi is a script used to create a bootable EFISTUB kernel image with
integrated kernel commandline and initramfs image. It uses objcopy to
combine those components to one image which can be directly booted on
UEFI systems.

## Options
The following is a list of options accepted by beefi

```
-c | --cmdline
```
Sets the kernel command line

```
-k | --kernel KERNEL
```
The location of the kernel image (e.g. */boot/vmlinuz-linux*)

```
-i | --initrd INITRD
```
The location of the initrd image (e.g. */boot/initramfs-linux.img*)

```
-o | --output \fOUT
```
The location of the output file (e.g. */boot/efi/EFI/boot/bootx64.efi*)

```
-u | --use-config
```
Use the configuration file */etc/beefi/beefi.conf*

```
-h | --help
```
Just print help string and exit

```
--version
```
Just print version string and exit

## Examples

Create a bootable image using the current kernel commandline.
Run:
```
beefi --current-cmdline -k /boot/vmlinuz-linux -i /boot/initramfs-linux.img -o output.efi
```

Create a bootable image using a custom kernel commandline.
Run:
```
beefi -c "root=UUID=aabbccdd-eeff-0011-223344556677 rw quiet" -k /boot/vmlinuz-linux -i /boot/initramfs-linux.img -o output.efi
```

Create a bootable image using the config file /etc/beefi/beefi.conf
Run:
```
beefi -u
```