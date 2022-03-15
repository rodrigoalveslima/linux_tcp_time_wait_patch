# TCP TIME-WAIT Patch
This Kernel patch changes the default Linux `TIME-WAIT` duration.

## Applying the Patch
1. Download the Linux source tree `linux-X.Y.Z` in this directory:
```
wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-X.Y.Z.tar.xz
tar -xvf linux-X.Y.Z.tar.xz
```
2. Apply the patch:
```
cd linux-X.Y.Z
patch -p1 < ../patchfile_linux-X.Y.Z
```

## Creating a New Patch
1. Download the Linux source tree `linux-X.Y.Z` in this directory:
```
wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-X.Y.Z.tar.xz
tar -xvf linux-X.Y.Z.tar.xz
```
2. Copy it to `linux-X.Y.Z.original`:
```
cp -R linux-X.Y.Z linux-X.Y.Z.original
```
3. Modify the source code in `linux-X.Y.Z`.
4. Create the new patch file:
```
diff -uNr linux-X.Y.Z.original linux-X.Y.Z > patchfile_linux-X.Y.Z
```
