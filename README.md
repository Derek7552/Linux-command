# Linux命令学习项目

一个系统化的Linux命令学习资料库，包含从入门到精通的完整学习路径。

## 📁 项目结构

```
Linux-command/
├── guides/           # 📚 学习指南
│   ├── README.md     # 学习指南导航
│   └── stages/       # 分阶段学习教程
│       ├── 阶段1-基础入门.md
│       ├── 阶段2-文本处理.md
│       ├── 阶段3-系统管理.md
│       └── 阶段4-网络与高级应用.md
├── commands/         # 🛠️ 命令合集
│   ├── README.md     # 命令合集导航
│   ├── essentials/   # ⭐ 精华命令合集
│   │   ├── Linux最常用命令TOP25.md
│   │   └── Linux最常用命令50个.md
│   ├── collections/  # 📋 完整命令合集
│   │   ├── Linux常用命令100个.md
│   │   └── Linux命令学习大纲.md
│   └── references/   # 🔍 专项参考资料
│       ├── echo命令快速参考.md
│       └── Linux特殊符号快速参考.md
├── docs/            # 📖 项目文档
│   ├── README.md    # 文档导航
│   └── project/     # 项目维护文档
│       └── README.md
└── .cursor/         # ⚙️ Cursor IDE配置
    └── git-workflow.md
```

## 🚀 快速开始

### 新手推荐学习路径
1. **第一步**: 阅读 [`guides/stages/阶段1-基础入门.md`](guides/stages/阶段1-基础入门.md)
2. **第二步**: 学习 [`commands/essentials/Linux最常用命令TOP25.md`](commands/essentials/Linux最常用命令TOP25.md)
3. **第三步**: 按照阶段顺序深入学习

### 查找特定内容
- **学习指南**: 查看 [`guides/`](guides/) 目录
- **命令合集**: 查看 [`commands/`](commands/) 目录
- **项目文档**: 查看 [`docs/`](docs/) 目录

## 🎯 学习目标

- ✅ 掌握Linux系统中最常用的命令
- ✅ 建立系统化的命令行操作思维
- ✅ 提高工作效率和问题解决能力
- ✅ 为系统管理和DevOps打下基础

## 📊 内容概览

| 分类 | 文档数量 | 主要内容 | 适合人群 |
|------|----------|----------|----------|
| 学习指南 | 5个文档 | 分阶段系统学习教程 | 所有学习者 |
| 命令合集 | 6个文档 | TOP25/50/100命令合集 | 按需求选择 |
| 专项参考 | 2个文档 | echo命令和特殊符号详解 | 深入学习者 |
| 项目文档 | 3个文档 | 项目介绍和维护指南 | 贡献者和维护者 |

## 📖 学习建议

### 学习节奏
- **每天**: 1-2个小时的学习时间
- **每周**: 完成1个阶段的学习
- **每月**: 进行一次综合复习

### 学习方法
1. **循序渐进**: 按照阶段顺序逐步学习
2. **动手实践**: 每个命令都要在终端中练习
3. **理解原理**: 不仅记住命令，还要理解其工作原理
4. **举一反三**: 掌握命令选项的组合使用
5. **记录笔记**: 整理学习心得和遇到的问题

### 实践环境
- **本地环境**: 在自己的Linux系统上练习
- **虚拟机**: 使用VirtualBox或VMware创建学习环境
- **在线平台**: 利用免费的在线Linux终端

## 📝 学习进度追踪

### 阶段1：基础入门
- [ ] 目录浏览和切换（ls, cd, pwd）
- [ ] 文件和目录操作（mkdir, touch, cp, mv, rm）
- [ ] 文件查看（cat, less, head, tail）

### 阶段2：文本处理
- [ ] 文本搜索（grep, find）
- [ ] 文本编辑（sed, awk）
- [ ] 文本处理（sort, uniq, wc）

### 阶段3：系统管理
- [ ] 进程管理（ps, top, kill, bg/fg）
- [ ] 系统监控（df, du, free, uptime）
- [ ] 权限管理（chmod, chown, sudo）
- [ ] 包管理（apt/yum/pacman）

### 阶段4：网络与高级应用
- [ ] 网络测试（ping, traceroute, nslookup）
- [ ] 文件传输（wget, curl, scp, rsync）
- [ ] 远程连接（ssh）
- [ ] 高级命令（history, alias, tar, 系统信息）

## 🛠️ 常用练习环境

### 在线平台
- [Linux命令行练习](https://cmdchallenge.com/)
- [OverTheWire Wargames](https://overthewire.org/)
- [WebLinux](https://www.weblinux.it/)

### 本地环境搭建
```bash
# Ubuntu/Debian
sudo apt update
sudo apt install vim tree htop curl wget

# CentOS/RHEL
sudo yum install vim tree htop curl wget
```

## 🛠️ 使用建议

### 查找命令
1. **日常使用**: 查看 [`commands/essentials/`](commands/essentials/) 目录
2. **功能查找**: 查看 [`commands/collections/`](commands/collections/) 目录
3. **深入学习**: 查看 [`guides/stages/`](guides/stages/) 目录
4. **快速参考**: 查看 [`commands/references/`](commands/references/) 目录

## 🤝 贡献指南

欢迎提交：
- 📝 学习经验和笔记
- 🔧 命令使用技巧
- 📚 学习资源推荐
- 🐛 文档纠错和改进

## 📄 许可证

本学习资料仅供学习使用，转载请注明出处。

## 🔗 相关链接

- **GitHub仓库**: [Derek7552/Linux-command](https://github.com/Derek7552/Linux-command)
- **在线学习**: 结合实际Linux环境练习

---

## 🎉 开始你的Linux学习之旅！

选择适合你的学习路径，逐步掌握Linux命令行的强大能力！

> 💡 **提示**: 学习Linux命令就像学习外语，需要大量的实践和应用。不要怕出错，多动手练习！
