
---

## 🗂️ Git Interview Notes

### 1. **What is Git?**

* Distributed version control system for tracking changes in source code.
* Every developer has a full copy of the repo history.
* Enables collaboration, branching, merging, reverting, and code audits.

---

### 2. **Basic Commands**

```bash
git init                   # Initialize repo
git clone <url>            # Clone remote
git status                 # Show current state
git add <file>             # Stage changes
git commit -m "message"    # Commit changes
git push                   # Push to remote
git pull                   # Pull latest changes
```

---

### 3. **Merge vs Rebase**

| Merge                  | Rebase                     |
| ---------------------- | -------------------------- |
| Preserves full history | Rewrites history           |
| Creates a merge commit | Creates linear history     |
| Easier for teams       | Cleaner for solo workflows |

```bash
git merge branch-name
git rebase branch-name
```

> ⚠️ Use rebase for local changes; avoid rebasing shared/public branches.

---

### 4. **Reset Types**

```bash
git reset --soft HEAD~1   # Keep changes staged
git reset --mixed HEAD~1  # Unstage, keep changes
git reset --hard HEAD~1   # Discard all changes
```

---

### 5. **Reflog**

* Shows history of HEAD references.

```bash
git reflog
```

> Useful to recover commits even after reset/hard delete.

---

### 6. **Stash**

* Save dirty working directory temporarily.

```bash
git stash
git stash list
git stash apply    # Keep stash
git stash pop      # Apply and delete
```

---

### 7. **Cherry-pick**

* Apply a commit from another branch.

```bash
git cherry-pick <commit_hash>
```

---

### 8. **Tagging**

```bash
git tag v1.0
git push origin v1.0
```

> Used to mark versions/releases.

---

### 9. **GitHub: Key Concepts**

* **Fork vs Clone**: Fork = copy to your GitHub account.
* **Pull Request (PR)**: Propose code changes to a repo.
* **Actions**: CI/CD workflows.
* **Branch Protection Rules**: Prevent force-push or unauthorized merges.

---

### 10. **GitLab: Key Concepts**

* GitLab CI/CD with `.gitlab-ci.yml`
* Built-in runners, stages, jobs
* Merge requests (like GitHub PRs)
* Variables and Secrets in GitLab

---

### 11. **Advanced Git**

* **Squash Commits**

  ```bash
  git rebase -i HEAD~3
  ```
* **Bisect**

  * Used to find faulty commits via binary search.

  ```bash
  git bisect start
  ```

---

### 12. **Best Practices**

* Commit often, with meaningful messages.
* Use feature branches (`feature/login-form`)
* Avoid force push on shared branches.
* Rebase before merging to avoid conflicts.
* Use `.gitignore` to exclude temp/build files.

---

### 13. **Interview Questions**

* Difference between Git and SVN?
* How does Git handle merge conflicts?
* How to undo a commit? (Different strategies)
* Difference between tracking and remote branches?
* What is HEAD in Git?
* How do you roll back a production bug using Git?

---

