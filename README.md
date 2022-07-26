# TCP TIME-WAIT Patch
This Linux Kernel patch changes the default `TIME-WAIT` duration (60 seconds for
Linux 5.4).

## Applying the Patch
1. Download the Linux source tree `linux-X.Y[.Z]` in this directory:
```
$ wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-X.Y[.Z].tar.xz
$ tar -xvf linux-X.Y[.Z].tar.xz
```
2. Apply the patch:
```
$ cd linux-X.Y[.Z]
$ patch -p1 < ../patchfile_linux-X.Y[.Z]
```

## Creating a New Patch
1. Download the Linux source tree `linux-X.Y[.Z]` in this directory:
```
$ wget https://cdn.kernel.org/pub/linux/kernel/vX.x/linux-X.Y[.Z].tar.xz
$ tar -xvf linux-X.Y[.Z].tar.xz
```
2. Copy it to `linux-X.Y[.Z].original`:
```
$ cp -R linux-X.Y[.Z] linux-X.Y[.Z].original
```
3. Modify the source code in `linux-X.Y[.Z]`.
4. Create the new patch file:
```
$ diff -uNr linux-X.Y[.Z].original linux-X.Y[.Z] > patchfile_linux-X.Y[.Z]
```

## Compiling the Kernel (on a Debian-based Distribution)
1. Download the Linux source tree `linux-X.Y[.Z]` and apply a patch.
2. Install the compilers and tools needed to build the Kernel:
```
$ sudo apt-get install build-essential libncurses-dev bison flex libssl-dev libelf-dev
```
3. Copy and edit the existing Linux configuration (or use `make menuconfig`):
```
$ cp -v /boot/config-$(uname -r) linux-X.Y[.Z]/.config
```
If copying from Ubuntu, read
[this](https://askubuntu.com/questions/1329538/compiling-the-kernel-5-11-11).

4. Build the Kernel:
```
$ cd linux-X.Y[.Z]
$ make oldconfig
$ make -j $(nproc)
```
5. Install the Kernel modules:
```
$ sudo make modules_install
```
6. Install the Kernel:
```
$ sudo make install
```
7. Clean build object files:
```
$ make clean
```
8. Edit and update the Grub configuration:
```
$ sudo vi /etc/default/grub
$ sudo update-grub
```
9. Reboot the system:
```
$ sudo reboot
```
10. Check the new Kernel version:
```
$ uname -mrs
```
