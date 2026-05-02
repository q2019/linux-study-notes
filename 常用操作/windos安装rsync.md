#

## 下载rsync

<https://www2.futureware.at/~nickoe/msys2-mirror/msys/x86_64/>

rsync-3.2.3-2-x86_64.pkg.tar.zst

以下安装包为可选

libzstd-1.4.9-1-x86_64.pkg.tar.zst
libxxhash-0.8.0-1-x86_64.pkg.tar.zst
liblz4-1.9.3-1-x86_64.pkg.tar.zst

配置
rsync 文件夹里的 bin 和 lib 的内容分别复制到 Git/usr/bin 和 Git/usr/lib 下

直接将下载好的package用7zip解压，将usr文件夹复制到 C:\Program Files\Git 中与 C:\Program Files\Git\usr文件夹合并

打开 Git Bash ，运行 rsync -v ，如果报 msys-zstd-1.dll not found ，则将 libzstd 文件夹里的 bin 的内容复制到 Git/usr/bin 下
重新运行，如果报 msys-xxhash-0.dll not found ，则将 libxxhash 文件夹里的 bin 的内容复制到 Git/usr/bin 下，并将其重命名为 msys-xxhash-0.dll
重新运行，如果报 msys-lz4-1.dll not found ，则将 liblz4 文件夹里的 bin 的内容复制到 Git/usr/bin 下
重新运行，如果报 msys-crypto-1.1.dll not found ，则将 Git/usr/bin 文件夹里的 msys-crypto-1.0.0.dll 复制到当前目录，并重命名为 msys-crypto-1.1.dll

## 上传时出现以下错误

```bash
$ rsync -r -t -n ~/Desktop/LINUX-ISO test@192.168.31.161:/home/test/btdownloads
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ED25519 key sent by the remote host is
SHA256:eiDJqxmXion7ttqXl9pozBoWqBLkLCdOL4URWKvh9d4.
Please contact your system administrator.
Add correct host key in /c/Users/test/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /c/Users/test/.ssh/known_hosts:3
Host key for 192.168.31.161 has changed and you have requested strict checking.
Host key verification failed.
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(231) [sender=3.3.0]

```

在git bash终端中输入 ssh-keygen.exe -R <远程服务器地址> 清除已缓存的公钥

```bash
test@DESKTOP-EF0TFA7 MINGW64 ~/Desktop
$ ssh-keygen.exe -R 192.168.31.161
# Host 192.168.31.161 found: line 1
# Host 192.168.31.161 found: line 2
# Host 192.168.31.161 found: line 3
/c/Users/test/.ssh/known_hosts updated.
Original contents retained as /c/Users/test/.ssh/known_hosts.old
```
