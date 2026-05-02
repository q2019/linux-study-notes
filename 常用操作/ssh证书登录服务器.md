# 在服务器上执行命令 `ssh-keygen` 生成密钥对

```bash
ssh-keygen
```

执行后生成 `公钥` 和 `私钥` 两个文件

`公钥` 文件名以 `.pub` 结尾

# 在本地 gitbash 中执行 `rsync` 命令取回服务器上的 `私钥`

```bash
rsync -r -t -v root@38.47.108.239:/root/test20240905 ~/rsync-test/
```

# 将取回的 `私钥` 转换为 PuTTY 支持的格式

1. 在本地打开 `PuTTYgen` 软件

2. 点击菜单栏 `Conversion` > `Import key`

3. 选择取回的 `私钥` 文件

4. 点击菜单栏 `File` > `Save private key`

# 删除服务器上的 `私钥`

```bash
sudo rm test20240905
```

# 配置 `sshd_config` 文件打开证书登录

```bash
sudo vim /etc/ssh/sshd_config
```

修改以下设置

```bash
PubkeyAuthentication yes
AuthorizedKeysFile /root/test20240905.pub
StrictModes no
```

# 在 PuTTY 设置证书登录

1. 在左侧选项栏中选择 `Connection` > `SSH` > `Auth` > `Credentials`

2. 在右侧 `Public-key authentication` > `Private key file for authentication:` > `Browse...`

# 在 PuTTY 设置登录用户名

1. 在左侧选项栏中选择 `Connection` > `Data`

2. 在右侧 `Login details` > `Auto-login username` 中设置
