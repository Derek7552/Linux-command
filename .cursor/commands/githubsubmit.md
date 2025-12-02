---
name: "GitHub 提交"
description: "一键完成 Git 添加、提交和推送操作"
author: "Derek7552"
tags: ["git", "github", "提交"]
command: |
  # 检查 Git 状态
  echo "📊 当前 Git 状态："
  git status --short

  echo ""
  echo "➕ 添加所有更改的文件..."
  git add .

  echo ""
  echo "💬 请输入提交信息："
  read -p "提交信息: " commit_message

  if [ -z "$commit_message" ]; then
    echo "❌ 提交信息不能为空"
    exit 1
  fi

  echo ""
  echo "✅ 提交更改..."
  git commit -m "$commit_message"

  echo ""
  echo "🚀 推送分支..."
  git push

  echo ""
  echo "🎉 提交完成！"
---

# GitHub 提交命令

## 功能说明

这个命令简化了 GitHub 仓库的提交流程，包含以下步骤：
1. 检查当前 Git 状态
2. 添加所有更改的文件到暂存区
3. 提交更改（支持交互式输入提交信息）
4. 推送到远程仓库

## 使用方法

在 Cursor 中运行此命令时，会执行以下操作：

```bash
# 检查状态
git status

# 添加所有更改
git add .

# 提交（需要输入提交信息）
git commit -m "您的提交信息"

# 推送
git push
```

## 适用场景

- 日常开发提交
- 文档更新提交
- 快速推送更改

## 注意事项

- 请确保已经配置好 Git 用户信息
- 建议在提交前检查更改内容
- 大型更改建议创建功能分支

## 相关命令

- `git status` - 查看当前状态
- `git log` - 查看提交历史
- `git branch` - 查看分支信息
