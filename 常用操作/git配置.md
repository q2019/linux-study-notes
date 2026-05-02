# git 配置

## git 配置非ASCII字符的显示方式

vscode 中提交commit时，自动生成的文件名直接显示，而不是显示转义字符。

```bash
git config --global core.quotepath false
```

1. 打开命令行（Git Bash、CMD 或 PowerShell）

2. 执行完整命令：

   ```bash
   git config --global core.quotepath false
   ```

3. 验证是否设置成功：

   ```bash
   git config --global core.quotepath
   ```

   如果返回 `false`，说明设置成功。

4. 重启 Git GUI（如果已打开，需要完全关闭再重新打开）

5. 再查看文件列表，中文文件名应该就能正常显示了

### 💡 简单记忆

- **查看配置**：`git config --global core.quotepath`
- **设置显示中文**：`git config --global core.quotepath false`
- **恢复转义显示**：`git config --global core.quotepath true`
