# Linux最常用命令50个

> 精选Linux日常工作中最常用的50个命令，按使用频率排序

## 📋 目录
1. [文件和目录操作 (1-15)](#文件和目录操作)
2. [文本处理和查看 (16-25)](#文本处理和查看)
3. [系统管理与监控 (26-35)](#系统管理与监控)
4. [网络和远程操作 (36-42)](#网络和远程操作)
5. [其他实用工具 (43-50)](#其他实用工具)

---

## 文件和目录操作

### 1. `ls` - 列出目录内容 ⭐⭐⭐⭐⭐
```bash
ls                    # 列出当前目录文件
ls -l                 # 详细列表（权限、大小、时间）
ls -a                 # 显示隐藏文件
ls -lh                # 人性化显示文件大小
ls -lt                # 按时间排序
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
mkdir dir1 dir2      # 创建多个目录
```

### 5. `cp` - 复制文件和目录 ⭐⭐⭐⭐⭐
```bash
cp file1 file2       # 复制文件
cp -r dir1 dir2      # 递归复制目录
cp -i file1 file2    # 复制前询问（安全）
cp -v file1 file2    # 显示复制过程
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
rm -f file.txt       # 强制删除（不询问）
rm -i file.txt       # 删除前询问
```

### 8. `touch` - 创建文件或更新时间戳 ⭐⭐⭐⭐⭐
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

### 10. `find` - 查找文件 ⭐⭐⭐⭐⭐
```bash
find . -name "*.txt" # 查找当前目录的txt文件
find /home -type f   # 查找所有文件
find . -size +1M     # 查找大于1MB的文件
```

### 11. `chmod` - 修改文件权限 ⭐⭐⭐⭐⭐
```bash
chmod 755 script.sh  # 设置权限为rwxr-xr-x
chmod +x script.sh   # 添加执行权限
chmod -R 644 dir/    # 递归设置目录权限
```

### 12. `chown` - 修改文件所有者 ⭐⭐⭐⭐
```bash
chown user file.txt  # 修改文件所有者
chown user:group file.txt  # 修改所有者和组
chown -R user dir/   # 递归修改目录所有者
```

### 13. `tar` - 打包和压缩 ⭐⭐⭐⭐⭐
```bash
tar -czf archive.tar.gz files    # 创建gzip压缩包
tar -xzf archive.tar.gz          # 解压gzip文件
tar -tf archive.tar.gz           # 查看压缩包内容
```

### 14. `ln` - 创建链接 ⭐⭐⭐⭐
```bash
ln file link         # 创建硬链接
ln -s file link      # 创建软链接（符号链接）
```

### 15. `du` - 显示磁盘使用情况 ⭐⭐⭐⭐
```bash
du -sh *             # 显示各项目大小
du -h --max-depth=1  # 显示目录大小
```

---

## 文本处理和查看

### 16. `grep` - 文本搜索 ⭐⭐⭐⭐⭐
```bash
grep "pattern" file  # 搜索包含pattern的行
grep -i "pattern" file # 忽略大小写
grep -n "pattern" file # 显示行号
grep -r "pattern" .   # 递归搜索
```

### 17. `echo` - 输出文本 ⭐⭐⭐⭐⭐
```bash
echo "Hello World"   # 输出文本
echo -n "No newline" # 不换行输出
echo -e "A\nB"       # 启用转义字符
```

### 18. `less` - 分页查看文件 ⭐⭐⭐⭐⭐
```bash
less file.txt        # 查看文件（支持上下滚动）
# 按q退出，/pattern搜索
```

### 19. `head` - 显示文件开头 ⭐⭐⭐⭐⭐
```bash
head file.txt        # 显示前10行
head -20 file.txt    # 显示前20行
head -5 file.txt     # 显示前5行
```

### 20. `tail` - 显示文件结尾 ⭐⭐⭐⭐⭐
```bash
tail file.txt        # 显示后10行
tail -f log.txt      # 实时监控文件变化
tail -20 file.txt    # 显示后20行
```

### 21. `sort` - 排序文本 ⭐⭐⭐⭐
```bash
sort file.txt        # 按字母排序
sort -n numbers.txt  # 按数值排序
sort -r file.txt     # 反向排序
sort -k 2 file.txt   # 按第2列排序
```

### 22. `uniq` - 去除重复行 ⭐⭐⭐⭐
```bash
sort file.txt | uniq # 去除重复行
uniq -c file.txt     # 统计重复次数
uniq -d file.txt     # 只显示重复行
```

### 23. `wc` - 统计字数 ⭐⭐⭐⭐
```bash
wc file.txt          # 显示行数、单词数、字节数
wc -l file.txt       # 只显示行数
wc -w file.txt       # 只显示单词数
```

### 24. `sed` - 流编辑器 ⭐⭐⭐⭐
```bash
sed 's/old/new/g' file    # 替换文本
sed '/pattern/d' file     # 删除匹配行
sed '1,10d' file          # 删除1-10行
```

### 25. `awk` - 文本处理工具 ⭐⭐⭐⭐
```bash
awk '{print $1}' file     # 打印第一列
awk '$3 > 100' file       # 条件过滤
awk '{sum += $1} END {print sum}' file  # 计算总和
```

---

## 系统管理与监控

### 26. `ps` - 显示进程信息 ⭐⭐⭐⭐⭐
```bash
ps aux                # 显示所有进程详细信息
ps -ef                # 显示完整格式进程信息
ps -u username        # 显示特定用户的进程
```

### 27. `top` - 实时系统监控 ⭐⭐⭐⭐⭐
```bash
top                   # 显示系统进程和资源使用
top -u username       # 显示特定用户的进程
# 按q退出，M按内存排序，P按CPU排序
```

### 28. `kill` - 终止进程 ⭐⭐⭐⭐⭐
```bash
kill 1234             # 终止进程ID为1234的进程
kill -9 1234          # 强制终止进程
kill -HUP 1234        # 发送HUP信号（重载配置）
```

### 29. `df` - 显示磁盘使用情况 ⭐⭐⭐⭐⭐
```bash
df                    # 显示磁盘使用情况
df -h                 # 人性化显示大小
df -i                 # 显示inode使用情况
```

### 30. `free` - 显示内存使用情况 ⭐⭐⭐⭐⭐
```bash
free                  # 显示内存使用情况
free -h               # 人性化显示
free -s 2             # 每2秒更新一次
```

### 31. `uptime` - 显示系统运行时间 ⭐⭐⭐⭐⭐
```bash
uptime                # 显示系统运行时间和负载
```

### 32. `whoami` - 显示当前用户名 ⭐⭐⭐⭐⭐
```bash
whoami                # 显示当前有效用户ID
```

### 33. `id` - 显示用户ID和组ID ⭐⭐⭐⭐
```bash
id                    # 显示当前用户ID信息
id username           # 显示指定用户ID信息
```

### 34. `uname` - 显示系统信息 ⭐⭐⭐⭐⭐
```bash
uname                 # 显示操作系统名
uname -a              # 显示所有系统信息
uname -r              # 显示内核版本
```

### 35. `date` - 显示或设置日期时间 ⭐⭐⭐⭐⭐
```bash
date                  # 显示当前日期时间
date +%Y-%m-%d        # 自定义格式显示
date -s "2024-01-01 12:00:00"  # 设置时间（需要权限）
```

---

## 网络和远程操作

### 36. `ping` - 测试网络连通性 ⭐⭐⭐⭐⭐
```bash
ping google.com       # 测试到主机的连通性
ping -c 4 192.168.1.1 # 发送4个包
ping -i 2 google.com  # 每2秒发送一个包
```

### 37. `ssh` - 安全远程登录 ⭐⭐⭐⭐⭐
```bash
ssh user@hostname     # 远程登录
ssh -p 2222 user@hostname  # 指定端口
ssh -i keyfile user@hostname  # 使用密钥登录
```

### 38. `scp` - 安全文件复制 ⭐⭐⭐⭐⭐
```bash
scp file.txt user@host:/path/  # 上传文件
scp user@host:/path/file.txt . # 下载文件
scp -r dir/ user@host:/path/   # 上传目录
```

### 39. `wget` - 下载文件 ⭐⭐⭐⭐⭐
```bash
wget https://example.com/file.zip  # 下载文件
wget -c url                        # 断点续传
wget -O filename url               # 指定保存文件名
```

### 40. `curl` - 传输数据工具 ⭐⭐⭐⭐⭐
```bash
curl https://api.example.com       # GET请求
curl -O url                        # 下载文件
curl -X POST -d 'data' url         # POST请求
```

### 41. `ifconfig` - 配置网络接口 ⭐⭐⭐⭐
```bash
ifconfig              # 显示网络接口信息
ifconfig eth0         # 显示指定接口信息
```

### 42. `netstat` - 网络连接信息 ⭐⭐⭐⭐
```bash
netstat -tuln         # 显示监听端口
netstat -an           # 显示所有连接
netstat -r            # 显示路由表
```

---

## 其他实用工具

### 43. `history` - 命令历史 ⭐⭐⭐⭐⭐
```bash
history               # 显示命令历史
history 20            # 显示最近20条命令
!123                  # 执行历史命令123
!!                    # 执行上一条命令
```

### 44. `alias` - 创建命令别名 ⭐⭐⭐⭐⭐
```bash
alias ll='ls -al'     # 创建别名
alias                  # 显示所有别名
unalias ll            # 删除别名
```

### 45. `man` - 查看帮助手册 ⭐⭐⭐⭐⭐
```bash
man ls                # 查看ls命令的手册
man -k keyword        # 搜索相关手册页
```

### 46. `which` - 显示命令位置 ⭐⭐⭐⭐⭐
```bash
which ls              # 显示ls命令的位置
which python          # 显示python解释器位置
```

### 47. `sudo` - 以超级用户权限执行 ⭐⭐⭐⭐⭐
```bash
sudo command          # 以root权限执行命令
sudo -i               # 切换到root用户
sudo -u user command  # 以指定用户身份执行
```

### 48. `passwd` - 修改密码 ⭐⭐⭐⭐⭐
```bash
passwd                # 修改当前用户密码
sudo passwd username  # 修改其他用户密码
```

### 49. `clear` - 清屏 ⭐⭐⭐⭐⭐
```bash
clear                 # 清空终端屏幕
```

### 50. `exit` - 退出当前shell ⭐⭐⭐⭐⭐
```bash
exit                  # 退出当前shell会话
exit 0                # 正常退出（返回状态0）
```

---

## 🎯 使用频率说明

- **⭐⭐⭐⭐⭐** 每天使用多次
- **⭐⭐⭐⭐** 经常使用
- **⭐⭐⭐** 偶尔使用
- **⭐⭐** 特定场景使用
- **⭐** 了解即可

## 💡 学习建议

1. **基础优先**: 先掌握1-15的命令，这些是日常必备
2. **逐步深入**: 按照顺序学习，不要贪多
3. **实践为主**: 每个命令都要动手练习
4. **组合使用**: 学习命令的管道和重定向组合
5. **查阅手册**: 使用`man`命令获取详细信息

## 🚀 进阶路径

掌握这50个命令后，可以学习：
- Shell脚本编程
- 系统服务管理
- 网络配置
- 安全管理

记住：熟能生巧，多练习是王道！🎉
