# 24.04 卸载自带的 vim-tiny

```bash
sudo apt purge vim-tiny
```

## 24.04 安装 vim

```bash
sudo apt install vim
```

安装此软件包的同时安装了
vim-common
vim-runtime
xxd

## 24.04 vim 程序命令

显示帮助

```bash
vim --help
```

显示版本 配置文件位置

```bash
vim --version
```

常用配置

## vim 三种模式

默认为 命令模式
其他模式按 ESC 退到命令模式

命令模式下
I 在行首插入
i 在光标前插入

A 在行尾插入
a 在光标后插入

O 在光标所在行的上方新建一行
o 在光标所在行的下方新建一行

## 剪切 粘贴 一行

dd 剪切光标所处当前行

按 p 粘贴在光标所在行的下一行
