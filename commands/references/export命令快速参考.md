# export命令快速参考

## 基本语法
```bash
export [选项] [变量名=值]
export [选项] [变量名]
```

## 常用选项

| 选项 | 含义 | 示例 |
|------|------|------|
| 无选项 | 显示所有导出的变量 | `export` |
| `-p` | 以标准格式显示所有导出的变量 | `export -p` |
| `-n` | 取消变量的导出属性 | `export -n VAR` |
| `-f` | 导出函数而非变量 | `export -f function_name` |

## 使用模式

### 1. 设置环境变量
```bash
export PATH=/usr/local/bin:$PATH
export JAVA_HOME=/usr/lib/jvm/java-11
export NODE_ENV=production
```

### 2. 设置多个变量
```bash
# 一行设置多个
export VAR1="value1" VAR2="value2"

# 分行设置
export DB_HOST="localhost"
export DB_PORT=3306
export DB_NAME="mydb"
```

### 3. 导出已存在的变量
```bash
# 先定义变量
VAR="hello"

# 再导出
export VAR

# 或者一起导出多个
export VAR1 VAR2 VAR3
```

### 4. 查看环境变量
```bash
export                  # 显示所有导出的变量
export -p               # 以declare格式显示
export | grep PATH      # 查找特定变量
printenv PATH           # 查看单个变量
echo $PATH              # 显示变量值
```

### 5. 取消导出
```bash
export -n VARIABLE      # 取消导出,但变量仍存在
unset VARIABLE          # 完全删除变量
```

## 实用场景

### 配置PATH路径
```bash
# 添加到PATH开头
export PATH=/new/path:$PATH

# 添加到PATH末尾
export PATH=$PATH:/new/path

# 添加多个路径
export PATH=/path1:/path2:$PATH
```

### 开发环境配置
```bash
# Java环境
export JAVA_HOME=/usr/lib/jvm/java-11
export PATH=$PATH:$JAVA_HOME/bin

# Python虚拟环境
export VIRTUAL_ENV=/path/to/venv
export PATH=$VIRTUAL_ENV/bin:$PATH

# Node.js
export NODE_ENV=development
export NPM_CONFIG_PREFIX=~/.npm-global
```

### 应用程序配置
```bash
# 数据库配置
export DATABASE_URL="postgresql://user:pass@localhost/db"
export DB_POOL_SIZE=10

# API密钥
export API_KEY="your-secret-key"
export API_ENDPOINT="https://api.example.com"

# 日志配置
export LOG_LEVEL=debug
export LOG_FILE=/var/log/app.log
```

### 本地化设置
```bash
export LANG=zh_CN.UTF-8
export LC_ALL=zh_CN.UTF-8
export TZ=Asia/Shanghai
```

## 实用技巧

### 临时环境变量
```bash
# 仅对单个命令有效
VAR=value command

# 对当前会话有效
export VAR=value
```

### 条件设置
```bash
# 如果变量未设置则设置
export PATH=${PATH:-/usr/local/bin}

# 追加路径(避免重复)
[[ ":$PATH:" != *":/new/path:"* ]] && export PATH=$PATH:/new/path
```

### 从文件加载
```bash
# 加载.env文件
set -a
source .env
set +a

# 或者
export $(cat .env | xargs)
```

### 脚本中使用
```bash
#!/bin/bash
# 设置脚本环境
export APP_NAME="myapp"
export VERSION="1.0.0"

# 子进程继承这些变量
./run_app.sh
```

### 环境切换
```bash
# 开发环境
dev() {
    export ENV=dev
    export DEBUG=true
    export DB_HOST=localhost
}

# 生产环境
prod() {
    export ENV=prod
    export DEBUG=false
    export DB_HOST=prod.example.com
}

# 使用: dev 或 prod
```

## 常见环境变量

### 系统变量
```bash
export PATH              # 可执行文件搜索路径
export HOME              # 用户主目录
export USER              # 当前用户名
export SHELL             # 当前Shell
export PWD               # 当前工作目录
export LANG              # 系统语言
export EDITOR            # 默认编辑器
export TERM              # 终端类型
```

### 开发相关
```bash
export JAVA_HOME         # Java安装路径
export GOPATH            # Go工作空间
export GOROOT            # Go安装路径
export PYTHONPATH        # Python模块路径
export NODE_ENV          # Node.js环境
export RAILS_ENV         # Rails环境
export DOCKER_HOST       # Docker主机
```

## 注意事项

1. **变量作用域**:
   - 普通变量: 仅当前Shell
   - export变量: 当前Shell + 所有子进程
   - 不影响父进程和兄弟进程

2. **子Shell继承**:
   ```bash
   export VAR="value"
   bash                    # 启动子Shell
   echo $VAR               # 可以访问
   exit
   ```

3. **变量修改**:
   ```bash
   export VAR="old"
   bash                    # 子Shell
   export VAR="new"        # 修改仅在子Shell有效
   exit
   echo $VAR               # 仍是"old"
   ```

4. **引号使用**:
   ```bash
   export VAR="value with spaces"    # 需要引号
   export PATH=$PATH:/new/path       # 无空格可不用引号
   ```

5. **特殊字符**:
   ```bash
   export VAR='$literal'    # 单引号: 字面值
   export VAR="$expanded"   # 双引号: 展开变量
   ```

## 永久设置

### Bash配置文件
```bash
# 用户级 - 非登录Shell
~/.bashrc

# 用户级 - 登录Shell
~/.bash_profile
~/.profile

# 系统级
/etc/environment
/etc/profile
/etc/bash.bashrc
```

### 添加永久配置
```bash
# 方法1: 手动编辑
vim ~/.bashrc
# 添加: export JAVA_HOME=/usr/lib/jvm/java-11

# 方法2: 追加命令
echo 'export JAVA_HOME=/usr/lib/jvm/java-11' >> ~/.bashrc

# 方法3: 使用heredoc
cat >> ~/.bashrc << 'EOF'
export JAVA_HOME=/usr/lib/jvm/java-11
export PATH=$PATH:$JAVA_HOME/bin
EOF

# 重新加载配置
source ~/.bashrc
```

## 调试技巧

### 查看变量是否已导出
```bash
# 方法1
export | grep VAR_NAME

# 方法2
declare -p VAR_NAME

# 方法3
printenv VAR_NAME
```

### 测试子进程继承
```bash
# 测试脚本 test.sh
#!/bin/bash
echo "VAR in child: $VAR"

# 测试
VAR="not exported"
./test.sh              # 输出为空

export VAR="exported"
./test.sh              # 输出: VAR in child: exported
```

## 相关命令对比

| 命令 | 功能 | 变量作用域 |
|------|------|-----------|
| `VAR=value` | 设置Shell变量 | 仅当前Shell |
| `export VAR=value` | 设置环境变量 | 当前Shell+子进程 |
| `declare VAR=value` | 声明变量 | 仅当前Shell |
| `readonly VAR=value` | 只读变量 | 仅当前Shell |
| `env VAR=value cmd` | 临时环境变量 | 仅指定命令 |

## 实战示例

### 完整的环境配置脚本
```bash
#!/bin/bash
# 项目环境配置脚本

# 基础路径
export PROJECT_ROOT="/opt/myproject"
export BIN_DIR="$PROJECT_ROOT/bin"
export LIB_DIR="$PROJECT_ROOT/lib"
export CONF_DIR="$PROJECT_ROOT/config"

# 添加到PATH
export PATH=$BIN_DIR:$PATH

# Java配置
export JAVA_HOME=/usr/lib/jvm/java-11
export CLASSPATH=.:$LIB_DIR/*:$JAVA_HOME/lib

# 应用配置
export APP_ENV=production
export SERVER_PORT=8080
export MAX_MEMORY=2048m

# 数据库
export DB_HOST=localhost
export DB_PORT=3306
export DB_NAME=myapp
export DB_USER=appuser

# 日志
export LOG_DIR=/var/log/myapp
export LOG_LEVEL=info

echo "环境配置完成"
echo "Java版本: $(java -version 2>&1 | head -n 1)"
echo "应用目录: $PROJECT_ROOT"
echo "日志目录: $LOG_DIR"
```

记住: `export` 是配置Shell环境和进程间传递变量的标准方法,掌握它对系统管理和脚本开发至关重要!
