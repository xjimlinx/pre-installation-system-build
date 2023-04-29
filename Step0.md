# 步骤〇 编译环境准备

如若需要返回主页，请点击这里：
[预安装系统的构建](./README.md)

> 考虑到装的都是 Ubuntu
> 这里仅写 Arch 和 Ubuntu 的准备

## Ubuntu

```bash
sudo apt install build-essential libncurses-dev bison flex libssl-dev libelf-dev gcc make cmake g++ libc6-dev bin86 qttools5-dev
```

## Arch

```bash
sudo pacman -S base-devel bc libelf flex bison cmake inetutils xmlto
```

此外，为了后面用qemu启动根文件系统，还需要下载qemu

## Ubuntu

```bash
sudo apt install qemu-system-gui qemu-system
```

## Arch

``` bash
sudo pacman -S qemu-emulators-full qemu-full

## 下一步 [步骤一 编译 Linux 内核](./Step1.md)
