# How to Initialize and Merge a Local Git Repository with GitHub (Windows)

Follow these steps to initialize a Git repository locally and merge it with your existing GitHub repository.

---

## 1. Install Git
- Download Git for Windows from [https://git-scm.com/download/win](https://git-scm.com/download/win)
- Install with default options.

---

## 2. Open PowerShell or Command Prompt
Navigate to your project folder:

```powershell
cd "C:\path\to\CommentCreator"
```

---

## 3. Initialize Git in the Folder

```bash
git init
```

This will create a local Git repository in the current folder.

---

## 4. Add Your GitHub Repository as a Remote

```bash
git remote add origin https://github.com/widgetech/CommentCreator.git
```

*(Skip this step if you cloned the repo previously.)*

---

## 5. Add and Commit Files

```bash
git add .
git commit -m "Initial commit with docs structure"
```

---

## 6. Pull and Merge Remote Repo

If your GitHub repository already has commits, pull and merge:

```bash
git pull origin main --allow-unrelated-histories
```

- If prompted, resolve any conflicts manually (VS Code or Git will highlight them).

---

## 7. Push to GitHub

```bash
git push origin main
```

Your local repository is now synced with the remote GitHub repo.

---

## Notes

- If your default branch is `master` instead of `main`, replace `main` with `master` in all commands.
- Use `git status` frequently to check which files are staged or need attention.
