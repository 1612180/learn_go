# Git Branching (ch3)

__commit__ trỏ đến __tree__, __tree__ chứa các __blob__, __blob__ trỏ đến file

![commit and tree](https://git-scm.com/book/en/v2/images/commit-and-tree.png)

__commit__ chứa __parent__ trỏ đến __commit__ ngay trước nó
![commit and parents](https://git-scm.com/book/en/v2/images/commits-and-parents.png)

Create a branch
```
git branch testing
```

`git branch` create a new branch but not switch to that branch

`HEAD` is pointer to current branch we are using

Switch branch
```
git checkout testing
```

__Quick__: Create a branch then switch
```
git branch -b testing2
```

Read [Basic branching and merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)

# Stranger chat app

[Activity diagram](https://github.com/1612180/chat_stranger_doc/tree/master/diagram/activity)

[Timeline](https://github.com/1612180/chat_stranger_doc/blob/master/timeline.md)