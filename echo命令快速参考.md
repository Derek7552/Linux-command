# echo命令快速参考

## 📋 基本语法
```bash
echo [选项] [字符串]
```

## 🎯 常用选项

| 选项 | 含义 | 示例 | 输出 |
|------|------|------|------|
| `-n` | 不换行输出 | `echo -n "Hello"` | Hello（无换行） |
| `-e` | 启用转义字符 | `echo -e "A\nB"` | A<br>B |
| `-E` | 禁用转义字符（默认） | `echo -E "A\nB"` | A\nB |

## 🔤 转义字符（需配合 -e 使用）

| 转义符 | 含义 | 示例输出 |
|--------|------|----------|
| `\n` | 换行 | 换行 |
| `\t` | 制表符 | 缩进 |
| `\a` | 蜂鸣声 | 发出声音 |
| `\\` | 反斜杠 | \ |
| `\"` | 双引号 | " |
| `\'` | 单引号 | ' |

## 💡 使用模式

### 1. 基本输出
```bash
echo "Hello World"           # 双引号
echo Hello World             # 无引号
echo 'Hello World'           # 单引号
```

### 2. 变量输出
```bash
name="Alice"
echo "Hello $name"           # Hello Alice
echo 'Hello $name'           # Hello $name（不解析）
echo "Path: $PATH"           # 显示环境变量
```

### 3. 命令结果
```bash
echo "Date: $(date)"         # Date: Wed Nov 27 12:34:56 2025
echo "Files: $(ls | wc -l)"  # Files: 42
echo "User: $(whoami)"       # User: username
```

### 4. 格式化输出
```bash
echo -e "Line 1\nLine 2"       # 多行输出
echo -e "Name:\tJohn"         # Name:    John
echo -e "\aAlert!"            # 发出蜂鸣声
```

### 5. 文件操作
```bash
echo "Hello" > file.txt      # 创建/覆盖文件
echo "World" >> file.txt     # 追加内容

# 生成配置文件
echo "# Config file" > app.conf
echo "name=myapp" >> app.conf
echo "version=1.0" >> app.conf
```

## 🚀 实用技巧

### 调试脚本
```bash
#!/bin/bash
echo "Script started at $(date)"
echo "Current user: $(whoami)"
echo "Working directory: $(pwd)"

# 处理逻辑...
echo "Processing complete"
```

### 进度显示
```bash
echo -n "Processing... "
# 执行耗时操作
sleep 2
echo "Done!"
```

### 多行文本
```bash
echo -e "Usage: script.sh [options]\n\nOptions:\n  -h    Show help\n  -v    Verbose mode"
```

### 系统信息
```bash
echo "=== System Status ==="
echo "CPU: $(uptime | awk '{print $NF}')"
echo "Memory: $(free -h | grep Mem | awk '{print $3"/"$2}')"
echo "Disk: $(df -h / | tail -1 | awk '{print $5} used')"
```

## ⚠️ 注意事项

1. **引号差异**：
   - 双引号：解析变量和转义符
   - 单引号：保持字面含义
   - 无引号：简单字符串

2. **重定向**：
   - `>` 创建/覆盖文件
   - `>>` 追加到文件
   - `2>` 错误输出重定向

3. **特殊字符**：
   - `$` 在双引号中表示变量
   - `$()` 执行命令替换
   - `\` 转义特殊字符

## 🔄 相关命令对比

| 命令 | 用途 | 特点 |
|------|------|------|
| `echo` | 简单文本输出 | 基础，内置命令 |
| `printf` | 格式化输出 | 更精确的格式控制 |
| `cat` | 显示文件内容 | 多行文本，文件操作 |
| `print` | 某些shell特有 | 不常用 |

记住：`echo` 是最常用的输出命令，掌握它的各种用法对编写脚本至关重要！
