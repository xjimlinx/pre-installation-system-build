# 步骤一 编译Linux内核

## 首先到官网下载内核源码
[Linux Kernel官网](https://kernel.org/)
![1682759867543](image/Step1/1682759867543.png)
> 本例选择Linux 6.3的内核进行编译

下载好后，双击压缩包进行解压（亦可在命令行中使用tar命令解压）

```bash
tar -xvJf xxx.tar.xz
```

![1682760262706](image/Step1/1682760262706.png)

如图所示，左边的文件夹为解压后的文件夹，右边的为压缩包
以上应该算是废话

打开命令行（linux下的快捷键通常是Ctrl + Alt + T）
记忆方式就是 T 是Terminal的开头

``` bash
cd <LinuxKernelSourceDir>
```

LinuxKernelSourceDir 为你解压的linux源码的文件夹

```bash
export ARCH=x86_64
# 配置架构为x86_64
```

```bash
make x86_64_defconfig
# 设置board config
# 会默认生成适用于x86_64架构相关的选项
```

```bash
make menuconfig
# 在上一步基础上配置要编译的内核的一些选项
```

```bash
make
# 编译
# 亦可为如下所示
make -jx
# x是线程数
```

接下来可以离开电脑休息一会儿或者玩你的其他电子设备或者看书
总之就是先去干别的事情，编译这个东西需要一定时间