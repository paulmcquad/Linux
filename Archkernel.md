## Manjaro - Building the Linux Kernel

#### Step 1: Clone the kernel:

`git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git`

---

#### Step 2: Configure the build

Get the `.config` file which is stored in: `proc/config.gz` or `boot/`.

Run:
`zcat /proc/config.gz > .config`

This will import the `.config` into the `linux` directory you cloned.

##### Advanced configuration

If you can't find a `.config`

Run some commands like:`make defconfig` , `make localmodconfig` and `make xconfig` to set/unset some of the settings.

Read the book: `Linux Kernel in a nutshell`

`Chapter 7 - Customizing a kernel`

Also read:

[ArchLinux Compilation](https://wiki.archlinux.org/index.php/Kernel/Traditional_compilation)

[Configuring the kernel](https://www.linux.com/topic/desktop/how-compile-linux-kernel-0/)

---

#### Step 3: Making/Compiling the kernel

At this point you should have the source code and a `.config` file in the same tree.

To get a list of the commands:
`make help`

The process is:

Build the kernel:
`time make -j8`

---

#### Step 4: Install the kernel & modules

Install the kernel modules to (/lib/modules/):

`sudo time make modules_install`

##### Copy the kernel to /boot directory:

- 64-bit (x86_64) kernel:

`cp -v arch/x86_64/boot/bzImage /boot/vmlinuz-linux57`

##### Make initial RAM disk

`mkinitcpio -k linux57 -g /boot/initramfs-linux57.img`

##### Copy System.map

`cp System.map /boot/System.map-linux57`

---

#### Step 5: Clean the directory

Remove the compiled kernel:
`make mrproper`

More info:
`Chapter 4 - Configuring and building`
`Chapter 10 - Kernel Build Command-Line Reference`

---
