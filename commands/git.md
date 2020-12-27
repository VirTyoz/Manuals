# Git

Edit _.gitconfig_
```
git config --global --edit
git config --global user.name
git config --global user.email
```

Stash the changes
```
git stash
git stash apply
```

Clone large svn repository
```
git svn clone -r1:HEAD http://my-project.googlecode.com/svn/ --authors-file=users.txt --no-metadata -s my_project
git svn fetch -r1:HEAD --authors-file=users.txt
```

Interactively choose hunks of patch between the index and the work tree and add them to the index.
```
git add --patch
```

Author name and email
```
git config --global user.name "author_name"
git config --global user.email email_address
```

All repository settings
```
git config --list
```

Remove paths only from the index
```
git rm --cashed
```

Discard changes
```
git checkout -- file_name
```

Unstage
```
git reset HEAD file_name
```

Replace the tip of the current branch by creating a new commit
```
git commit --amend
```

Revert some existing commits
```
git revert commit_hash
```

Resets the index and working tree
```
git reset --hard commit_hash
```

Does not touch the index file or the working tree at all
```
git reset --soft commit_hash
```

Resets the index but not the working tree. Default
```
git reset --mixed commit_hash
```

Create a new branch
```
git checkout --branch branch_name
git branch branch_name
```

Stash the changes
```
git stash --save "massage_text"
```

Clone and auto checkout
```
git clone --branch
```

Сlone a specific branch
```
git clone --branch --single-branch
```
