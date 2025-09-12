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
# Check status to check for missing files
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        READMe.md
        test4.md

nothing added to commit but untracked files present (use "git add" to track)

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git log 

# stage the file and commit it
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
$ git rebase -i HEAD~4
Stopped at 713e3f7...  chore : create third and forth file
You can amend the commit now, with

  git commit --amend

Once you are satisfied with your changes, run

  git rebase --continue

YOGA@AJAH MINGW64 ~/gitadvanced (master|REBASE 4/4)
$ git reset HEAD^

YOGA@AJAH MINGW64 ~/gitadvanced (master|REBASE 4/4)
$ git add test3.md && git commit -m 'Chore create third file'
[detached HEAD 7b03596] Chore create third file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md

YOGA@AJAH MINGW64 ~/gitadvanced (master|REBASE 4/4)
$ git add test4.md && git commit -m 'Chore create fourth file'
[detached HEAD 77af228] Chore create fourth file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.md

YOGA@AJAH MINGW64 ~/gitadvanced (master|REBASE 4/4)
$ git rebase --continue
Successfully rebased and updated refs/heads/master.

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
Next commands to do (14 remastering commands):
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
Next commands to do (13 remastering commands):
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
YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ touch unwanted.md

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$  git add unwantedtext.md && git commit -m 'Unwanted commit'
fatal: pathspec 'unwantedtext.md' did not match any files

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$  git add unwantedtext.txt && git commit -m 'Unwanted commit'
[master e33312e] Unwanted commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 unwantedtext.txt

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git rebase -i HEAD~4
##locate commit and replace pick with drop
Successfully rebased and updated refs/heads/master.
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
YOGA@AJAH MINGW64 ~/gitadvanced (ft/branch)
$  git cherry-pick -e 7ae5d86
On branch ft/branch
You are currently cherry-picking commit 7ae5d86.
  (all conflicts fixed: run "git cherry-pick --continue")
  (use "git cherry-pick --skip" to skip this patch)
  (use "git cherry-pick --abort" to cancel the cherry-pick operation)

nothing to commit, working tree clean
The previous cherry-pick is now empty, possibly due to conflict resolution.
If you wish to commit it anyway, use:

    git commit --allow-empty

Otherwise, please use 'git cherry-pick --skip'

YOGA@AJAH MINGW64 ~/gitadvanced (ft/branch|CHERRY-PICKING)
$ git commit --allow-empty
[ft/branch 0471b40] Implemented  test 5-cherrypicked
 Date: Tue Sep 9 10:34:28 2025 +0200
```
# 9.Visualizing Commit History (Bonus):

```bash 
YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git log --graph
*   commit 122b59d63d2465d6c066b6614b1e616bda424a9b (HEAD -> master, origin/master)
|\  Merge: 7107b05 614845a
| | Author: ajah <ajahajang00@gmail.com>
| | Date:   Tue Sep 9 10:41:05 2025 +0200
| |
| |     Merge branch 'master' of https://github.com/ajah-ac/gitaddvancedexercises
| |
| * commit 614845a5b46981081374b5e2848db0bd73c07b0e
| | Author: ajah <ajahajang00@gmail.com>
| | Date:   Mon Sep 8 16:11:17 2025 +0200
| | 
| |      updating readme
| |
| * commit f3bada55268f7cbbf8e16473af4b238dd74d95a3
| | Author: ajah <ajahajang00@gmail.com>
| | Date:   Mon Sep 8 15:37:24 2025 +0200
| |
:
*   commit 122b59d63d2465d6c066b6614b1e616bda424a9b (HEAD -> master, origin/master)
|\  Merge: 7107b05 614845a
| | Author: ajah <ajahajang00@gmail.com>
| | Date:   Tue Sep 9 10:41:05 2025 +0200
| |
| |     Merge branch 'master' of https://github.com/ajah-ac/gitaddvancedexercises
| |
| * commit 614845a5b46981081374b5e2848db0bd73c07b0e
| | Author: ajah <ajahajang00@gmail.com>
| | Date:   Mon Sep 8 16:11:17 2025 +0200
| |
| |      updating readme
| |
| * commit f3bada55268f7cbbf8e16473af4b238dd74d95a3
| | Author: ajah <ajahajang00@gmail.com>
| | Date:   Mon Sep 8 15:37:24 2025 +0200
| |
```
# 10.Understanding Reflogs (Bonus):
``` bash
YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git reflog
122b59d (HEAD -> master, origin/master) HEAD@{0}: checkout: moving from ft/branch to master
0471b40 (ft/branch) HEAD@{1}: commit (cherry-pick): Implemented test 5-cherrypicked
7ae5d86 HEAD@{2}: commit (cherry-pick): Implemented test 5
f7980c5 HEAD@{3}: reset: moving to f7980c50efc07033bf23da20a99a31059e77fe6a
f7980c5 HEAD@{4}: reset: moving to f7980c50efc07033bf23da20a99a31059e77fe6a
f7980c5 HEAD@{5}: reset: moving to f7980c50efc07033bf23da20a99a31059e77fe6a
f7980c5 HEAD@{6}: checkout: moving from master to ft/branch
122b59d (HEAD -> master, origin/master) HEAD@{7}: checkout: moving from ft/branch to master
f7980c5 HEAD@{8}: commit: updating readme
637bfa1 HEAD@{9}: commit: updating readme
fbed584 HEAD@{10}: reset: moving to fbed584e1c4a7f3a187e7d36108cfff66e665d59
fbed584 HEAD@{11}: checkout: moving from master to ft/branch
122b59d (HEAD -> master, origin/master) HEAD@{12}: commit (merge): Merge branch 'master' of https://github.com/ajah-ac/gitaddvancedexercises
7107b05 HEAD@{13}: commit: Updating Readme
0b5a597 HEAD@{14}: checkout: moving from ft/branch to master
fbed584 HEAD@{15}: reset: moving to fbed584e1c4a7f3a187e7d36108cfff66e665d59
fbed584 HEAD@{16}: commit: Implemented test 5

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git checkout HEAD@{3}
Note: switching to 'HEAD@{3}'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at f7980c5 updating readme

YOGA@AJAH MINGW64 ~/gitadvanced ((f7980c5...))
$
```
## Part 2
# 1.Feature Branch Creation:
```bash
YOGA@AJAH MINGW64 ~/gitadvanced ((f7980c5...))
$ git checkout -b 'ft/new-feature'
Switched to a new branch 'ft/new-feature'
```
# 2.Working on the Feature Branch:
```bash
YOGA@AJAH MINGW64 ~/gitadvanced (ft/new-feature)
$ git add feature.txt && git commit -m 'Implemented core functionality for new feature'
[ft/new-feature 74378c4] Implemented core functionality for new feature
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 feature.txt

YOGA@AJAH MINGW64 ~/gitadvanced (ft/new-feature)
$
```
# 3.Switching Back and Making More Changes:
```bash
YOGA@AJAH MINGW64 ~/gitadvanced (ft/new-feature)
$ git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git add readme.txt && git commit -m 'Updating project readme'
[master 301ab84] Updating project readme
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 readme.txt
```
# 4.Local vs. Remote Branches:
```bash
<<<<<<< HEAD
=======

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git remote -v
origin  https://github.com/ajah-ac/gitaddvancedexercises.git (fetch)
origin  https://github.com/ajah-ac/gitaddvancedexercises.git (push)

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git branch -r
  origin/master

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git branch -a
  ft/branch
  ft/new-feature
* master
  my-temp-branch
  remotes/origin/master

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git push -u origin ft/new-feature
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 10 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 1.87 KiB | 639.00 KiB/s, done.
Total 5 (delta 3), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (3/3), completed with 2 local objects.
remote:
remote: Create a pull request for 'ft/new-feature' on GitHub by visiting:
remote:      https://github.com/ajah-ac/gitaddvancedexercises/pull/new/ft/new-feature
remote:
To https://github.com/ajah-ac/gitaddvancedexercises.git
 * [new branch]      ft/new-feature -> ft/new-feature
branch 'ft/new-feature' set up to track 'origin/ft/new-feature'.

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git pull
Already up to date.

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git fetch

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git pull
Already up to date.
```
# 5.Branch deletion
```bash

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git branch -d ft/new-feature
warning: deleting branch 'ft/new-feature' that has been merged to
         'refs/remotes/origin/ft/new-feature', but not yet merged to HEAD
Deleted branch ft/new-feature (was 01a3b21).

YOGA@AJAH MINGW64 ~/gitadvanced (master)
$
```
# 6.Creating a branch from a commit

```bash
YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git log --oneline
87e9e00 (HEAD -> master) Updating readme
4a6867e (origin/master) Updating readme
301ab84 Updating project readme
57aaf64 Updating readme
122b59d Merge branch 'master' of https://github.com/ajah-ac/gitaddvancedexercises
7107b05 Updating Readme
0b5a597 updating readme
69b39ac chore:creating four file
d99e3f9 chore: Create third and fourth files
8d3b1da chore:CReat initial and second file
c104f99 exercise 3
18b0f94 chore:creating four file
8a468a4 chore: Create third and fourth files
4463f14 exercise 3
614845a  updating readme
f3bada5 updating readme
65cd9d2 unwanted text
YOGA@AJAH MINGW64 ~/gitadvanced (master)
$ git checkout -b ft/new-branch-from-commit 57aaf64
Switched to a new branch 'ft/new-branch-from-commit'

YOGA@AJAH MINGW64 ~/gitadvanced (ft/new-branch-from-commit)
$ git log --oneline
57aaf64 (HEAD -> ft/new-branch-from-commit) Updating readme
122b59d Merge branch 'master' of https://github.com/ajah-ac/gitaddvancedexercises
7107b05 Updating Readme
0b5a597 updating readme
69b39ac chore:creating four file
d99e3f9 chore: Create third and fourth files
8d3b1da chore:CReat initial and second file
c104f99 exercise 3
18b0f94 chore:creating four file
8a468a4 chore: Create third and fourth files
4463f14 exercise 3
614845a  updating readme
f3bada5 updating readme
65cd9d2 unwanted text
0924bb2 exercise 4
476f96c exercise 4
72c4b05 Chore: create four file
```
# 7. Branch merging
```bash
YOGA@AJAH MINGW64 ~/gitadvanced (ft/new-branch-from-commit)
$ git checkout main
Already on 'main'
Your branch is up to date with 'origin/main'.

YOGA@AJAH MINGW64 ~/gitadvanced (main)
$ git merge ft/new-branch-from-commit
Already up to date.

YOGA@AJAH MINGW64 ~/gitadvanced (main)
$ git log --oneline --graph --all
* 87e9e00 (HEAD -> main, origin/main) Updating readme
* 4a6867e (origin/master) Updating readme
* 301ab84 Updating project readme
* 57aaf64 (ft/new-branch-from-commit) Updating readme
*   122b59d Merge branch 'master' of https://github.com/ajah-ac/gitaddvancedexercises
|\
| * 614845a  updating readme
* | 7107b05 Updating Readme
| | * 01a3b21 (origin/ft/new-feature) Updating readme
| | * 74378c4 Implemented core functionality for new feature
| | | * 0471b40 (origin/ft/branch, ft/branch) Implemented  test 5-cherrypicked
| | | * 7ae5d86 Implemented test 5
| | |/
| | * f7980c5 updating readme
| | * 637bfa1 updating readme
| | * fbed584 Implemented test 5
| |/

YOGA@AJAH MINGW64 ~/gitadvanced (main)
$ git push origin main
Everything up-to-date

YOGA@AJAH MINGW64 ~/gitadvanced (main)
```
# 8. Branch rebasing
``` bash
YOGA@AJAH MINGW64 ~/gitadvanced (main)
$ git checkout ft/new-branch-from-commit
Switched to branch 'ft/new-branch-from-commit'

YOGA@AJAH MINGW64 ~/gitadvanced (ft/new-branch-from-commit)
$ git fetch origin main
From https://github.com/ajah-ac/gitaddvancedexercises
 * branch            main       -> FETCH_HEAD

YOGA@AJAH MINGW64 ~/gitadvanced (ft/new-branch-from-commit)
$ git rebase origin/main
Successfully rebased and updated refs/heads/ft/new-branch-from-commit.

YOGA@AJAH MINGW64 ~/gitadvanced (ft/new-branch-from-commit)
$ git add .
```
# 9. Renaming branches
```bash 
YOGA@AJAH MINGW64 ~/gitadvanced (ft/new-branch-from-commit)
$ git branch -m ft/new-branch-from-commit ft/improved-branch-name 

YOGA@AJAH MINGW64 ~/gitadvanced (ft/improved-branch-name)
$ git push -u origin ft/improved-branch-name
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
remote: 
remote: Create a pull request for 'ft/improved-branch-name' on GitHub by visiting:
remote:      https://github.com/ajah-ac/gitaddvancedexercises/pull/new/ft/improved-branch-name
remote:
To https://github.com/ajah-ac/gitaddvancedexercises.git
 * [new branch]      ft/improved-branch-name -> ft/improved-branch-name
branch 'ft/improved-branch-name' set up to track 'origin/ft/improved-branch-name'.
```
# 10.Checking Out Detached HEAD:
```bash
YOGA@AJAH MINGW64 ~/gitadvanced (ft/improved-branch-name)
$ git checkout 056e46a
Note: switching to '056e46a'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 056e46a Updating readme

YOGA@AJAH MINGW64 ~/gitadvanced ((056e46a...))
```
# Part 3:Advanced Workflows
# 1.Stashing changes:Stashing current changes in main using git stash
```bash



