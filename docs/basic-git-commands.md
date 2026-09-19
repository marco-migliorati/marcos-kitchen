# Basic Git CLI Commands

A simple cheat sheet for working with the Marco's Kitchen repository from Terminal.

## Core Workflow

The basic Git workflow is:

**Change → Inspect → Stage → Inspect → Commit → Push**

### 1. Go to the repository

```bash
cd ~/GitHub/marcos-kitchen
```

### 2. See what has changed

```bash
git status
```

### 3. Inspect the changes

```bash
git diff
```

### 4. Stage a specific file

```bash
git add path/to/recipe.md
```

Example:

```bash
git add cocktails/negroni.md
```

To stage all changes:

```bash
git add .
```

Using a specific filename is safer when you want precise control over a commit.

### 5. Confirm what is staged

```bash
git status
```

### 6. Inspect exactly what will be committed

```bash
git diff --staged
```

### 7. Commit the changes

```bash
git commit -m "Add Negroni recipe"
```

Use a short message describing what changed.

### 8. Push the commit to GitHub

```bash
git push
```

## Other Useful Commands

### Get the latest changes from GitHub

```bash
git pull
```

### View recent commit history

```bash
git log --oneline
```

### View branches

```bash
git branch
```

The branch marked with `*` is the current branch.

### Discard an uncommitted change to a tracked file

```bash
git restore path/to/file.md
```

**Warning:** `git restore` discards the uncommitted edits in that file.

## Mental Model

```text
Working Files  →  Staging Area  →  Local Git History  →  GitHub
                 git add           git commit            git push
```

For normal Marco's Kitchen updates, the sequence is:

```bash
git status
git diff
git add path/to/file.md
git status
git diff --staged
git commit -m "Describe the change"
git push
```
