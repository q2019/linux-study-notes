# rsync常用命令

- -r 递归传输
- -t 保留时间信息
- -v 输出详细信息
- -n --dry-run 模拟运行
- -h --help 显示帮助信息
- -V --version 显示版本
- --checksum, -c 传输时检查校验和
- --progress 传输时显示进度
- --bwlimit=2048 限制传输速度 单位为KB/s

- -crtv

## 上传到服务器

-crtv

### 上传文件夹

```bash
rsync -r -t ~/Documents/test002/000LINUX/some-tools/u-boot laptop@192.168.100.204:/home/laptop
```

上面的命令将本地~/Documents/test002/000LINUX/some-tools/u-boot `文件夹` 上传到远端/home/laptop

### 上传文件夹中的内容

```bash
rsync -r -t ~/Documents/test002/000LINUX/some-tools/u-boot/ laptop@192.168.100.204:/home/laptop
```

上面的命令将本地~/Documents/test002/000LINUX/some-tools/u-boot `文件夹中的内容` 上传到远端/home/laptop

## 从服务器下载

### 下载文件夹

```bash
rsync -r -t -v laptop@192.168.100.204:/home/laptop/u-boot ~/rsync-test/
```

### 下载文件夹中的内容

```bash
rsync -r -t -v laptop@192.168.100.204:/home/laptop/u-boot/ ~/rsync-test/
```
