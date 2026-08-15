# git 配置

## git 配置非ASCII字符的显示方式

vscode 中提交commit时，自动生成的文件名直接显示，而不是显示转义字符。

PowerShell

```PowerShell
git config --global core.quotepath false
```

CMD

```CMD
git config --global core.quotepath false
```

Git Bash

```bash
git config --global core.quotepath false
```

## 验证是否设置成功

如果返回 `false`，说明设置成功。

PowerShell

```PowerShell
git config --global core.quotepath
```

CMD

```CMD
git config --global core.quotepath
```

Git Bash

```bash
git config --global core.quotepath
```

## GIT 查看当前项目 用户名 邮箱 地址

### 查看当前项目配置的 用户名

Git Bash ✅

PowerShell ✅

```bash
git config --local user.name
```

### 查看当前项目配置的 邮箱

Git Bash ✅

PowerShell ✅

```bash
git config --local user.email
```

### 查看当前项目配置的 远程仓库地址

Git Bash ✅

PowerShell ✅

查看所有远程仓库的地址（最常用）

简写

```bash
git remote -v
```

全写

```bash
git remote --verbose
```

只查看 origin 的地址

```bash
git remote get-url origin
```

查看 origin 的详细信息（包括地址、跟踪分支等）

```bash
git remote show origin
```

## 配置当前仓库的用户名和邮箱

### 设置用户名

Git Bash ✅

PowerShell ✅

```bash
git config --local user.name "你的名字"
```

### 设置邮箱

Git Bash ✅

PowerShell ✅

```bash
git config --local user.email "你的邮箱@example.com"
```

### 修改远程仓库地址

Git Bash ✅

PowerShell ✅

```bash
git remote set-url origin git@github.com:username/repo.git
```

## 生成新的 SSH 密钥对

### 交互式生成

Git Bash ✅

PowerShell ✅

```bash
ssh-keygen.exe
```

根据提示输入完整路径，括号内为默认，这里需要手动输入完整路径和文件名

Git Bash ✅

```bash
$ ssh-keygen.exe
Generating public/private ed25519 key pair.
Enter file in which to save the key (/c/Users/test/.ssh/id_ed25519): /c/Users/test/.ssh/test
```

PowerShell ✅

```powershell
PS C:\Users\test\Desktop> ssh-keygen.exe
Generating public/private ed25519 key pair.
Enter file in which to save the key (C:\Users\test/.ssh/id_ed25519): C:\Users\test/.ssh/test
```

生成两个文件
test 为私钥
test.pub 为公钥

### 修改 .ssh/config 文件

Git Bash ✅

大小写不敏感

IdentitiesOnly yes 表示只使用指定密钥文件，不会尝试其他密钥文件

```bash
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/test
    IdentitiesOnly yes

Host bitbucket.org
    HostName bitbucket.org
    User git
    IdentityFile ~/.ssh/test
    IdentitiesOnly yes
```

### 测试连接

Git Bash ✅

```bash
ssh -T git@bitbucket.org
```
