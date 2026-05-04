#

## 安装 fastfetch

ubuntu 24.04.4

```bash
sudo add-apt-repository ppa:zhangsongcui3371/fastfetch
sudo apt update
sudo apt install fastfetch
```

## 卸载 fastfetch

ubuntu 24.04.4

```bash
sudo apt purge fastfetch
```

```bash
sudo apt autoremove --purge
```

```bash
sudo apt clean
```

## 移除 ppa源

```bash
sudo add-apt-repository --remove ppa:zhangsongcui3371/fastfetch
```

## 🔧 手动强制删除 ppa源 的方法

当 `add-apt-repository --remove` 命令失败时

```bash
sudo rm /etc/apt/sources.list.d/zhangsongcui3371-ubuntu-fastfetch-noble.sources
```

更新软件源缓存

```bash
sudo apt update
```

验证是否删除成功

检查 sources.list.d 目录下是否还有 fastfetch 相关文件

```bash
ls /etc/apt/sources.list.d/ | grep -i fastfetch
```

检查 APT 源列表中是否还有 PPA 条目

```bash
apt-cache policy | grep -i fastfetch
```

如果没有任何输出，说明删除成功。
