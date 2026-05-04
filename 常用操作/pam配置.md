# pam 配置文件位置

```bash
cd /etc/pam.d
```

## 查看配置文件

```bash
cat /etc/pam.d/sshd
```

## 配置 ssh 登录后显示的信息

```bash
sudo vim /etc/pam.d/sshd
```

不显示信息，则注释掉此行

```bash
session    optional     pam_motd.so  motd=/run/motd.dynamic
```
