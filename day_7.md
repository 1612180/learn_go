[Overview chat stranger app](https://github.com/1612180/chat_stranger_doc)

# Git Basics (ch2)

## Basic command

Init a repo inside existing directory
```
cd myrepo
git init
```

Nothing is tracked yet

Clone an Exisitng Repo
```
git clone <url>
git clone <url> name_bla
```

## Recording changes

Each file in directory has 2 stated:
- tracked (Git knows)
- untracked

tracked: __unmodified__, __modified__, __staged__

![lifeycle](https://git-scm.com/book/en/v2/images/lifecycle.png)

If you modify a file after you run `git add`, you have to run `git add` again to stage the latest version of the file:

Ignore file in `.gitignore`

What have you __changed__ but not yet __staged__?
```
git diff
```

If want to see what __staged__ so far => 
```
git diff --staged
```

Commit change
```
git commit
```

Remove file from directory and staging area
```
git rm <filename>
```

Next time `commit`, deleted file become __untracked__

Remove file only from staging area (not delete in disk)
```
git rm --cached <filename>
```

Move file
```
git mv <from> <to>
```

## Commit history

View history in reverse order (recent commit is first)
```
git log
```

View patch in each commit
```
git log -p -2
```

`-2` is for 2 recent commits

## Undo

### Uncommit

Commit too early and __mising__ some files, or mess up __commit msg__
=> make changes, __stage__(git add) , then 
```
git commit --amend
```

### Unstaging the __staged__ file

Image you have 2 files, and you want to commit theme __separately__ but accidentally stage 2 files (`git add *`). `git status` show what to do
```
git reset HEAD <file>...
```

### Unmodify the __modified__ file

File is modified but not __staged__

`git status` is saviour again
```
git checkout -- <file>...
```

## Remote

Get data from remote projects
```
git fetch <remote>
```

Automatically fetch and then merge that remote branch into your current branch
```
git pull
```

## Tag

List tag
```
git tag
```

2 type of tag:
- lightweight: pointer to specific commit
- annotated: full object

Create annotated tag
```
git tag -a v1.0 -m "my version 1.0"
```

Create lightweight tag
```
git tag v1.0-lw
```

Push tag to remote
```
# only 1 tag
git push origin v1.0

# all tags
git push origin --tags
```

Delete tag
```
git tag -d v1.0-lw
```