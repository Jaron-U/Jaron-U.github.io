---
title: 'Removing large commits from git'
date: 2024-07-27
permalink: /posts/git-remove-file/
tags:
  - git

---

## Removing large commits from git

**Accidentally committed the trained weights file, but was REJECTED when trying to push it due to git not allowing commits over 100MB. Since the commit has already been made, removing the file from the cache directly won't fix the problem.**

I tried searching but many solutions are very troublesome, even ChatGPT told me to download the GBF tool.

I found a very simple solution here. But this method has some limitations, it only works for the most recent commit.

```bash
# first using soft reset to remove the last commit
git reset --soft HEAD~1

# then remove the file from the cache
git rm --cached path/to/file

# then commit again
git commit -m "commit message"

# finally push
git push
```

After that, the file will be removed from the commit and the commit will be pushed successfully.