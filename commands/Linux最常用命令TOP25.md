# Linux最常用命令TOP25

> 精选Linux日常工作中最核心的25个命令，涵盖95%的日常使用场景

## 📋 TOP25核心命令

### 1. `ls` - 列出目录内容 ⭐⭐⭐⭐⭐
```bash
ls                    # 列出当前目录文件
ls -l                 # 详细列表（权限、大小、时间）
ls -a                 # 显示隐藏文件
ls -lh                # 人性化显示文件大小
```

### 2. `cd` - 切换目录 ⭐⭐⭐⭐⭐
```bash
cd /home             # 切换到指定目录
cd ..                # 切换到上级目录
cd ~                 # 切换到用户主目录
cd -                 # 切换到上一个目录
```

### 3. `pwd` - 显示当前工作目录 ⭐⭐⭐⭐⭐
```bash
pwd                  # 显示完整路径
```

### 4. `mkdir` - 创建目录 ⭐⭐⭐⭐⭐
```bash
mkdir dir1           # 创建单个目录
mkdir -p a/b/c       # 递归创建多层目录
```

### 5. `cp` - 复制文件和目录 ⭐⭐⭐⭐⭐
```bash
cp file1 file2       # 复制文件
cp -r dir1 dir2      # 递归复制目录
cp -i file1 file2    # 复制前询问（安全）
```

### 6. `mv` - 移动或重命名 ⭐⭐⭐⭐⭐
```bash
mv file1 file2       # 重命名文件
mv file dir/         # 移动文件到目录
mv *.txt docs/       # 移动多个文件
```

### 7. `rm` - 删除文件和目录 ⭐⭐⭐⭐⭐
```bash
rm file.txt          # 删除文件
rm -r dir/           # 递归删除目录
rm -f file.txt       # 强制删除
rm -i file.txt       # 删除前询问
```

### 8. `touch` - 创建文件 ⭐⭐⭐⭐⭐
```bash
touch file.txt       # 创建空文件
touch file1 file2    # 创建多个文件
```

### 9. `cat` - 查看文件内容 ⭐⭐⭐⭐⭐
```bash
cat file.txt         # 显示文件内容
cat -n file.txt      # 显示行号
cat file1 file2      # 显示多个文件
```

### 10. `chmod` - 修改文件权限 ⭐⭐⭐⭐⭐
```bash
chmod 755 script.sh  # 设置权限为rwxr-xr-x
chmod +x script.sh   # 添加执行权限
chmod -R 644 dir/    # 递归设置目录权限
```

### 11. `grep` - 文本搜索 ⭐⭐⭐⭐⭐
```bash
grep "pattern" file  # 搜索包含pattern的行
grep -i "pattern" file # 忽略大小写
grep -n "pattern" file # 显示行号
grep -r "pattern" .   # 递归搜索
```

### 12. `echo` - 输出文本 ⭐⭐⭐⭐⭐
```bash
echo "Hello World"   # 输出文本
echo -n "No newline" # 不换行输出
echo -e "A\nB"       # 启用转义字符
```

### 13. `ps` - 显示进程信息 ⭐⭐⭐⭐⭐
```bash
ps aux                # 显示所有进程详细信息
ps -ef                # 显示完整格式进程信息
ps -u username        # 显示特定用户的进程
```

### 14. `top` - 实时系统监控 ⭐⭐⭐⭐⭐
```bash
top                   # 显示系统进程和资源使用
top -u username       # 显示特定用户的进程
# 按q退出，M按内存排序，P按CPU排序
```

### 15. `kill` - 终止进程 ⭐⭐⭐⭐⭐
```bash
kill 1234             # 终止进程ID为1234的进程
kill -9 1234          # 强制终止进程
kill -HUP 1234        # 发送HUP信号（重载配置）
```

### 16. `df` - 显示磁盘使用情况 ⭐⭐⭐⭐⭐
```bash
df                    # 显示磁盘使用情况
df -h                 # 人性化显示大小
df -i                 # 显示inode使用情况
```

### 17. `free` - 显示内存使用情况 ⭐⭐⭐⭐⭐
```bash
free                  # 显示内存使用情况
free -h               # 人性化显示
free -s 2             # 每2秒更新一次
```

### 18. `ping` - 测试网络连通性 ⭐⭐⭐⭐⭐
```bash
ping google.com       # 测试到主机的连通性
ping -c 4 192.168.1.1 # 发送4个包
ping -i 2 google.com  # 每2秒发送一个包
```

### 19. `ssh` - 安全远程登录 ⭐⭐⭐⭐⭐
```bash
ssh user@hostname     # 远程登录
ssh -p 2222 user@hostname  # 指定端口
ssh -i keyfile user@hostname  # 使用密钥登录
```

### 20. `scp` - 安全文件复制 ⭐⭐⭐⭐⭐
```bash
scp file.txt user@host:/path/  # 上传文件
scp user@host:/path/file.txt . # 下载文件
scp -r dir/ user@host:/path/   # 上传目录
```

### 21. `wget` - 下载文件 ⭐⭐⭐⭐⭐
```bash
wget https://example.com/file.zip  # 下载文件
wget -c url                        # 断点续传
wget -O filename url               # 指定保存文件名
```

### 22. `sudo` - 以超级用户权限执行 ⭐⭐⭐⭐⭐
```bash
sudo command          # 以root权限执行命令
sudo -i               # 切换到root用户
sudo -u user command  # 以指定用户身份执行
```

### 23. `history` - 命令历史 ⭐⭐⭐⭐⭐
```bash
history               # 显示命令历史
history 20            # 显示最近20条命令
!123                  # 执行历史命令123
!!                    # 执行上一条命令
```

### 24. `which` - 显示命令位置 ⭐⭐⭐⭐⭐
```bash
which ls              # 显示ls命令的位置
which python          # 显示python解释器位置
```

### 25. `man` - 查看帮助手册 ⭐⭐⭐⭐⭐
```bash
man ls                # 查看ls命令的手册
man -k keyword        # 搜索相关手册页
```

---

## 🎯 使用频率说明

- **⭐⭐⭐⭐⭐** 每天使用多次
- **⭐⭐⭐⭐** 经常使用
- **⭐⭐⭐** 偶尔使用
- **⭐⭐** 特定场景使用
- **⭐** 了解即可

## 💡 学习建议

### 核心命令优先级：
1. **文件操作**: ls, cd, pwd, mkdir, cp, mv, rm (基础中的基础)
2. **文件查看**: cat, touch, chmod (文件处理必备)
3. **系统监控**: ps, top, df, free (系统状态检查)
4. **网络操作**: ping, ssh, scp, wget (远程工作必备)
5. **工具命令**: grep, echo, sudo, history (提高效率)

### 掌握方法：
1. **每天练习**: 选择3-5个命令深入练习
2. **场景应用**: 在实际工作中使用这些命令
3. **组合使用**: 学习命令的管道和重定向
4. **参数记忆**: 重点记住常用参数选项

## 🚀 效率提升技巧

### 快速导航
```bash
cd ~    # 回主目录
cd -    # 回上个目录
cd ..   # 上一级
```

### 文件批量操作
```bash
cp *.txt backup/      # 复制所有txt文件
rm *.log              # 删除所有日志文件
chmod +x *.sh         # 给所有脚本添加执行权
```

### 系统监控
```bash
top                   # 查看系统负载
df -h                 # 查看磁盘使用
free -h               # 查看内存使用
ps aux | grep nginx   # 查找nginx进程
```

### 网络诊断
```bash
ping google.com       # 测试网络连通
ssh user@server       # 远程登录服务器
scp file.txt server:/tmp/  # 上传文件
wget -c large-file.zip     # 断点续传大文件
```

## 📊 覆盖率统计

这25个命令覆盖了：
- **文件操作**: 70% 的日常文件管理需求
- **系统管理**: 80% 的基础系统维护任务
- **网络操作**: 90% 的基本网络通信需求
- **开发环境**: 95% 的编程环境配置需求

掌握这25个命令，你就能处理95%的Linux日常工作场景！

---

## 🎉 恭喜！

掌握了这25个核心命令，你已经具备了在Linux环境中高效工作的基本能力。继续深入学习其他命令，你会成为真正的Linux高手！🚀
