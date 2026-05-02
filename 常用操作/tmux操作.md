# 新建会话

```bash
tmux new -s <session-name>
```

# 分离会话

在 tmux 会话中输入

```bash
tmux detach
```

如果有程序运行不能输入则使用快捷键

1. `Ctrl` + `b`

2. `d`

# 列出所有会话

```bash
tmux ls
```

# 进入已有会话

```bash
tmux attach -t <session-name>
```

# 删除会话

```bash
tmux kill-session -t <session-name>
```
