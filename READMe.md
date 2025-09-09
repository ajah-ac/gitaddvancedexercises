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
# 1. Missing file fix
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
## 2.Editing commit history
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


## 3.squasing second file into intial file
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

# 4 Splitting a commit
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
 # 5. Advanced Squashing 
 ```bash
 YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git rebase -i HEAD~6
[detached HEAD a419d7d] Chore: create third and fourTH files
 Date: Fri Sep 5 16:10:21 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md
interactive rebase in progress; onto 4981fb0
Last commands done (4 commands done):
   pick 476f96c exercise 4
   pick 8644d8e chore: Create thiRD and fourTH files
  (see more in file .git/rebase-merge/done)
Next commands to do (14 remaining commands):
   pick 604ba43 chore:creating four file
   pick 7c3d8f5 exercise 1 & 2
  (use "git rebase --edit-todo" to view and edit)
You are currently rebasing branch 'master' on '4981fb0'.
  (all conflicts fixed: run "git rebase --continue")

nothing to commit, working tree clean
The previous cherry-pick is now empty, possibly due to conflict resolution.
If you wish to commit it anyway, use:

    git commit --allow-empty

Otherwise, please use 'git rebase --skip'
Could not apply 8644d8e... chore: Create thiRD and fourTH files

YOGA@AJAH MINGW64 ~/gitadvanced (master|REBASE 4/18)
$ git rebase --skip
interactive rebase in progress; onto 4981fb0
Last commands done (5 commands done):
   pick 8644d8e chore: Create thiRD and fourTH files
   pick 604ba43 chore:creating four file
  (see more in file .git/rebase-merge/done)
Next commands to do (13 remaining commands):
   pick 7c3d8f5 exercise 1 & 2
   pick a2d302f exercise 3
  (use "git rebase --edit-todo" to view and edit)
You are currently rebasing branch 'master' on '4981fb0'.
  (all conflicts fixed: run "git rebase --continue")

nothing to commit, working tree clean
The previous cherry-pick is now empty, possibly due to conflict resolution.
If you wish to commit it anyway, use:

    git commit --allow-empty

Otherwise, please use 'git rebase --skip'
Could not apply 604ba43... chore:creating four file

YOGA@AJAH MINGW64 ~/gitadvanced (master|REBASE 5/18)
$ git rebase --skip
Auto-merging READMe.md
CONFLICT (add/add): Merge conflict in READMe.md
error: could not apply 7c3d8f5...  exercise 1 & 2
hint: Resolve all conflicts manually, mark them as resolved with
hint: "git add/rm <conflicted_files>", then run "git rebase --continue".
hint: You can instead skip this commit: run "git rebase --skip".
hint: To abort and get back to the state before "git rebase", run "git rebase --abort".
hint: Disable this message with "git config advice.mergeConflict false"
Could not apply 7c3d8f5... exercise 1 & 2

YOGA@AJAH MINGW64 ~/gitadvanced (master|REBASE 6/18)
$ git add .

YOGA@AJAH MINGW64 ~/gitadvanced (master|REBASE 6/18)
$ git rebase --abort
 ```
 # 6. Dropping a commit 
 ``` bash 
 $ git add unwantedtext.md && git commit -m 'Unwanted commit'
[master 8fce026] Unwanted commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 unwantedtext.md
YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ $ git reset --hard HEAD~1
bash: $: command not found

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ $ git reset --hard HEAD~1
bash: $: command not found

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$  git reset --hard HEAD~1
HEAD is now at f3bada5 updating readme

<<<<<<< HEAD
YOGA@AJAH MINGW64 ~/gitadvanced (master)
```
# 7.Reordering commits
```bash
YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git log
commit 642981e545c63d70e60ca1fcc241e4779ebd3af1 (HEAD -> master)
Author: ajah <ajahajang00@gmail.com>
Date:   Fri Sep 5 14:41:26 2025 +0200

    chore:creating four file

commit 3b1cc20db8a91c601b6ba4e1d780d0592455ed29
Author: ajah <ajahajang00@gmail.com>
Date:   Mon Sep 8 15:37:24 2025 +0200

    updating readme

commit d99e3f9def451be0ea7c8be6a873bc88a7081bca
Author: ajah <ajahajang00@gmail.com>
Date:   Fri Sep 5 14:40:39 2025 +0200

    chore: Create third and fourth files

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git rebase -i HEAD~6
Successfully rebased and updated refs/heads/master.

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git log
commit 0b5a59718b8b932bcc28b6e4c2f665bfdce82a37 (HEAD -> master)
Author: ajah <ajahajang00@gmail.com>
Date:   Mon Sep 8 15:37:24 2025 +0200

    updating readme

commit 69b39ace6043b688bf357e74c680611a81454dca
Author: ajah <ajahajang00@gmail.com>
Date:   Fri Sep 5 14:41:26 2025 +0200

    chore:creating four file

commit d99e3f9def451be0ea7c8be6a873bc88a7081bca
Author: ajah <ajahajang00@gmail.com>
Date:   Fri Sep 5 14:40:39 2025 +0200

    chore: Create third and fourth files

```
# 8.Cherry picking commits
``` bash
YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git checkout -b ft/branch
Switched to a new branch 'ft/branch'
YOGA@AJAH MINGW64 ~/gitadvanced (ft/branch)
$ git add test5.md && git commit -m 'Implemented test 5'
[ft/branch fbed584] Implemented test 5
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test5.md
=======
YOGA@AJAH MINGW64 ~/gitadvanced (master) ```
>>>>>>> 614845a5b46981081374b5e2848db0bd73c07b0e
