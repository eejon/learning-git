# Learning Git!

It's never too late to start!

---

### Making a New Repo

Starting out, we first create a directory for the project. The name of the directory should match the name of the repository created on your GitHub account (via the web UI).

```
mkdir myrepo
cd myrepo
git init
```

---

### Connecting to the Remote Repo

Before pushing any changes, we need to tell Git where the remote repository is:

```
git remote add origin <remote:git_url>
```

This command sets the remote location for your local Git repository. While `origin` is the conventional name, you can name it anything.

You can inspect this setup in `.git/config`:

```
[remote "origin"]
    url = https://github.com/you/repo1.git
[remote "backup"]
    url = https://gitlab.com/you/repo.git
```

The second remote (`backup`) was added with:

```
git remote add backup https://gitlab.com/you/repo.git
```

---

### Commit Your Changes

Once your Git repository is initialized, and you’ve made changes (e.g. added a file), you need to stage and commit them:

```
git add file          # or use git add . to track all changes
git commit -m "commit message"
```

Alternatively, to stage and commit modified (tracked) files in one command:

```
git commit -am "commit message"
```

---

### Pushing to the Remote Repository

Now that changes are committed, push them to the remote repository:

```
git push origin main
```

Explanation:

- `origin`: alias for the remote repository
- `main`: the branch you’re pushing

To make this the default tracking connection (upstream):

```
git push -u origin main
```

Now you can simply run `git push` or `git pull` without specifying `origin` and `main`.

---

### Branching

Branches are like snapshots of your code. The `main` branch is the default. When you want to make changes without affecting `main`, you create a new branch. This helps avoid conflicts and enables safe experimentation.

For example, to add a new feature:

- Create a branch from `main`
- Work on the new branch
- Push the branch to remote
- Check and resolve conflicts
- Merge it into `main` once it’s working

#### Creating and Switching to a Branch

```
git branch <branch_name>       # create the branch
git checkout <branch_name>     # switch to it
# or, in shorthand:
git checkout -b <branch_name>
```

Alternatively (with newer Git versions):

```
git switch -c <branch_name>    # create and switch
```

#### Keeping Main Up-to-Date

Before creating a new branch, ensure your local `main` is up-to-date:

```
git checkout main
git pull origin main
```

If you’ve set an upstream, a simple `git pull` is enough:

```
git pull
```

Now you can confidently create a new feature branch from the latest `main`.

---

Happy committing!
