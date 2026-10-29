---
name: commit-push
description: 当用户要求"提交项目""commit""push""推送到 GitHub/Gitee"时使用。检查工作区状态、暂存全部改动、用中文写简洁的提交信息，并推送到指定远程仓库（GitHub 远程名 github，分支 master；Gitee 远程名 origin，分支 main）。
---

# 提交并推送本项目

把当前工作区的改动提交成一个 commit，并推送到远程仓库。

## 仓库信息

| 远程名 | 地址 | 默认分支 |
| --- | --- | --- |
| `github` | `ssh://git@ssh.github.com:443/sjsgbmyqj/hujiayu.git` | `master` |
| `origin` | `https://gitee.com/qiji66666/hujiayu2026.git` | `main` |

- 本机已配置 SSH 公钥，GitHub 走 443 端口通道，**不需要输入账号密码**。
- 未特别说明时，默认推送到 `github`（`master` 分支）。

## 工作流程

### 1. 查看状态

```powershell
git status --porcelain -uall
git remote -v
git log --oneline -3
```

确认改动文件符合预期；若发现不该提交的文件（密钥、node_modules、临时截图等），先写进 `.gitignore`。

### 2. 暂存改动

```powershell
git add -A
```

### 3. 提交

```powershell
git commit -m "<一句话中文提交信息>"
```

- 提交信息要说明**做了什么**，例如：`新增16-3 网易云音乐导航栏还原页，同步导航入口`。
- 用 `git diff --staged --stat` 复核后再提交，避免误提交临时文件。

### 4. 推送

```powershell
git push github master        # GitHub
git push origin main          # Gitee（按需）
```

首次推送或分支未关联时可加 `-u`：`git push -u github master`。

## 注意事项

- 推送前**不要修改 git config**（用户名、邮箱、远程地址都保持原样）。
- 只提交与作业相关的文件：HTML 页面、`hjy_prompt.md`、`index.html`、图片与字体资源。
- 若 push 提示鉴权失败，先确认 SSH 公钥已加入 GitHub 账号，再重试；不要改成 HTTPS 地址并要求用户输入密码。
- 提交后把结果（commit 摘要 + 推送的远程分支）简要汇报给用户。
