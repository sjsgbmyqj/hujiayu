---
name: commit-push-github
description: Commits all project changes and pushes to the GitHub remote sjsgbmyqj/hujiayu, adding the remote if needed. Use when the user asks to commit or push to GitHub, 提交到github, or 同步到 GitHub.
---

# Commit and Push to GitHub

Commit the current project and push it to the GitHub remote repository.

## Remote Repository

- SSH URL: `ssh://git@ssh.github.com:443/sjsgbmyqj/hujiayu.git`（公钥已配置；本机网络屏蔽 22 端口，必须走 ssh.github.com 的 443 端口 SSH 通道）
- Remote name: `github`
- Branch: `master`

## Workflow

### 1. Check Current State

```powershell
git status
git remote -v
```

### 2. Configure Remote

If the `github` remote is missing:

```powershell
git remote add github ssh://git@ssh.github.com:443/sjsgbmyqj/hujiayu.git
```

If it exists but points elsewhere:

```powershell
git remote set-url github ssh://git@ssh.github.com:443/sjsgbmyqj/hujiayu.git
```

### 3. Stage and Commit

```powershell
git add .
git commit -m "<中文提交信息>"
```

本环境 PowerShell 不支持 `&&`，链式命令使用 `;` 分隔。提交信息使用中文，简明描述变更内容（如 `新增15-1数7游戏页面`）。

### 4. Push

First push:

```powershell
git push -u github master
```

Subsequent pushes:

```powershell
git push github master
```

### 5. Handle Failures

- `Permission denied (publickey)`: SSH 公钥未加载，提示用户检查 `ssh-add` 与 `~/.ssh` 配置。
- 非快进推送失败时不要强推，先 `git pull --rebase github master` 解决冲突后再推。

## Notes

- `origin` 远程指向 Gitee，本技能只操作 `github` 远程，不影响 Gitee 推送。
- 推送前用 `git status` 确认变更，避免提交无关文件。
- 不要提交敏感文件（.env、凭据、token）。
