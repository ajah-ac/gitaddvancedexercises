# Initiliazing your environment and missing file fix
```bash YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git remote add origin https://github.com/ajah-ac/gitaddvancedexercises.git

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ touch test{1..4}.md
git add test1.md && git commit -m "chore: Create initial file"
git add test2.md && git commit -m "chore: Create another file"
git add test3.md && git commit -m "chore: Create third and fourth files"
[master (root-commit) e1b9a46] chore: Create initial file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
[master 6a35852] chore: Create another file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
[master c728a60] chore: Create third and fourth files
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
```
# Missing file fix
```bash

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        READMe.md
        test4.md

nothing added to commit but untracked files present (use "git add" to track)

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git log 


YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git add test4.md && git commit -m 'chore:creating four file'
[master 71c423a] chore:creating four file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.md
```
## exerice 2:
```bash 

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git rebase -i HEAD~3
Stopped at 6a35852...  chore: Create another file
You can amend the commit now, with
  git commit --amend
  Once you are satisfied with your changes, run
    git rebase --continue
YOGA@AJAH MINGW64 ~/gitadvanced (master|REBASE 1/3)
$ git commit --amend
[detached HEAD 25fc59b] chore: Create second file
 Date: Wed Sep 3 15:40:36 2025 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md

 YOGA@AJAH MINGW64 ~/gitadvanced (master|REBASE 1/3)
$ git rebase --continue
Successfully rebased and updated refs/heads/master.
```


## exercise 3 squasing second file into intial file
```bash YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git rebase -i HEAD~4
[detached HEAD c23aba9] chore:CReat initial and second file
 Date: Fri Sep 5 14:40:38 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/master.

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git rebase --continue
fatal: no rebase in progress

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git log
commit ec90e093f4ef832c03d872e0dbb9cc71b84d7f17 (HEAD -> master)
Author: ajah <ajahajang00@gmail.com>
Date:   Fri Sep 5 14:41:26 2025 +0200

    chore:creating four file

commit 2f1f5ca5f161ebfd0f7bcd3107882873f8aec21c
Author: ajah <ajahajang00@gmail.com>
Date:   Fri Sep 5 14:40:39 2025 +0200

    chore: Create third and fourth files

commit c23aba925008be821eea568cd509483aab142f7f
Author: ajah <ajahajang00@gmail.com>
Date:   Fri Sep 5 14:40:38 2025 +0200

    chore:CReat initial and second file
:
commit ec90e093f4ef832c03d872e0dbb9cc71b84d7f17 (HEAD -> master)
Author: ajah <ajahajang00@gmail.com>
Date:   Fri Sep 5 14:41:26 2025 +0200

    chore:creating four file

commit 2f1f5ca5f161ebfd0f7bcd3107882873f8aec21c
Author: ajah <ajahajang00@gmail.com>
Date:   Fri Sep 5 14:40:39 2025 +0200

    chore: Create third and fourth files

commit c23aba925008be821eea568cd509483aab142f7f
Author: ajah <ajahajang00@gmail.com>
Date:   Fri Sep 5 14:40:38 2025 +0200

    chore:CReat initial and second file
:
```

# exercise 4
```bash YOGA@AJAH MINGW64 ~/gitadvanced (master)
YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git rebase -i HEAD~6
Stopped at eed36e2...  chore: Create third and fourth files
You can amend the commit now, with

  git commit --amend

Once you are satisfied with your changes, run

  git rebase --continue

YOGA@AJAH MINGW64 ~/gitadvanced (master|REBASE 6/6)
$ git edit HEAD^
git: 'edit' is not a git command. See 'git --help'.

The most similar command is
        init

YOGA@AJAH MINGW64 ~/gitadvanced (master|REBASE 6/6)
$ git reset HEAD^

YOGA@AJAH MINGW64 ~/gitadvanced (master|REBASE 6/6)
$ git add test3.md && git commit -m 'Chore: create third file'
[detached HEAD 44b1b9a] Chore: create third file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md

YOGA@AJAH MINGW64 ~/gitadvanced (master|REBASE 6/6)
$ git add test4.md && git commit -m 'Chore: create four file'
[detached HEAD 72c4b05] Chore: create four file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.md

YOGA@AJAH MINGW64 ~/gitadvanced (master|REBASE 6/6)
$ git rebase --continue
Successfully rebased and updated refs/heads/master.

YOGA@AJAH MINGW64 ~/gitadvanced (master)
 ```