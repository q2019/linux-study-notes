#

## ssh配置文件

以下为 客户端 配置文件

```bash
sudo vim /etc/ssh/ssh_config
```

以下为 服务端 配置文件

```bash
sudo vim /etc/ssh/sshd_config
```

## 服务端 sshd_config 常用配置

### 设置 sshd 监听的端口号

```bash
Port 22
```

### 设置是否允许 root 通过 ssh 登录

```bash
PermitRootLogin yes
```

### 设置是否允许只有 RSA 安全验证

```bash
RSAAuthentication yes
```

### 设置是否允许口令验证

```bash
PasswordAuthentication yes
```

## 设置是否允许证书验证

```bash
PubkeyAuthentication yes
```

## 公钥证书位置

```bash
AuthorizedKeysFile /root/test20240905.pub
```

## 严格模式，使用证书登录时建议改为 `no`

```bash
StrictModes no
```

## 设置是否允许 X11 转发

```bash
X11Forwarding yes
```

## 设置是否允许用口令为空的帐号登录

```bash
PermitEmptyPasswords no
```

## 服务端 sshd_config 其他配置

"ListenAddress”设置 sshd 服务器绑定的 IP 地址。

```bash
ListenAddress 192.168.1.1
```

"HostKey”设置包含计算机私人密匙的文件。

```bash
HostKey /etc/ssh/ssh_host_key
```

"ServerKeyBits”定义服务器密匙的位数。

```bash
ServerKeyBits 1024
```

"LoginGraceTime”设置如果用户不能成功登录，在切断连接之前服务器需要等待的时间（以秒为单位）。

```bash
LoginGraceTime 600
```

"KeyRegenerationInterval”设置在多少秒之后自动重新生成服务器的密匙（如果使用密匙）。重新生成密匙是为了防止用盗用的密匙解密被截获的信息。

```bash
KeyRegenerationInterval 3600
```

"IgnoreRhosts”设置验证的时候是否使用“rhosts”和“shosts”文件。

```bash
IgnoreRhosts yes
```

“IgnoreUserKnownHosts”设置 ssh daemon 是否在进行 RhostsRSAAuthentication 安全验证的时候忽略用户的”$HOME/.ssh/known_hosts”

```bash
IgnoreUserKnownHosts yes
```

"PrintMotd”设置 sshd 是否在用户登录的时候显示“/etc/motd”中的信息。

```bash
PrintMotd yes
```

"SyslogFacility”设置在记录来自 sshd 的消息的时候，是否给出“facility code”。

```bash
SyslogFacility AUTH
```

"LogLevel”设置记录 sshd 日志消息的层次。INFO 是一个好的选择。查看 sshd 的 man 帮助页，已获取更多的信息。

```bash
LogLevel INFO
```

"RhostsAuthentication”设置只用 rhosts 或“/etc/hosts.equiv”进行安全验证是否已经足够了。

```bash
RhostsAuthentication no
```

"RhostsRSA”设置是否允许用 rhosts 或“/etc/hosts.equiv”加上 RSA 进行安全验证。

```bash
RhostsRSAAuthentication no
```

"AllowUsers”的后面可以跟任意的数量的用户名的匹配串，这些字符串用空格隔开。主机名可以是域名或 IP 地址。

```bash
AllowUsers admin
```
