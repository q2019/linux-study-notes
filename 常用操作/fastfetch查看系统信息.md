#

## 安装 fastfetch

### ubuntu 24.04.4

```bash
sudo add-apt-repository ppa:zhangsongcui3371/fastfetch
sudo apt update
sudo apt install fastfetch
```

## 卸载 fastfetch

```bash
# 1. 删除主程序及其配置
sudo apt purge fastfetch

# 2. 清理不再需要的依赖包，并同时删除它们的配置
sudo apt autoremove --purge

# 3. （可选）清理下载的安装包缓存，释放硬盘空间
sudo apt clean   # 删除所有已下载的.deb安装包[citation:3][citation:6]
```
