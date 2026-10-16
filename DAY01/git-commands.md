# Git Commands — Complete Guide

## 1. `git init`

Definition: Initializes a new Git repository in the current directory.

Syntax:

bash
```
git init
git init <directory-name>
```

Example:

bash
```
mkdir my-project
cd my-project
git init
```

Use case:

- Start version control for a new project.
- Track changes in an existing project.

Interview explanation: `git init` creates the `.git` directory and initializes repository metadata. It does not automatically upload files to GitHub.

## 2. `git clone`

Definition: Creates a local copy of an existing repository, including its commit history.

Syntax:

bash
```
git clone <repository-url>
```

Example:

bash
```
git clone https://github.com/username/project.git
```

Use case:

- Download a project from GitHub.
- Start contributing to a team project.

Interview explanation: `git clone` copies an existing repository and normally configures its remote as `origin`. Unlike `git init`, it starts with an existing repository.

## 3. `git log`

Definition: Displays the commit history of a repository.

Syntax:

bash
```
git log [options]
```

Examples:

bash
```
git log
git log --oneline
git log --all --graph --oneline
git log -n 5
```

Use case:

- Investigate bugs.
- Review previous changes.
- Find commit IDs.

Interview explanation: `git log` displays commit metadata and history. `--oneline` gives a compact view, while `--all --graph` helps visualize branch history.

## 4. `git status`

Definition: Shows the state of the working directory and staging area.

Syntax:

bash
```
git status
git status --short
```

Example:

bash
```
git status
```

Use case:

- Check modified and untracked files.
- Confirm which changes are staged.
- Check whether the working tree is clean.

Interview explanation: `git status` tells me which changes are staged, unstaged, or untracked. I use it before and after important Git operations.

## 5. `git add`

Definition: Stages changes for the next commit.

Syntax:

bash
```
git add <file-name>
git add .
git add -A
```

Examples:

bash
```
git add app.py
git add .
git add -A
```

Use case:

- Select changes for a commit.
- Stage multiple files together.

Interview explanation: `git add` updates the staging area; it does not create a commit. `git add -A` stages additions, modifications, and deletions throughout the working tree.

## 6. `git commit`

Definition: Records staged changes as a commit in the local repository.

Syntax:

bash
```
git commit -m "commit message"
```

Example:

bash
```
git add app.py
git commit -m "Add login feature"
```

Use case:

- Save a logical unit of work.
- Maintain a meaningful project history.

Interview explanation: A commit records a snapshot of staged changes and metadata. It remains local until pushed to a remote repository.

## 7. `git push`

Definition: Uploads local commits to a remote repository.

Syntax:

bash
```
git push <remote> <branch>
```

Examples:

bash
```
git push origin main
git push -u origin feature-login
```

Use case:

- Share work on GitHub.
- Update a remote branch.
- Publish committed changes.

Interview explanation: `git push` sends local commits to a remote branch. It can be rejected if the remote contains incompatible new commits or you lack permission.

## 8. `git reset`

Definition: Moves the current branch reference and optionally updates the staging area and working directory.

Syntax:

bash
```
git reset [--soft | --mixed | --hard] <commit>
git reset <file-name>
```

Examples:

bash
```
# Keep changes staged
git reset --soft HEAD~1

# Keep changes but unstage them
git reset --mixed HEAD~1

# Reset tracked files and discard affected changes
git reset --hard HEAD~1

# Unstage a file
git reset app.py
```

Use case:

- Unstage files.
- Revise local commit history.
- Remove a local commit while retaining its changes.

Interview explanation: `--soft` keeps changes staged, `--mixed` keeps changes in the working directory but unstaged, and `--hard` resets tracked files and the index to the target commit. Hard reset can discard work, so use it cautiously.

## 9. `git revert`

Definition: Creates a new commit that reverses the changes introduced by an earlier commit.

Syntax:

bash
```
git revert <commit-hash>
```

Examples:

bash
```
git revert HEAD
git revert a1b2c3d
```

Use case:

- Reverse a buggy change.
- Undo a commit in a shared branch.
- Preserve an auditable history.

Interview explanation: Unlike reset, revert does not normally remove the old commit from history. It creates a new commit that undoes its changes.

## 10. `git clean`

Definition: Removes untracked files and, with options, directories and ignored files.

Syntax:

bash
```
git clean -n
git clean -f
git clean -fd
git clean -fdX
git clean -fdx
```

Examples:

bash
```
# Preview untracked files
git clean -n

# Preview untracked files and directories
git clean -nd

# Delete untracked files and directories
git clean -fd
```

Use case:

- Remove temporary files.
- Clean generated artifacts.
- Prepare a workspace for a fresh build.

Interview explanation: `git clean` targets untracked files, whereas `git reset --hard` resets tracked changes. Preview with `git clean -nd` before deleting anything.

Warning: `git clean -fdx` also removes ignored files. Check carefully before running it.

## 11. `git merge`

Definition: Integrates changes from another branch into the current branch.

Syntax:

bash
```
git merge <branch-name>
```

Examples:

bash
```
git switch main
git merge feature-login
```

To force a merge commit when a fast-forward is possible:

bash
```
git merge --no-ff feature-login
```

Use case:

- Integrate a feature branch into `main`.
- Combine work from multiple developers.
- Incorporate changes from another branch.

Interview explanation: Git may perform a fast-forward merge or create a merge commit. Conflicts must be resolved before completing the merge.

To cancel an in-progress merge:

bash
```
git merge --abort
```

## Common Git Workflow

bash
```
# Check changes
git status

# Stage changes
git add .

# Commit changes locally
git commit -m "Describe the change"

# Upload commits to GitHub
git push origin main
```

## Quick Interview Revision

| Command | Main purpose |
| --- | --- |
| `git init` | Initialize a repository |
| `git clone` | Copy an existing repository |
| `git log` | View commit history |
| `git status` | Check repository state |
| `git add` | Stage changes |
| `git commit` | Save a local commit |
| `git push` | Upload commits |
| `git reset` | Move branch pointer or unstage changes |
| `git revert` | Reverse changes with a new commit |
| `git clean` | Remove untracked files |
| `git merge` | Integrate another branch |

## Upload the file to GitHub

Save the content as `git-commands-guide.md`, then run:

bash
```
git add git-commands-guide.md
git commit -m "Add Git commands interview guide"
git push origin main
```
