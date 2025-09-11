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
Successfully rebased and updated refs/heads/main.

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
YOGA@AJAH MINGW64 ~/gitadvanced (main)
$ touch unwanted.md

YOGA@AJAH MINGW64 ~/gitadvanced (main)
$  git add unwantedtext.md && git commit -m 'Unwanted commit'
fatal: pathspec 'unwantedtext.md' did not match any files

YOGA@AJAH MINGW64 ~/gitadvanced (main)
$  git add unwantedtext.txt && git commit -m 'Unwanted commit'
[main e33312e] Unwanted commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 unwantedtext.txt

YOGA@AJAH MINGW64 ~/gitadvanced (main)
$ git rebase -i HEAD~4
##locate commit and replace pick with drop
Successfully rebased and updated refs/heads/main.
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