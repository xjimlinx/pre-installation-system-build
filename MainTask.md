> 因为现在还没有麒麟源，所以暂时用他爹 Debian 替代一下

如若需要返回主页，请点击：
[预安装系统的构建](./README.md)

---

# 第一题——使用 Debian 源创建根文件系统，达到以下目标

#### 1. 使用 Qemu 能够正常启动根文件系统

##### References(参考) of Q1：

[使用 qemu 模拟调试内核和 debian 根文件系统](https://www.bbsmax.com/A/WpdK7VrodV/)

#### 2. 向根文件系统中集成 ssh、apt 功能

##### References(参考) of Q2：

在创建好根文件系统之后，chroot 至创建好的根文件系统

然后安装上述的两个软件包

#### **关于 chroot 命令**

> &emsp;chroot 是 Unix/Linux 操作系统中的一个命令，用于将当前进程的根目录更改为另一个目录，从而创建一个虚拟的文件系统环境。chroot 命令的主要作用是隔离进程和文件系统，可以将一个进程限制在指定的目录内，使它不能访问其他目录。
> &emsp;chroot 通常被用于构建安全环境、系统修复、软件包的安装和测试等场景。比如，在安装新的 Linux 发行版时，可以在原有的 Linux 系统上使用 chroot 命令来创建一个新的虚拟文件系统环境，然后在这个环境中进行新系统的安装。
> &emsp;使用 chroot 命令时需要注意一些细节，如需要将必要的系统文件和库复制到新的目录中，同时要注意权限和用户身份等问题。在使用 chroot 命令时，需要有 root 用户的权限，否则无法进行操作。

常用命令格式

> NewRootDir 即新的根目录
> Command 即要执行的命令

```bash
chroot [NewRootDir] [Command]
# 这种格式下，chroot命令将当前进程的根目录更改为新的根目录，
# 并在新的根目录中运行指定的命令。

chroot [NewRootDir] /bin/bash
# 这种格式下，chroot命令将当前进程的根目录更改为新的根目录，
# 并在新的根目录中启动一个新的bash终端。

chroot [NewRootDir] /bin/sh -c [要执行的命令]
# 这种格式下，chroot命令将当前进程的根目录更改为新的根目录，
# 并在新的根目录中执行指定的命令。
# 注意到此处的 sh 与上面的 bash 不同，你也可以将此处的sh改
# 为你喜欢的shell,如fish、zsh、csh等。

chroot [NewRootDir] /usr/sbin/chroot [要切换的目录] [要运行的命令]
# 这种格式下，chroot命令将当前进程的根目录更改为新的根目录，
# 并在新的根目录中切换到指定的目录，然后运行指定的命令。

# 需要注意的是，chroot命令只是将进程的根目录更改为新的目录，
# 但是其他系统资源（如网络、用户信息、设备等）仍然是原来的。
# 因此，在使用chroot命令时，需要特别注意对系统资源的处理。
```

---

# 第二题——构建预安装系统，达成以下目标

### 1. 在 initrd 中集成预安装系统

### 2. 预安装系统支持 x86_64/arm64 架构，制作 U 盘启动器后，能够在 UEFI 引导方式下正常引导

### 3. 预安装系统支持进入控制终端，查看硬件信息

### 4. 预安装系统支持磁盘分区，用户/密码，主机名，系统语言等配置修改

### 5. 预安装系统运行结束后，重启设备，确保系统正常启动以及以上配置生效（如：按照上述配置的用户/密码，能够进入系统）

---

# （可选）第三题：预安装系统能够支持提供图形化支持

### 以题目二为基础，工具需要追加下列功能：

## 1. 预安装系统提供 GUI 支持

## 2. 预安装系统提供图形化安装程序，可方便的配置分区、用户/密码，主机名，语言等

> &emsp;这里的图形化界面应该可以理解为桌面环境，应该不至于让用户手写 GUI 界面，那难度就不是中也不是高了

---

# （可选）第四题：预安装系统能够使用 secureboot 功能

### 以题目二为基础，工具需要追加下列功能：

1. 使用自定义证书对内核和 initrd 进行签名，当检测到内核和 initrd 被篡改时，阻止系统启动

---

# 参考文档

[Linux 官网关于 initrd 的手册](https://www.kernel.org/doc/html/latest/admin-guide/initrd.html)

[Debian 官方关于 Debootstrap 的 Wiki](https://wiki.debian.org/Debootstrap)

[Debian 官方说明文档](https://www.debian.org/doc/index.zh-cn.html)

###### Debian GNU/Linux 安装手册

> Bookworm 即最新的 Debian 发行版，版本号 12
> Bullseye 版本号为 11

- [Debian GNU/Linux 安装手册 Bookworm amd64](https://www.debian.org/releases/bookworm/amd64/index.zh-cn.html)
- [Debian GNU/Linux 安装手册 Bookworm arm64](https://www.debian.org/releases/bookworm/arm64/index.zh-cn.html)
- [Debian GNU/Linux 安装手册 Bullseye amd64](https://www.debian.org/releases/bullseye/amd64/index.zh-cn.html)
- [Debian GNU/Linux 安装手册 Bullseye arm64](https://www.debian.org/releases/bullseye/arm64/index.zh-cn.html)

---

# 特征

- 需要了解 linux 根文件系统目录结构以及制作方法
  - [linux 根文件系统的分类,Linux 中文件系统分类方法](https://blog.csdn.net/weixin_42099151/article/details/116870301)
  - [什么是”根文件系统“？一节课讲明白根文件系统的内容与制作](https://www.bilibili.com/video/BV1UD4y1q7pt/?spm_id_from=333.337.search-card.all.click&vd_source=e4cb7ef37d816fd7e84f261ab447a94e)
  - [linux 内核开发第 1 讲：从源码编译 linux-4.9.229 内核和 busybox 文件系统](https://www.bilibili.com/video/BV1Vo4y117Xx/?spm_id_from=333.788&vd_source=e4cb7ef37d816fd7e84f261ab447a94e)
- 需要了解 linux 启动过程
- 需要了解 linux 安装过程
