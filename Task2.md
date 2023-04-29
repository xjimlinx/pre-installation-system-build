# 任务二 配置代理环境

如若需要返回主页，请点击这里：
[预安装系统的构建](./README.md)

## 1. 配置代理环境

### 1.1 下载 Qv2ray.Appimage

#### 1.1.1 Ubuntu 下使用 Appimage 可能会报错

根据 Appimage 官网的 Wiki：
https://github.com/AppImage/AppImageKit/wiki/FUSE

![1682702649615](image/Task1/1682702649615.png)
注意 22.04 及以上不要安装 fuse,要不然可能得重装 Ubuntu

```bash
sudo apt install libfuse2
```
