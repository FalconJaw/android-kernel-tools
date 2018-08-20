# Toolchains (GCC & Clang 9 and 11) with libraries for compiling Android kernel.
  [**Not noob friendly.**]

Getting Started
==================================================

### How to use these toolchains for compiling android Kernels ?
--------
1. Clone this toolchain repo in tools folder
```bash
$ git clone https://github.com/mranonymz/android-kernel-tools.git tools
```
2. Set path according to your choice.

```bash
	PATH="tools/build-tools/linux-x86/bin:$PATH"
	PATH="tools/build-tools/path/linux-x86:$PATH"
	PATH="tools/gcc/linux-x86/aarch64/aarch64-linux-android-4.9/bin:$PATH"
	PATH="tools/gcc/linux-x86/arm/arm-linux-androideabi-4.9/bin:$PATH"
	PATH="tools/clang/host/linux-x86/**clang-r353983d**/bin:$PATH"
	PATH="tools/misc/linux-x86/lz4:$PATH"
	PATH="tools/misc/linux-x86/dtc:$PATH"
	PATH="tools/misc/linux-x86/libufdt:$PATH"
	export LD_LIBRARY_PATH="tools/clang/host/linux-x86/**clang-r353983d**/lib64:$LD_LIBRARY_PATH"
```
>> Here clang-r353983d for AOSP clang 9.0.4
>> and clang-r399163b for AOSP clang 11.0.5.
3. Use these command for compiling with **clang**.
```bash
$ make \
  O=out \
  ARCH=arm64 \
  SUBARCH=ARM64 \
  CC=clang \
  HOSTCC=clang \
  HOSTCXX=clang++ \
  CLANG_TRIPLE=aarch64-linux-gnu- \
  CROSS_COMPILE=aarch64-linux-android- \
  CROSS_COMPILE_ARM32=arm-linux-androideabi- \
  ${DEVICE}_defconfig
```
4. Use this command for compiling only with **gcc**.
```bash
$ make \
  O=out \
  ARCH=arm64 \
  SUBARCH=ARM64 \
  CLANG_TRIPLE=aarch64-linux-gnu- \
  CROSS_COMPILE=aarch64-linux-android- \
  CROSS_COMPILE_ARM32=arm-linux-androideabi- \
  ${DEVICE}_defconfig
```

>> Here ${DEVICE}_defconfig is the kernel config file used to compile kernel.

### It will be easy to compile kernel with a bash script. Make a bash script in kernel folder and set toolchain path according to your folders.
### You can use one like [**This**](https://github.com/pkm774/kernel_asus_sdm660/blob/ten/build.sh).

### All source credit goes to : [**Android Open Source Project**](https://source.android.com)
### Give a star if u liked my work :)
