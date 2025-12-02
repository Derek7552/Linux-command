# GitHub代码提交命令指南

## 🎯 快速推送命令

### 推送当前分支到GitHub
```bash
git push origin main
```

### 推送新创建的分支
```bash
git push -u origin feature/new-feature
```

### 强制推送（谨慎使用）
```bash
git push --force-with-lease origin main
```

## 📋 完整推送流程

### 1. 检查状态
```bash
git status
```

### 2. 添加文件
```bash
git add .                    # 添加所有更改
git add filename.md         # 添加特定文件
git add commands/           # 添加目录
```

### 3. 提交更改
```bash
git commit -m "feat: 添加新功能"
git commit -m "fix: 修复bug"
git commit -m "docs: 更新文档"
```

### 4. 推送代码
```bash
git push origin main
```

### 5. 创建Pull Request（可选）
1. 打开GitHub仓库: https://github.com/Derek7552/Linux-command
2. 点击"Compare & pull request"
3. 填写PR信息并提交

## 🚀 常用场景命令

### 推送功能分支
```bash
# 创建并切换到功能分支
git checkout -b feature/new-feature

# 开发代码后
git add .
git commit -m "feat: 实现新功能"

# 推送分支
git push -u origin feature/new-feature
```

### 紧急修复推送
```bash
# 创建热修复分支
git checkout -b hotfix/critical-fix

# 修复代码
git add .
git commit -m "fix: 紧急修复关键问题"

# 推送并合并
git push origin hotfix/critical-fix
```

### 同步远程更改
```bash
# 拉取最新代码
git pull origin main

# 如果有冲突，解决后推送
git add .
git commit -m "fix: 解决合并冲突"
git push origin main
```

## ⚙️ 项目特定配置

### 当前远程仓库
```bash
# 查看远程仓库
git remote -v
# origin	https://github.com/Derek7552/Linux-command.git (fetch)
# origin	https://github.com/Derek7552/Linux-command.git (push)
```

### 分支策略
- `main`: 主分支，受保护，只允许通过PR合并
- `feature/*`: 功能开发分支
- `bugfix/*`: 问题修复分支
- `hotfix/*`: 紧急修复分支

### 提交规范
遵循 [Conventional Commits](https://conventionalcommits.org/) 规范：
- `feat:` 新功能
- `fix:` 修复bug
- `docs:` 文档更新
- `style:` 代码格式
- `refactor:` 重构
- `test:` 测试
- `chore:` 构建/工具

## 🔧 问题解决

### 推送被拒绝
```bash
# 拉取最新代码
git pull origin main --rebase

# 或强制推送（谨慎）
git push --force-with-lease origin main
```

### 分支不存在远程
```bash
# 设置上游分支
git branch --set-upstream-to=origin/feature/branch-name

# 或推送并设置上游
git push -u origin feature/branch-name
```

### 认证失败
```bash
# 检查SSH密钥
ssh -T git@github.com

# 或使用个人访问令牌
git remote set-url origin https://YOUR_USERNAME:YOUR_TOKEN@github.com/Derek7552/Linux-command.git
```

## 📊 当前项目状态

### 远程分支状态
- **仓库**: Derek7552/Linux-command
- **主分支**: main (受保护)
- **活跃分支**: feature/linux-commands-update

### 最近提交
```
76bcd934 chore: 完成项目配置和文档更新
b20270e2 chore: 添加.gitignore文件
543bf71 docs: 添加GitHub代码提交指南到Cursor配置
```

## 🎯 快速操作

### 日常推送
```bash
git add .
git commit -m "feat: 你的更改描述"
git push origin main
```

### 分支开发
```bash
git checkout -b feature/new-feature
# 开发代码
git add .
git commit -m "feat: 实现新功能"
git push -u origin feature/new-feature
# 在GitHub创建PR
```

## ⚠️ 注意事项

1. **保护主分支**: 不要直接推送到main分支
2. **提交前检查**: 确保代码无误，运行测试
3. **清晰描述**: 提交信息要明确说明更改内容
4. **定期同步**: 开发前先拉取最新代码
5. **备份重要更改**: 大型重构前创建备份分支

## 📚 相关链接

- [GitHub文档](https://docs.github.com/)
- [Git工作流](https://guides.github.com/introduction/flow/)
- [Cursor Git集成](https://cursor.sh/docs/git)

---

*此指南为Linux-command项目的GitHub推送规范，适用于所有贡献者。请遵循这些规范确保代码质量和团队协作效率。*
