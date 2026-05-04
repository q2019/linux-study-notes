#

## 1 在本地执行命令 `ssh-keygen` 生成密钥对

git bash

```bash
ssh-keygen.exe
```

执行后生成 `公钥` 和 `私钥` 两个文件

`公钥` 文件名以 `.pub` 结尾

### 1.1 在本地使用 pscp 将公钥上传至服务器

确认已安装pscp

git bash

```bash
where.exe pscp.exe
```

返回 C:\Program Files\PuTTY\pscp.exe

将公钥文件上传至服务器
基本语法

```bash
pscp 本地文件路径 用户名@服务器IP:远程目标路径
```

先在服务器建立好文件夹 mykey 用于存放公钥

切换至本地公钥文件所在的目录,执行以下命令

```bash
pscp.exe id_ed25519.pub root@192.168.1.1:/root/mykey/
```

### 1.2 配置 `sshd_config` 文件打开证书登录

```bash
sudo vim /etc/ssh/sshd_config
```

修改以下设置

```bash
PubkeyAuthentication yes
AuthorizedKeysFile /root/mykey/id_ed25519.pub
StrictModes no
```

重启服务（会短暂断开现有连接，但会重新启动）

ubuntu 24.04.4

```bash
sudo systemctl restart ssh.service
```

或者使用 reload（更温和，仅重新加载配置，不断开现有连接）

ubuntu 24.04.4

```bash
sudo  systemctl reload ssh.service
```

### 1.3 将本地 `私钥` 转换为 PuTTY 支持的格式

1. 在本地打开 `PuTTYgen` 软件

2. 点击菜单栏 `Conversion` > `Import key`

3. 选择取回的 `私钥` 文件

4. 点击菜单栏 `File` > `Save private key`

### 1.4 在 PuTTY 设置证书登录

1. 在左侧选项栏中选择 `Connection` > `SSH` > `Auth` > `Credentials`

2. 在右侧 `Public-key authentication` > `Private key file for authentication:` > `Browse...`

### 1.5 在 PuTTY 设置登录用户名

1. 在左侧选项栏中选择 `Connection` > `Data`

2. 在右侧 `Login details` > `Auto-login username` 中设置

## 2 在服务器上执行命令 `ssh-keygen` 生成密钥对

```bash
ssh-keygen
```

执行后生成 `公钥` 和 `私钥` 两个文件

`公钥` 文件名以 `.pub` 结尾

### 在本地 gitbash 中执行 `rsync` 命令取回服务器上的 `私钥`

```bash
rsync -r -t -v root@38.47.108.239:/root/test20240905 ~/rsync-test/
```

## 将取回的 `私钥` 转换为 PuTTY 支持的格式

1. 在本地打开 `PuTTYgen` 软件

2. 点击菜单栏 `Conversion` > `Import key`

3. 选择取回的 `私钥` 文件

4. 点击菜单栏 `File` > `Save private key`

## 删除服务器上的 `私钥`

```bash
sudo rm test20240905
```

## 配置 `sshd_config` 文件打开证书登录

```bash
sudo vim /etc/ssh/sshd_config
```

修改以下设置

```bash
PubkeyAuthentication yes
AuthorizedKeysFile /root/test20240905.pub
StrictModes no
```

## 在 PuTTY 设置证书登录

1. 在左侧选项栏中选择 `Connection` > `SSH` > `Auth` > `Credentials`

2. 在右侧 `Public-key authentication` > `Private key file for authentication:` > `Browse...`

## 在 PuTTY 设置登录用户名

1. 在左侧选项栏中选择 `Connection` > `Data`

2. 在右侧 `Login details` > `Auto-login username` 中设置
