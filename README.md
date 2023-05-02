# Kernel Action

Action for Non-GKI Kernel, with certain universality, requires understanding of kernel and Android related knowledge to apply.

## Warning:warning: :warning: :warning:

If you are not a kernel author, use other people's labor to build KernelSU for personal use only. Do not share it with others. This is respect for the original author's labor results.

## Supported kernels

- `4.19`
- `4.14`

## Usage

> After successful compilation, AnyKernel3 will be uploaded in `Action`, and device check has been turned off. Please flash it in TWRP.

Fork this repository to your storage, then edit config.env according to the following content. After that, click `Star` or `Action`. You can see the option `Build Kernel` on the left side. Clicking on it will show `Run workflows` on the top of the large dialog box on the right side. Clicking on it will start the build.

### Kernel Source

Fill in your kernel repository address.

For example: https://github.com/iminamoto/kernel_oneplus_sm8250/tree/oos

### Kernel Source Branch

Fill in your kernel branch.

For example: oos

### Kernel defconfig

Fill in the name of your kernel configuration file.

For example: vendor/kona_defconfig

### Target arch

For example: arm64

### Kernel file

Fill in the image that needs to be flashed, which is generally consistent with BOARD_KERNEL_IMAGE_NAME in your AOSP-device tree.

For example: Image.gz

### Clang

#### Use custom clang

Change it to true. You can use non-Google official clang, such as [proton-clang](https://github.com/kdrag0n/proton-clang).

#### Custom Clang

Supports direct links to GitHub repositories or zip archives.

#### Custom Clang Commands

If you are using custom clang, you should change the compiler location yourself.

#### Clang Branch

The main branches are:
| Clang Branch |
| ------------ |
| master |
| master-kernel-build-2021 |
| master-kernel-build-2022 |

Or other branches, please look for them in https://android.googlesource.com/platform/prebuilts/clang/host/linux-x86 according to your needs.

#### Clang version

Fill in the Clang version you need to use.
| Clang Version | Corresponding Android Version | AOSP-Clang Version |
| ---------- | ----------------- | --------------- |
| 12.0.5 | Android S | r416183b |
| 14.0.6 | Android T | r450784d |
| 14.0.7 | | r450784e |
| 15.0.1 | | r458507 |

Generally, Clang12 can compile most kernels above 4.14.

### Extra build commands

Some kernels need to manually add some compilation commands to compile normally. If not needed, leave it blank.
Please separate the commands with spaces.

For example: LLVM=1 LLVM_IAS=1

### Disable LTO

Used to optimize the kernel, but sometimes it may cause errors, so it is provided to disable it. Set it to true to disable it.

### Use KernelSU

Whether to use KernelSU, used to troubleshoot kernel faults or compile kernels separately.

#### KernelSU Branch or Tag

Select the branch or tag of KernelSU:
- Main branch (development version): `KERNELSU_TAG=main`
- Latest TAG (stable version): `KERNELSU_TAG=`
- Specify TAG (such as `v0.5.2`): `KERNELSU_TAG=v0.5.2`

### Use Kprobes

If your kernel Kprobes work normally, change this to true to automatically inject parameters into defconfig.

### Use overlayfs

If the kernel does not have this parameter, please enable it. The module needs it.

### Need DTBO

If your kernel also needs to flash DTBO, please set it to true.

### Make boot image
> Merged from previous Workflows, you can view historical submissions

Setting it to true will compile boot.img. You need to provide `Source boot image`.

### Source boot image

As the name suggests, provide a boot image that can boot the source system normally. It needs a direct link, preferably built from the same kernel source code and device tree as your current system from AOSP. The ramdisk contains partition tables and init. If not, the built image will not be able to boot normally.

For example: https://github.com/iminamoto/Kernel_Action/raw/master/boot/boot.img

## Thanks

- [AnyKernel3](https://github.com/osm0sis/AnyKernel3)
- [AOSP](https://android.googlesource.com)
- [KernelSU](https://github.com/tiann/KernelSU)
- [xiaoxindada](https://github.com/xiaoxindada)
