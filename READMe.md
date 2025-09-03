# exercise number one
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