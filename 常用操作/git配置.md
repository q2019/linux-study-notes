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
