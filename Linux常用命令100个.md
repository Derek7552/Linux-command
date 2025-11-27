# Linux常用命令100个

## 📋 目录
1. [文件和目录操作 (1-25)](#文件和目录操作)
2. [文本处理和编辑 (26-45)](#文本处理和编辑)
3. [系统信息和监控 (46-65)](#系统信息和监控)
4. [进程管理 (66-80)](#进程管理)
5. [网络和通信 (81-90)](#网络和通信)
6. [软件包管理 (91-95)](#软件包管理)
7. [其他实用命令 (96-100)](#其他实用命令)

---

## 文件和目录操作

### 1. `ls` - 列出目录内容
```bash
ls                    # 列出当前目录文件
ls -l                 # 详细列表
ls -a                 # 显示隐藏文件
ls -h                 # 人性化显示大小
```

### 2. `cd` - 切换目录
```bash
cd /home             # 切换到/home目录
cd ..                # 切换到上级目录
cd ~                 # 切换到用户主目录
cd -                 # 切换到上一个目录
```

### 3. `pwd` - 显示当前工作目录
```bash
pwd                  # 显示完整路径
```

### 4. `mkdir` - 创建目录
```bash
mkdir dir1           # 创建单个目录
mkdir -p a/b/c       # 递归创建多层目录
```

### 5. `rmdir` - 删除空目录
```bash
rmdir dir1           # 删除空目录
```

### 6. `touch` - 创建文件或更新时间戳
```bash
touch file.txt       # 创建空文件
touch file1 file2    # 创建多个文件
```

### 7. `cp` - 复制文件和目录
```bash
cp file1 file2       # 复制文件
cp -r dir1 dir2      # 递归复制目录
cp -i file1 file2    # 复制前询问
```

### 8. `mv` - 移动或重命名文件
```bash
mv file1 file2       # 重命名文件
mv file dir/         # 移动文件到目录
mv *.txt docs/       # 移动多个文件
```

### 9. `rm` - 删除文件和目录
```bash
rm file.txt          # 删除文件
rm -r dir/           # 递归删除目录
rm -f file.txt       # 强制删除
rm -i file.txt       # 删除前询问
```

### 10. `cat` - 查看文件内容
```bash
cat file.txt         # 显示文件内容
cat -n file.txt      # 显示行号
cat file1 file2      # 显示多个文件
```

### 11. `more` - 分页查看文件
```bash
more file.txt        # 分页显示文件内容
```

### 12. `less` - 高级分页查看器
```bash
less file.txt        # 查看文件，支持上下滚动
```

### 13. `head` - 显示文件开头内容
```bash
head file.txt        # 显示前10行
head -20 file.txt    # 显示前20行
```

### 14. `tail` - 显示文件结尾内容
```bash
tail file.txt        # 显示后10行
tail -f log.txt      # 实时监控文件变化
```

### 15. `find` - 查找文件
```bash
find . -name "*.txt" # 查找txt文件
find /home -type f   # 查找所有文件
find . -size +1M     # 查找大于1MB的文件
```

### 16. `locate` - 快速文件定位
```bash
locate filename      # 搜索文件（需预先构建数据库）
updatedb             # 更新locate数据库
```

### 17. `which` - 显示命令位置
```bash
which ls             # 显示ls命令的位置
which python         # 显示python解释器位置
```

### 18. `whereis` - 查找命令相关文件
```bash
whereis ls           # 显示ls命令的位置和手册页
```

### 19. `file` - 识别文件类型
```bash
file file.txt        # 显示文件类型
file *               # 显示当前目录所有文件类型
```

### 20. `chmod` - 修改文件权限
```bash
chmod 755 file.sh    # 设置权限为rwxr-xr-x
chmod +x script.sh   # 添加执行权限
chmod -R 644 dir/    # 递归设置目录权限
```

### 21. `chown` - 修改文件所有者
```bash
chown user file.txt  # 修改文件所有者
chown user:group file.txt  # 修改所有者和组
chown -R user dir/   # 递归修改目录所有者
```

### 22. `chgrp` - 修改文件所属组
```bash
chgrp group file.txt # 修改文件所属组
```

### 23. `ln` - 创建链接
```bash
ln file link         # 创建硬链接
ln -s file link      # 创建软链接（符号链接）
```

### 24. `stat` - 显示文件状态
```bash
stat file.txt        # 显示文件详细状态信息
```

### 25. `du` - 显示磁盘使用情况
```bash
du -sh *             # 显示各项目大小
du -h --max-depth=1  # 显示目录大小（一层）
```

---

## 文本处理和编辑

### 26. `echo` - 输出文本
```bash
echo "Hello World"   # 输出文本
echo -n "No newline" # 不换行输出
echo -e "Line\nBreak" # 启用转义字符
```

### 27. `grep` - 文本搜索
```bash
grep "pattern" file  # 搜索包含pattern的行
grep -i "pattern" file # 忽略大小写
grep -n "pattern" file # 显示行号
grep -r "pattern" .   # 递归搜索
```

### 28. `sed` - 流编辑器
```bash
sed 's/old/new/g' file    # 替换文本
sed '/pattern/d' file     # 删除匹配行
sed '1,10d' file          # 删除1-10行
```

### 29. `awk` - 文本处理工具
```bash
awk '{print $1}' file     # 打印第一列
awk '$3 > 100' file       # 条件过滤
awk '{sum += $1} END {print sum}' file  # 计算总和
```

### 30. `sort` - 排序文本
```bash
sort file.txt             # 按字母排序
sort -n numbers.txt       # 按数值排序
sort -r file.txt          # 反向排序
sort -k 2 file.txt        # 按第2列排序
```

### 31. `uniq` - 去除重复行
```bash
uniq file.txt             # 去除相邻重复行
uniq -c file.txt          # 统计重复次数
uniq -d file.txt          # 只显示重复行
```

### 32. `wc` - 统计字数
```bash
wc file.txt               # 显示行数、单词数、字节数
wc -l file.txt            # 只显示行数
wc -w file.txt            # 只显示单词数
wc -c file.txt            # 只显示字节数
```

### 33. `cut` - 剪切文本列
```bash
cut -d: -f1 /etc/passwd   # 以:分割，取第1列
cut -c 1-10 file.txt      # 剪切前10个字符
```

### 34. `paste` - 合并文本行
```bash
paste file1 file2         # 并排合并文件
paste -d, file1 file2     # 用逗号分隔合并
```

### 35. `tr` - 字符转换
```bash
tr 'a-z' 'A-Z' < file     # 小写转大写
tr -d '\n' < file         # 删除换行符
tr ' ' '\n' < file        # 空格转换为换行
```

### 36. `diff` - 比较文件差异
```bash
diff file1 file2          # 显示文件差异
diff -u file1 file2       # 统一格式显示差异
```

### 37. `patch` - 应用补丁
```bash
patch < patchfile         # 应用补丁到文件
patch -p1 < patchfile     # 应用补丁（去除一级路径）
```

### 38. `vim` - 文本编辑器
```bash
vim file.txt              # 编辑文件
vim +10 file.txt          # 打开文件并跳转到第10行
vim -R file.txt           # 只读模式打开
```

### 39. `nano` - 简单文本编辑器
```bash
nano file.txt             # 编辑文件
nano -w file.txt          # 不自动换行
```

### 40. `emacs` - 高级文本编辑器
```bash
emacs file.txt            # 编辑文件
```

### 41. `tee` - 读取标准输入并写入文件
```bash
echo "text" | tee file.txt # 输出到屏幕和文件
command | tee output.txt  # 保存命令输出
```

### 42. `split` - 分割文件
```bash
split -l 1000 largefile   # 按行分割文件
split -b 10M largefile    # 按大小分割文件
```

### 43. `csplit` - 按上下文分割文件
```bash
csplit file.txt /pattern/  # 按模式分割文件
```

### 44. `fmt` - 格式化文本
```bash
fmt file.txt              # 重新格式化文本段落
fmt -w 80 file.txt        # 设置行宽为80字符
```

### 45. `pr` - 格式化打印文本
```bash
pr file.txt               # 为打印格式化文本
pr -2 file.txt            # 双列输出
```

---

## 系统信息和监控

### 46. `uname` - 显示系统信息
```bash
uname                    # 显示操作系统名
uname -a                 # 显示所有系统信息
uname -r                 # 显示内核版本
```

### 47. `hostname` - 显示或设置主机名
```bash
hostname                 # 显示当前主机名
hostname newname         # 设置新主机名（需要权限）
```

### 48. `whoami` - 显示当前用户名
```bash
whoami                   # 显示当前有效用户ID
```

### 49. `id` - 显示用户ID和组ID
```bash
id                       # 显示当前用户ID信息
id username              # 显示指定用户ID信息
```

### 50. `date` - 显示或设置日期时间
```bash
date                     # 显示当前日期时间
date +%Y-%m-%d           # 自定义格式显示
date -s "2024-01-01 12:00:00"  # 设置时间（需要权限）
```

### 51. `cal` - 显示日历
```bash
cal                      # 显示当前月份日历
cal 2024                 # 显示全年日历
cal 12 2023              # 显示指定年月
```

### 52. `uptime` - 显示系统运行时间
```bash
uptime                   # 显示系统运行时间和负载
```

### 53. `who` - 显示登录用户
```bash
who                      # 显示当前登录用户
who -a                   # 显示所有用户信息
```

### 54. `w` - 显示用户详细信息
```bash
w                        # 显示登录用户详细信息
```

### 55. `last` - 显示最近登录历史
```bash
last                     # 显示最近登录记录
last -10                 # 显示最近10条记录
```

### 56. `df` - 显示磁盘使用情况
```bash
df                       # 显示磁盘使用情况
df -h                    # 人性化显示大小
df -i                    # 显示inode使用情况
```

### 57. `free` - 显示内存使用情况
```bash
free                     # 显示内存使用情况
free -h                  # 人性化显示
free -s 2                # 每2秒更新一次
```

### 58. `top` - 实时系统监控
```bash
top                      # 显示系统进程和资源使用
top -u username          # 显示特定用户的进程
```

### 59. `htop` - 增强版进程查看器
```bash
htop                     # 交互式进程查看器
```

### 60. `ps` - 显示进程信息
```bash
ps                       # 显示当前终端进程
ps aux                   # 显示所有进程详细信息
ps -ef                   # 显示完整格式进程信息
```

### 61. `pstree` - 显示进程树
```bash
pstree                   # 显示进程树结构
pstree -p                # 显示进程ID
```

### 62. `vmstat` - 虚拟内存统计
```bash
vmstat                   # 显示虚拟内存统计
vmstat 2                 # 每2秒更新一次
```

### 63. `iostat` - IO统计
```bash
iostat                   # 显示IO统计信息
iostat -x                # 显示扩展统计
```

### 64. `sar` - 系统活动报告
```bash
sar                      # 显示系统活动报告
sar -u                   # 显示CPU使用率
```

### 65. `dmesg` - 显示内核环缓冲区消息
```bash
dmesg                    # 显示内核消息
dmesg | tail -20         # 显示最近20条消息
```

---

## 进程管理

### 66. `kill` - 终止进程
```bash
kill 1234                # 终止进程ID为1234的进程
kill -9 1234             # 强制终止进程
kill -HUP 1234           # 发送HUP信号（重载配置）
```

### 67. `killall` - 按名称终止进程
```bash
killall firefox          # 终止所有firefox进程
killall -9 process       # 强制终止指定名称进程
```

### 68. `pkill` - 按模式终止进程
```bash
pkill firefox            # 终止匹配firefox的进程
pkill -f "script.py"     # 终止命令行包含script.py的进程
```

### 69. `bg` - 将进程放到后台
```bash
bg                       # 将最近的停止进程放到后台
bg %1                    # 将作业1放到后台
```

### 70. `fg` - 将进程调到前台
```bash
fg                       # 将最近的后台进程调到前台
fg %1                    # 将作业1调到前台
```

### 71. `jobs` - 显示后台作业
```bash
jobs                     # 显示后台作业列表
jobs -l                  # 显示详细信息
```

### 72. `nice` - 设置进程优先级
```bash
nice -n 10 command       # 以较低优先级运行命令
nice --10 command        # 以较高优先级运行命令
```

### 73. `renice` - 修改运行中进程优先级
```bash
renice 10 -p 1234        # 修改进程1234的优先级
renice -5 -u username    # 修改用户所有进程的优先级
```

### 74. `nohup` - 忽略挂起信号运行命令
```bash
nohup command &          # 在后台运行，忽略挂起信号
nohup script.sh > output.log 2>&1 &
```

### 75. `screen` - 多窗口终端管理
```bash
screen                   # 启动screen会话
screen -ls               # 列出所有会话
screen -r session        # 恢复会话
```

### 76. `tmux` - 终端多路复用器
```bash
tmux                     # 启动tmux会话
tmux new -s session      # 创建命名会话
tmux ls                  # 列出会话
tmux attach -t session   # 附加到会话
```

### 77. `at` - 在指定时间执行命令
```bash
at 2:30 tomorrow         # 明天2:30执行命令
at now + 1 hour          # 1小时后执行命令
atq                      # 查看at队列
atrm 1                   # 删除at任务
```

### 78. `cron` - 定时任务调度器
```bash
crontab -e               # 编辑crontab文件
crontab -l               # 显示crontab内容
crontab -r               # 删除crontab
```

### 79. `systemctl` - 系统和服务管理器
```bash
systemctl status nginx   # 查看服务状态
systemctl start nginx    # 启动服务
systemctl stop nginx     # 停止服务
systemctl restart nginx  # 重启服务
systemctl enable nginx   # 设置开机自启
```

### 80. `service` - 服务管理（旧式）
```bash
service nginx start      # 启动nginx服务
service nginx stop       # 停止nginx服务
service nginx restart    # 重启nginx服务
```

---

## 网络和通信

### 81. `ping` - 测试网络连通性
```bash
ping google.com          # 测试到主机的连通性
ping -c 4 192.168.1.1    # 发送4个包
ping -i 2 google.com     # 每2秒发送一个包
```

### 82. `traceroute` - 跟踪数据包路径
```bash
traceroute google.com    # 跟踪到主机的路径
traceroute -n 8.8.8.8    # 不解析主机名
```

### 83. `nslookup` - DNS查询
```bash
nslookup google.com      # 查询域名对应的IP
nslookup -type=mx google.com  # 查询邮件服务器
```

### 84. `dig` - DNS查询工具
```bash
dig google.com           # 详细DNS查询
dig google.com A         # 查询A记录
dig google.com MX        # 查询MX记录
```

### 85. `wget` - 下载文件
```bash
wget https://example.com/file.zip  # 下载文件
wget -c url                        # 断点续传
wget -r url                        # 递归下载
wget -O filename url               # 指定保存文件名
```

### 86. `curl` - 传输数据工具
```bash
curl https://api.example.com       # GET请求
curl -X POST -d 'data' url         # POST请求
curl -I url                        # 只获取头部信息
curl -O url                        # 下载文件
```

### 87. `ssh` - 安全远程登录
```bash
ssh user@hostname                  # 远程登录
ssh -p 2222 user@hostname          # 指定端口
ssh -i keyfile user@hostname       # 使用密钥登录
```

### 88. `scp` - 安全文件复制
```bash
scp file.txt user@host:/path/      # 上传文件
scp user@host:/path/file.txt .     # 下载文件
scp -r dir/ user@host:/path/       # 上传目录
```

### 89. `rsync` - 高效文件同步
```bash
rsync -av source/ dest/            # 本地同步
rsync -av source/ user@host:/dest/ # 远程同步
rsync -av --delete source/ dest/   # 镜像同步
```

### 90. `netstat` - 网络连接信息
```bash
netstat -tuln                     # 显示监听端口
netstat -an                       # 显示所有连接
netstat -r                        # 显示路由表
```

---

## 软件包管理

### 91. `apt` (Debian/Ubuntu) - 包管理
```bash
apt update                        # 更新包列表
apt upgrade                       # 升级所有包
apt install package               # 安装包
apt remove package                # 卸载包
apt search keyword                # 搜索包
apt show package                  # 显示包信息
```

### 92. `yum` (RedHat/CentOS) - 包管理
```bash
yum install package               # 安装包
yum remove package                # 卸载包
yum update                        # 更新系统
yum search keyword                # 搜索包
yum info package                  # 显示包信息
```

### 93. `dnf` (新版RedHat) - 包管理
```bash
dnf install package               # 安装包
dnf remove package                # 卸载包
dnf update                        # 更新系统
dnf search keyword                # 搜索包
```

### 94. `pacman` (Arch Linux) - 包管理
```bash
pacman -S package                 # 安装包
pacman -R package                 # 卸载包
pacman -Syu                       # 同步和升级
pacman -Ss keyword                # 搜索包
```

### 95. `snap` - 通用包管理
```bash
snap install package              # 安装snap包
snap remove package               # 卸载包
snap list                         # 列出已安装包
snap find keyword                 # 搜索包
```

---

## 其他实用命令

### 96. `history` - 命令历史
```bash
history                          # 显示命令历史
history 20                       # 显示最近20条命令
!123                             # 执行历史命令123
!!                               # 执行上一条命令
!ls                              # 执行最近的ls命令
```

### 97. `alias` - 创建命令别名
```bash
alias ll='ls -al'                # 创建别名
alias                            # 显示所有别名
unalias ll                       # 删除别名
```

### 98. `tar` - 打包和压缩
```bash
tar -czf archive.tar.gz files    # 创建gzip压缩包
tar -xzf archive.tar.gz          # 解压gzip文件
tar -cJf archive.tar.xz files    # 创建xz压缩包
tar -tzf archive.tar.gz          # 查看压缩包内容
```

### 99. `gzip` - 文件压缩
```bash
gzip file.txt                    # 压缩文件
gzip -d file.txt.gz              # 解压文件
gzip -l file.txt.gz              # 查看压缩信息
```

### 100. `man` - 帮助手册
```bash
man ls                           # 查看ls命令的手册
man -k keyword                   # 搜索相关手册页
man 5 passwd                     # 查看特定章节
```

---

## 🎯 使用提示

1. **组合使用**：很多命令可以组合使用，如 `ps aux | grep nginx`
2. **管道操作**：使用 `|` 将命令输出传递给下一个命令
3. **重定向**：使用 `>`、`>>`、`2>` 等进行输入输出重定向
4. **通配符**：使用 `*`、`?`、`[]` 等进行文件匹配
5. **选项组合**：大多数命令支持选项组合，如 `ls -lah`

## 📚 学习建议

- 从基础命令开始学习（1-25）
- 重点掌握文本处理命令（26-45）
- 熟悉系统管理命令（46-80）
- 学习网络相关命令（81-90）
- 选择适合自己系统的包管理器（91-95）

记住：实践是最好的学习方法！多在实际环境中使用这些命令。
