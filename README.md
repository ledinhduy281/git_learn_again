# git_learn_again
I hope this is my last time learning this fucking git


## Basic things to know
- commits
- staging
- branches
- checking status and inspecting commits
- push and pull
- undoing and redoing changes
- merging and conflict resolution

## Commit
a set of saved repository changes. 

- A commit is never lost. 
- A commit has a hash key
- A commit is always a same

```git

D:\coding\git_learn\git_learn_again>echo Hello World > Dontreadme.md

D:\coding\git_learn\git_learn_again>git add .

D:\coding\git_learn\git_learn_again>git commit -m "Initial commit"
[main 2200b23] Initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 Dontreadme.md

D:\coding\git_learn\git_learn_again>git log
commit 2200b23a9c2452f223d12263b570afb0081a8254 (HEAD -> main)
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 16:27:49 2025 +0700

    Initial commit

commit d976cda36699ae72afa82a411f72835b53bba90e (origin/main, origin/HEAD)
Author: KTANE <49335381+ledinhduy281@users.noreply.github.com>
Date:   Sun Feb 23 15:56:30 2025 +0700

    Initial commit

```

`git add.` adds all the file changes to the staging area
`git commit` allows us to create a commit
`git log` gives us an overview of commits

## Staging

```git
D:\coding\git_learn\git_learn_again>echo staged > staged_file.txt

D:\coding\git_learn\git_learn_again>echo unstaged > unstaged.txt

D:\coding\git_learn\git_learn_again>git add staged_file.txt

D:\coding\git_learn\git_learn_again>git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   staged_file.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        unstaged.txt


D:\coding\git_learn\git_learn_again>git reset staged_file.txt

D:\coding\git_learn\git_learn_again>git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        staged_file.txt
        unstaged.txt

nothing added to commit but untracked files present (use "git add" to track)
```

`git add <filename>` adds one or more files to staging
`git reset <filename>` removes one or more files from staging
`git status` print repository status

## Branches

```
D:\coding\git_learn\git_learn_again>git branch
* main

D:\coding\git_learn\git_learn_again>git branch new_branch

D:\coding\git_learn\git_learn_again>git branch
* main
  new_branch

D:\coding\git_learn\git_learn_again>echo master branch > new_file_main.txt

D:\coding\git_learn\git_learn_again>git add .

D:\coding\git_learn\git_learn_again>git commit -m "Main branch commit"
[main ced495b] Main branch commit
 3 files changed, 3 insertions(+)
 create mode 100644 new_file_main.txt
 create mode 100644 staged_file.txt
 create mode 100644 unstaged.txt

D:\coding\git_learn\git_learn_again>git log
commit ced495b3253ce2981117f7d88fe1b44a60ec8fb9 (HEAD -> main)
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 16:44:30 2025 +0700

    Main branch commit

commit 2200b23a9c2452f223d12263b570afb0081a8254 (new_branch)
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 16:27:49 2025 +0700

    Initial commit

commit d976cda36699ae72afa82a411f72835b53bba90e (origin/main, origin/HEAD)
Author: KTANE <49335381+ledinhduy281@users.noreply.github.com>
Date:   Sun Feb 23 15:56:30 2025 +0700

    Initial commit

D:\coding\git_learn\git_learn_again>git checkout new_branch
Switched to branch 'new_branch'

D:\coding\git_learn\git_learn_again>echo new branch > new_file_new_branch.txt

D:\coding\git_learn\git_learn_again>git add .

D:\coding\git_learn\git_learn_again>git commit -m "new branch commit"
[new_branch 46645fa] new branch commit
 1 file changed, 1 insertion(+)
 create mode 100644 new_file_new_branch.txt

D:\coding\git_learn\git_learn_again>git log
commit 46645fa7e2630ee3e87bac315c0117375f653e1c (HEAD -> new_branch)
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 16:45:55 2025 +0700

    new branch commit

commit 2200b23a9c2452f223d12263b570afb0081a8254
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 16:27:49 2025 +0700

    Initial commit

commit d976cda36699ae72afa82a411f72835b53bba90e (origin/main, origin/HEAD)
Author: KTANE <49335381+ledinhduy281@users.noreply.github.com>
Date:   Sun Feb 23 15:56:30 2025 +0700

    Initial commit

D:\coding\git_learn\git_learn_again>git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)

```

`git branch` displays available branches
`git branch <branch name>` creates a new branch
`git checkout <branch name>` switches to a different branch

## Checking status and inspecting commits

```
D:\coding\git_learn\git_learn_again>git log
commit ced495b3253ce2981117f7d88fe1b44a60ec8fb9 (HEAD -> main)
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 16:44:30 2025 +0700

    Main branch commit

commit 2200b23a9c2452f223d12263b570afb0081a8254
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 16:27:49 2025 +0700

    Initial commit

commit d976cda36699ae72afa82a411f72835b53bba90e (origin/main, origin/HEAD)
Author: KTANE <49335381+ledinhduy281@users.noreply.github.com>
Date:   Sun Feb 23 15:56:30 2025 +0700

    Initial commit

D:\coding\git_learn\git_learn_again>git show ced495b3253ce2981117f7d88fe1b44a60ec8fb9 
commit ced495b3253ce2981117f7d88fe1b44a60ec8fb9 (HEAD -> main)
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 16:44:30 2025 +0700

    Main branch commit

diff --git a/new_file_main.txt b/new_file_main.txt
new file mode 100644
index 0000000..3b3ed16
--- /dev/null
+++ b/new_file_main.txt
@@ -0,0 +1 @@
+master branch 
diff --git a/staged_file.txt b/staged_file.txt
new file mode 100644
index 0000000..7553b0d
--- /dev/null
+++ b/staged_file.txt
@@ -0,0 +1 @@
+staged 
diff --git a/unstaged.txt b/unstaged.txt
new file mode 100644
index 0000000..961828c
--- /dev/null
+++ b/unstaged.txt
@@ -0,0 +1 @@
+unstaged 

D:\coding\git_learn\git_learn_again>git reflog
ced495b (HEAD -> main) HEAD@{0}: checkout: moving from new_branch to main
46645fa (new_branch) HEAD@{1}: commit: new branch commit
2200b23 HEAD@{2}: checkout: moving from main to new_branch
ced495b (HEAD -> main) HEAD@{3}: commit: Main branch commit
2200b23 HEAD@{4}: commit: Initial commit
d976cda (origin/main, origin/HEAD) HEAD@{5}: clone: from https://github.com/ledinhduy281/git_learn_again.git
```

`git show <hash>` gives extensive commit info
`git show --name-only <hash>` gives shorthand commit info
`git reflog` gives info about all commits on all branches

## Push and Pull

```git
D:\coding\git_learn\git_learn_again>git push
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (8/8), 626 bytes | 313.00 KiB/s, done.
Total 8 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/ledinhduy281/git_learn_again.git
   d976cda..ced495b  main -> main

D:\coding\git_learn\git_learn_again>cd ..

D:\coding\git_learn>git clone https://github.com/ledinhduy281/git_learn_again.git clone_git_again_to_learn_pull
Cloning into 'clone_git_again_to_learn_pull'...
remote: Enumerating objects: 11, done.
remote: Counting objects: 100% (11/11), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 11 (delta 1), reused 8 (delta 1), pack-reused 0 (from 0)
Receiving objects: 100% (11/11), done.
Resolving deltas: 100% (1/1), done.

D:\coding\git_learn>cd clone_git_again_to_learn_pull

D:\coding\git_learn\clone_git_again_to_learn_pull>echo test > test.txt

D:\coding\git_learn\clone_git_again_to_learn_pull>git add .

D:\coding\git_learn\clone_git_again_to_learn_pull>git commit -m "add test file"
[main 117c25f] add test file
 1 file changed, 1 insertion(+)
 create mode 100644 test.txt

D:\coding\git_learn\clone_git_again_to_learn_pull>git push
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 267 bytes | 267.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/ledinhduy281/git_learn_again.git
   ced495b..117c25f  main -> main

D:\coding\git_learn\clone_git_again_to_learn_pull>cd ../git_learn_again

D:\coding\git_learn\git_learn_again>git pull
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (1/1), done.
remote: Total 3 (delta 1), reused 3 (delta 1), pack-reused 0 (from 0)
Unpacking objects: 100% (3/3), 247 bytes | 20.00 KiB/s, done.
From https://github.com/ledinhduy281/git_learn_again
   ced495b..117c25f  main       -> origin/main
Updating ced495b..117c25f
Fast-forward
 test.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 test.txt
```

`git push` sends commits to central repository
`git pull` retrieves commits from central repository to the local project

## Undo and redo changes
```git
D:\coding\git_learn\git_learn_again>git log
commit 117c25f8745b7f70e981b81feaceb3619412ae01 (HEAD -> main, origin/main, origin/HEAD)
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 17:00:52 2025 +0700

    add test file

commit ced495b3253ce2981117f7d88fe1b44a60ec8fb9
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 16:44:30 2025 +0700

    Main branch commit

commit 2200b23a9c2452f223d12263b570afb0081a8254
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 16:27:49 2025 +0700

    Initial commit

commit d976cda36699ae72afa82a411f72835b53bba90e
Author: KTANE <49335381+ledinhduy281@users.noreply.github.com>
Date:   Sun Feb 23 15:56:30 2025 +0700

    Initial commit

D:\coding\git_learn\git_learn_again>git revert 117c25f8745b7f70e981b81feaceb3619412ae01

[main c334d22] Revert "add test file"
 1 file changed, 1 deletion(-)
 delete mode 100644 test.txt

D:\coding\git_learn\git_learn_again>git reset ced495b3253ce2981117f7d88fe1b44a60ec8fb9

D:\coding\git_learn\git_learn_again>git log
commit ced495b3253ce2981117f7d88fe1b44a60ec8fb9 (HEAD -> main)
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 16:44:30 2025 +0700

    Main branch commit

commit 2200b23a9c2452f223d12263b570afb0081a8254
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 16:27:49 2025 +0700

    Initial commit

commit d976cda36699ae72afa82a411f72835b53bba90e
Author: KTANE <49335381+ledinhduy281@users.noreply.github.com>
Date:   Sun Feb 23 15:56:30 2025 +0700

    Initial commit
```

`git revert` creates a new commit to undo changes
`git reset --soft` removes commits from history keeps changes
`git reset --hard` removes commits from history removes changes

## Merging branches

![[Pasted image 20250223172419.png]]

```git
D:\coding\git_learn\git_learn_again>git merge new_branch
Merge made by the 'ort' strategy.
 new_file_new_branch.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 new_file_new_branch.txt

D:\coding\git_learn\git_learn_again>git log
commit 327534615dee6b1faa7247ad1b688ef6ea24cf34 (HEAD -> main)
Merge: ced495b 46645fa
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 17:24:59 2025 +0700

    Merge branch 'new_branch'

commit 46645fa7e2630ee3e87bac315c0117375f653e1c (new_branch)
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 16:45:55 2025 +0700

    new branch commit

commit ced495b3253ce2981117f7d88fe1b44a60ec8fb9
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 16:44:30 2025 +0700

    Main branch commit

commit 2200b23a9c2452f223d12263b570afb0081a8254
Author: duy.le281 <duy.le281@hcmut.edu.vn>
Date:   Sun Feb 23 16:27:49 2025 +0700

    Initial commit

commit d976cda36699ae72afa82a411f72835b53bba90e
Author: KTANE <49335381+ledinhduy281@users.noreply.github.com>
Date:   Sun Feb 23 15:56:30 2025 +0700

    Initial commit

```

