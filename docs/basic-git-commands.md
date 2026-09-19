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

### 3. Inspect unstaged changes

```bash
git diff
```

### 4. Stage changes

Stage a specific file:

```bash
git add path/to/recipe.md
```

Example:

```bash
git add cocktails/negroni.md
```

Stage a directory:

```bash
git add docs/
```

Stage everything from the current directory downward:

```bash
git add .
```

Use `git add .` when everything shown by `git status` belongs in the same commit. Otherwise, stage specific files or directories.

### 5. Confirm what is staged

```bash
git status
```

### 6. Inspect exactly what will be committed

```bash
git diff --staged
```

If Git opens the diff in a pager and shows `(END)`, press:

```text
q
```

to return to the command prompt.

### 7. Commit the changes

```bash
git commit -m "Add Negroni recipe"
```

Use a short message describing what changed.

### 8. Push the commit to GitHub

```bash
git push
```

## Staging and Unstaging

### Unstage a file without deleting your changes

```bash
git restore --staged path/to/file
```

Example:

```bash
git restore --staged .DS_Store
```

This removes the file from the staging area but leaves the file itself unchanged.

### Discard an uncommitted change to a tracked file

```bash
git restore path/to/file.md
```

**Warning:** This discards the uncommitted edits in that file.

## Ignoring Files with `.gitignore`

Some local files should never be committed. On macOS, `.DS_Store` is a common example.

Create or add to `.gitignore`:

```bash
echo ".DS_Store" >> .gitignore
```

Then stage the `.gitignore` file:

```bash
git add .gitignore
```

Git will ignore future untracked `.DS_Store` files.

A useful starter `.gitignore` for this repository is:

```gitignore
.DS_Store
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

A more visual history:

```bash
git log --oneline --graph --decorate
```

### View branches

```bash
git branch
```

The branch marked with `*` is the current branch.

### Check whether local and GitHub are synchronized

```bash
git status -sb
```

If `main` and `origin/main` are synchronized, there will be no `ahead` or `behind` indicator.

## Mental Model

```text
Working Files  →  Staging Area  →  Local Git History  →  GitHub
                 git add           git commit            git push
```

For normal Marco's Kitchen updates:

```bash
git status
git diff

git add path/to/file.md

git status
git diff --staged

git commit -m "Describe the change"
git push
```

## Good Habits

- Run `git status` frequently.
- Use `git diff` before staging.
- Use `git diff --staged` before committing.
- Use `git add .` only when all current changes belong together.
- Keep commits focused on one logical change.
- Write commit messages that describe what changed.
- Use `.gitignore` for machine-specific or generated files that do not belong in the repository.
