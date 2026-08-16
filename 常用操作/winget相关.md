#

## 显示工具的版本

PowerShell 5.1 ✅

```powershell
winget -v
```

```powershell
winget --version
```

## 显示工具的常规信息

PowerShell 5.1 ✅

```powershell
winget --info
```

## 显示选定命令的帮助信息

PowerShell 5.1 ✅

```powershell
winget -?
```

```powershell
winget --help
```

```powershell
winget search -?
```

## search 常用选项

--id                        按 id 筛选结果
-e,--exact                  使用精确匹配查找程序包，大小写敏感

```powershell
winget search --id Microsoft.PowerShell --exact
```

## show 常用选项

查看某个安装包有哪些安装类型

```powershell
winget show --id Microsoft.PowerShell
```
