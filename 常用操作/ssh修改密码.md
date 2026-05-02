# 查看用户密码状态

```bash
passwd --status
```

passwd `-S` 或 `--status` 命令可以查看某一个用户密码的状态

```bash
passw -S mino
mino P 04/21/2015 0 90 15 -1
```

第一列：返回值 mino 为用户名

第二列：locked password (L)密码被锁住, has no password (NP)没有密码, has a usable password (P)有一个可用密码

第三列：该用户密码的最后修改时间

第四列：最小时间，密码最小的生存期（天）

第五列：最大时间，密码最大的生存期（天）

第六列：警告时间，在密码失效前多少天用户开始收到警告提示

第七列：失效时间，密码的失效时间（-1 表示没有失效时间）
