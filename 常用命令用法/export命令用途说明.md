# export命令用途说明

## 命令简介

`export` 是Linux/Unix系统中的Shell内置命令,用于设置或显示环境变量。它的主要作用是将变量标记为环境变量,使其能够被当前Shell及其所有子进程访问和继承。

## 主要用途

### 1. 设置环境变量
创建新的环境变量或修改已有变量的值,并使其对子进程可见。

**使用场景:**
- 配置系统环境变量
- 设置应用程序所需的环境变量
- 临时修改程序运行环境

**示例:**
```bash
export PATH=/usr/local/bin:$PATH
export JAVA_HOME=/usr/lib/jvm/java-11
export NODE_ENV=production
```

### 2. 查看环境变量
显示当前Shell已导出的所有环境变量及其值。

**使用场景:**
- 检查环境变量配置
- 调试环境变量问题
- 了解系统环境配置

**示例:**
```bash
export              # 显示所有导出的变量
export -p           # 以标准格式显示
export | grep PATH  # 查找特定变量
```

### 3. 导出已存在的Shell变量
将普通Shell变量转换为环境变量,使其可被子进程访问。

**使用场景:**
- 脚本中需要将变量传递给子进程
- 临时提升变量的作用域
- 在多层脚本调用中共享变量

**示例:**
```bash
DB_HOST="localhost"
DB_PORT=3306
export DB_HOST DB_PORT
./app.sh  # 子进程可访问这些变量
```

### 4. 配置开发环境
设置编程语言、工具链和开发框架所需的环境变量。

**使用场景:**
- 配置Java、Python、Node.js等开发环境
- 设置编译器和构建工具路径
- 配置SDK和框架路径

**示例:**
```bash
export JAVA_HOME=/usr/lib/jvm/java-11
export MAVEN_HOME=/opt/maven
export GOPATH=$HOME/go
export GOROOT=/usr/local/go
export PATH=$PATH:$GOPATH/bin:$GOROOT/bin
```

### 5. 应用程序配置
为运行的应用程序设置配置参数和运行模式。

**使用场景:**
- 设置数据库连接信息
- 配置应用运行模式(开发/生产)
- 设置API密钥和访问令牌

**示例:**
```bash
export DATABASE_URL="postgresql://user:pass@localhost:5432/mydb"
export API_KEY="your-api-key-here"
export DEBUG=true
export LOG_LEVEL=info
```

### 6. 国际化和本地化
配置系统语言、字符编码和时区等本地化设置。

**使用场景:**
- 设置系统显示语言
- 配置字符编码格式
- 设置时区和日期格式

**示例:**
```bash
export LANG=zh_CN.UTF-8
export LC_ALL=zh_CN.UTF-8
export TZ=Asia/Shanghai
```

## 典型应用场景

### 脚本环境配置
```bash
#!/bin/bash
# 设置脚本运行环境
export APP_NAME="MyApp"
export APP_VERSION="1.0.0"
export LOG_DIR="/var/log/myapp"
export CONFIG_FILE="/etc/myapp/config.ini"

echo "启动 $APP_NAME v$APP_VERSION"
```

### 临时修改PATH
```bash
# 临时添加自定义命令路径
export PATH=$HOME/bin:$PATH
export PATH=/opt/local/bin:$PATH

# 验证修改
echo $PATH
which mycommand
```

### 多环境切换
```bash
# 开发环境
dev_env() {
    export NODE_ENV=development
    export DB_HOST=localhost
    export DEBUG=true
    echo "切换到开发环境"
}

# 生产环境
prod_env() {
    export NODE_ENV=production
    export DB_HOST=prod.example.com
    export DEBUG=false
    echo "切换到生产环境"
}
```

### 容器化应用配置
```bash
# Docker容器环境变量配置脚本
export CONTAINER_NAME="web-app"
export IMAGE_NAME="myapp:latest"
export MYSQL_ROOT_PASSWORD="secret"
export MYSQL_DATABASE="appdb"
export MYSQL_USER="appuser"
export MYSQL_PASSWORD="apppass"

docker run -d \
  --name $CONTAINER_NAME \
  -e MYSQL_ROOT_PASSWORD \
  -e MYSQL_DATABASE \
  -e MYSQL_USER \
  -e MYSQL_PASSWORD \
  mysql:8.0
```

## 实际案例: Web应用部署脚本

下面是一个完整的实际案例,展示了export命令在实际工作中的综合应用。

**场景说明:** 编写一个Node.js Web应用的自动化部署脚本,需要配置各种环境变量并管理多个环境。

```bash
#!/bin/bash
# Web应用自动化部署脚本
# 功能: 配置环境变量、部署应用、启动服务

# ==================== 基础配置 ====================
export DEPLOY_USER="deploy"
export APP_NAME="my-web-app"
export APP_ROOT="/var/www/$APP_NAME"
export DEPLOY_DATE=$(date '+%Y%m%d_%H%M%S')

echo "=========================================="
echo "部署脚本: $APP_NAME"
echo "部署时间: $DEPLOY_DATE"
echo "=========================================="

# ==================== 环境选择 ====================
if [ "$1" == "prod" ]; then
    export DEPLOY_ENV="production"
    export SERVER_PORT=80
    export DB_HOST="prod-db.example.com"
    export DB_NAME="production_db"
    export REDIS_HOST="prod-redis.example.com"
    export LOG_LEVEL="error"
    export NODE_ENV=production
    echo "目标环境: 生产环境"
elif [ "$1" == "staging" ]; then
    export DEPLOY_ENV="staging"
    export SERVER_PORT=8080
    export DB_HOST="staging-db.example.com"
    export DB_NAME="staging_db"
    export REDIS_HOST="staging-redis.example.com"
    export LOG_LEVEL="info"
    export NODE_ENV=staging
    echo "目标环境: 预发布环境"
else
    export DEPLOY_ENV="development"
    export SERVER_PORT=3000
    export DB_HOST="localhost"
    export DB_NAME="dev_db"
    export REDIS_HOST="localhost"
    export LOG_LEVEL="debug"
    export NODE_ENV=development
    echo "目标环境: 开发环境"
fi

# ==================== 应用配置 ====================
# Node.js配置
export NODE_VERSION="18.x"
export NPM_REGISTRY="https://registry.npmmirror.com"

# 数据库配置
export DB_PORT=3306
export DB_USER="app_user"
# 从密钥管理系统获取密码(示例)
export DB_PASSWORD=$(cat /etc/secrets/db_password)

# Redis配置
export REDIS_PORT=6379
export REDIS_PASSWORD=$(cat /etc/secrets/redis_password)

# 应用特定配置
export MAX_UPLOAD_SIZE="10mb"
export SESSION_SECRET=$(openssl rand -hex 32)
export JWT_SECRET=$(cat /etc/secrets/jwt_secret)
export API_TIMEOUT=30000

# CDN和静态资源
export CDN_URL="https://cdn.example.com"
export STATIC_PATH="$APP_ROOT/public"

# 日志配置
export LOG_DIR="/var/log/$APP_NAME"
export LOG_MAX_SIZE="100m"
export LOG_MAX_FILES=10

echo ""
echo "环境变量配置完成:"
echo "- 运行环境: $NODE_ENV"
echo "- 服务端口: $SERVER_PORT"
echo "- 数据库: $DB_HOST:$DB_PORT/$DB_NAME"
echo "- Redis: $REDIS_HOST:$REDIS_PORT"
echo "- 日志目录: $LOG_DIR"

# ==================== 前置检查 ====================
echo ""
echo "【步骤1】前置环境检查"

# 检查Node.js版本
if ! command -v node &> /dev/null; then
    echo "错误: 未安装Node.js"
    exit 1
fi

CURRENT_NODE_VERSION=$(node -v)
echo "Node.js版本: $CURRENT_NODE_VERSION"

# 检查必要目录
for dir in "$APP_ROOT" "$LOG_DIR" "$STATIC_PATH"; do
    if [ ! -d "$dir" ]; then
        echo "创建目录: $dir"
        mkdir -p "$dir"
    fi
done

# ==================== 代码部署 ====================
echo ""
echo "【步骤2】部署应用代码"

cd $APP_ROOT || exit 1

# 从Git拉取最新代码
if [ "$DEPLOY_ENV" == "production" ]; then
    export GIT_BRANCH="main"
else
    export GIT_BRANCH="develop"
fi

echo "拉取分支: $GIT_BRANCH"
git fetch origin
git checkout $GIT_BRANCH
git pull origin $GIT_BRANCH

# 记录部署版本
export COMMIT_HASH=$(git rev-parse --short HEAD)
echo "部署版本: $COMMIT_HASH"

# ==================== 依赖安装 ====================
echo ""
echo "【步骤3】安装依赖"

# 设置npm镜像
npm config set registry $NPM_REGISTRY

# 安装依赖
if [ "$NODE_ENV" == "production" ]; then
    npm ci --only=production
else
    npm install
fi

# ==================== 构建应用 ====================
echo ""
echo "【步骤4】构建应用"

# 构建前端资源
npm run build

# 生成配置文件
cat > $APP_ROOT/.env << EOF
# 自动生成的环境配置文件
# 生成时间: $DEPLOY_DATE
# 部署环境: $DEPLOY_ENV

NODE_ENV=$NODE_ENV
PORT=$SERVER_PORT

# 数据库配置
DB_HOST=$DB_HOST
DB_PORT=$DB_PORT
DB_NAME=$DB_NAME
DB_USER=$DB_USER
DB_PASSWORD=$DB_PASSWORD

# Redis配置
REDIS_HOST=$REDIS_HOST
REDIS_PORT=$REDIS_PORT
REDIS_PASSWORD=$REDIS_PASSWORD

# 应用配置
SESSION_SECRET=$SESSION_SECRET
JWT_SECRET=$JWT_SECRET
API_TIMEOUT=$API_TIMEOUT
MAX_UPLOAD_SIZE=$MAX_UPLOAD_SIZE

# CDN配置
CDN_URL=$CDN_URL
STATIC_PATH=$STATIC_PATH

# 日志配置
LOG_DIR=$LOG_DIR
LOG_LEVEL=$LOG_LEVEL
LOG_MAX_SIZE=$LOG_MAX_SIZE
LOG_MAX_FILES=$LOG_MAX_FILES

# 版本信息
APP_VERSION=$COMMIT_HASH
DEPLOY_DATE=$DEPLOY_DATE
EOF

echo ".env配置文件已生成"

# ==================== 数据库迁移 ====================
echo ""
echo "【步骤5】数据库迁移"

# 运行数据库迁移
npm run migrate

# ==================== 启动服务 ====================
echo ""
echo "【步骤6】启动应用服务"

# 使用PM2管理进程
if command -v pm2 &> /dev/null; then
    # PM2配置
    export PM2_INSTANCES=4
    export PM2_MAX_MEMORY="500M"

    # 停止旧服务
    pm2 stop $APP_NAME 2>/dev/null || true

    # 启动新服务
    pm2 start npm \
        --name $APP_NAME \
        --instances $PM2_INSTANCES \
        --max-memory-restart $PM2_MAX_MEMORY \
        -- start

    # 保存PM2配置
    pm2 save

    echo "应用已通过PM2启动"
else
    # 直接启动
    nohup npm start > $LOG_DIR/app.log 2>&1 &
    echo $! > $APP_ROOT/app.pid
    echo "应用已启动, PID: $(cat $APP_ROOT/app.pid)"
fi

# ==================== 健康检查 ====================
echo ""
echo "【步骤7】健康检查"

sleep 5

# 检查端口监听
if netstat -tuln | grep ":$SERVER_PORT " > /dev/null; then
    echo "端口检查: 服务正在监听 $SERVER_PORT"
else
    echo "警告: 端口 $SERVER_PORT 未在监听"
fi

# HTTP健康检查
HEALTH_URL="http://localhost:$SERVER_PORT/health"
if curl -f -s $HEALTH_URL > /dev/null; then
    echo "健康检查: 应用运行正常"
else
    echo "警告: 健康检查失败"
fi

# ==================== 部署完成 ====================
echo ""
echo "=========================================="
echo "部署完成!"
echo "=========================================="
echo "环境: $DEPLOY_ENV"
echo "版本: $COMMIT_HASH"
echo "端口: $SERVER_PORT"
echo "时间: $DEPLOY_DATE"
echo ""
echo "查看日志: tail -f $LOG_DIR/app.log"
echo "查看状态: pm2 status $APP_NAME"
echo "=========================================="

# 导出部署信息供后续脚本使用
export DEPLOY_SUCCESS=true
export DEPLOYED_VERSION=$COMMIT_HASH
```

**脚本运行效果:**
```
==========================================
部署脚本: my-web-app
部署时间: 20251204_143025
==========================================
目标环境: 生产环境

环境变量配置完成:
- 运行环境: production
- 服务端口: 80
- 数据库: prod-db.example.com:3306/production_db
- Redis: prod-redis.example.com:6379
- 日志目录: /var/log/my-web-app

【步骤1】前置环境检查
Node.js版本: v18.17.0
创建目录: /var/log/my-web-app

【步骤2】部署应用代码
拉取分支: main
部署版本: a3f5d8c

【步骤3】安装依赖
added 342 packages in 15s

【步骤4】构建应用
.env配置文件已生成

【步骤5】数据库迁移
Migration completed: 3 migrations applied

【步骤6】启动应用服务
应用已通过PM2启动

【步骤7】健康检查
端口检查: 服务正在监听 80
健康检查: 应用运行正常

==========================================
部署完成!
==========================================
环境: production
版本: a3f5d8c
端口: 80
时间: 20251204_143025

查看日志: tail -f /var/log/my-web-app/app.log
查看状态: pm2 status my-web-app
==========================================
```

**案例分析:**

这个部署脚本综合运用了export命令的多种功能:

1. **环境配置**: 根据部署环境设置不同的变量值
2. **安全管理**: 从密钥文件读取敏感信息
3. **配置生成**: 使用环境变量生成应用配置文件
4. **跨进程传递**: 环境变量在子进程(npm、git等)中可用
5. **状态记录**: 导出部署状态供后续脚本使用
6. **灵活配置**: 支持多环境切换和参数化配置

**实用价值:**
- 统一管理应用配置,避免硬编码
- 支持多环境部署,配置清晰
- 安全存储敏感信息
- 便于CI/CD集成
- 易于维护和扩展

## 为什么常用export

1. **变量传递**: 唯一能将变量传递给子进程的方式
2. **环境隔离**: 为不同应用配置独立的运行环境
3. **配置灵活**: 无需修改代码即可改变程序行为
4. **标准做法**: Linux/Unix系统配置的标准方法
5. **工具兼容**: 几乎所有命令行工具都支持环境变量

## 与普通变量的区别

**普通Shell变量:**
```bash
VAR="value"          # 仅当前Shell可用
./script.sh          # 子进程无法访问VAR
```

**环境变量:**
```bash
export VAR="value"   # 当前Shell及子进程都可用
./script.sh          # 子进程可以访问VAR
```

## 常见配置位置

永久设置环境变量通常在以下文件中:

- `~/.bashrc`: 用户级别,非登录Shell
- `~/.bash_profile`: 用户级别,登录Shell
- `~/.profile`: 用户级别,通用配置
- `/etc/environment`: 系统级别,所有用户
- `/etc/profile`: 系统级别,登录Shell

**示例:**
```bash
# 添加到 ~/.bashrc
echo 'export JAVA_HOME=/usr/lib/jvm/java-11' >> ~/.bashrc
echo 'export PATH=$PATH:$JAVA_HOME/bin' >> ~/.bashrc
source ~/.bashrc  # 重新加载配置
```

## 总结

`export` 命令是Shell编程和系统配置的核心工具,它使得环境变量能够在进程间传递,为应用程序提供配置参数。掌握export的使用对于脚本开发、应用部署和系统管理至关重要。无论是简单的路径设置,还是复杂的多环境应用部署,export都扮演着不可或缺的角色。

---

*参考资料: Linux-command/commands/references/export命令快速参考.md*
