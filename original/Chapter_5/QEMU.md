# Getting Started with QEMU
## Compiling Required Binaries
If you want to follow along with the videos, you can certainly do so. However, it should be noted that creating an emulation environment is no small task. We’d highly recommend you simply follow along for now unless you have experience with compiling the Linux kernel.

Instructions for compiling required binaries can be found in the [*"RISC-V - Getting Started Guide"*](https://risc-v-getting-started-guide.readthedocs.io/en/latest/linux-qemu.html).

## Creating a Custom RISC-V System
If you are already comfortable with compiling the Linux kernel, QEMU, and software suites like BusyBox, you may want to take things a step further. There is a build system for creating Linux based root file systems and emulating them called the Yocto Project. RISC-V has a “layer” which can be used to create a completely custom Linux distribution. For more details see [meta-riscv](https://github.com/riscv/meta-riscv) on GitHub.