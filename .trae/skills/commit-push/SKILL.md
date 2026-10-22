---
name: commit-push
description: Commits all project changes and pushes to the Gitee remote, initializing git if needed. Use when the user asks to commit and push, 提交推送, or 同步到 Gitee.
---

# Commit and Push to Gitee

Commit the current project and push it to the Gitee remote repository.

## Remote Repository

- URL: `https://gitee.com/qiji66666/hujiayu2026.git`
- User: `qiji66666` / Email: `2075677138@qq.com`

## Workflow

### 1. Check Current State

```powershell
git status
git remote -v
```

If not a git repository, initialize:

```powershell
git init
git branch -M main
```

### 2. Configure Remote

```powershell
git remote add origin https://gitee.com/qiji66666/hujiayu2026.git
```

If the remote already exists, update it:

```powershell
git remote set-url origin https://gitee.com/qiji66666/hujiayu2026.git
```

### 3. Stage Changes

```powershell
git add .
```

If there are files that should not be committed (secrets, build artifacts), create or update `.gitignore` first.

### 4. Commit

```powershell
git commit -m "<descriptive commit message in Chinese>"
```

Use a clear, concise commit message describing the changes (e.g. `添加练习11-3：CSS3 3D旋转`).

### 5. Push

```powershell
git push -u origin main
```

For subsequent pushes:

```powershell
git push
```

### 6. Handle Authentication

On Windows, Git Credential Manager (GCM) should handle HTTPS authentication via a popup dialog. If credentials are not cached, the user will need to authenticate interactively. If push fails with `Authentication failed`, inform the user to check their Gitee credentials or use a Personal Access Token.

## Notes

- Always verify the remote URL before pushing to avoid pushing to the wrong repository.
- Use `git diff --staged` to review changes before committing.
- Do not commit sensitive files (`.env`, credentials, tokens).
