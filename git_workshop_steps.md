git init
==
```
ramiro@walden:~/glitchLAB/git$ git init
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint: 	git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint: 	git branch -m <name>
Initialized empty Git repository in /home/ramiro/glitchLAB/git/.git/
```

Let's decolonialize git. Set the default branch name to `main`.
```
ramiro@walden:~/glitchLAB/git$ git config --global init.defaultBranch main
```

Rename our branch (we'll talk about branches later).
```
git branch -M master main
```

git status (empty)
==
```
ramiro@walden:~/glitchLAB/git$ git status
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

Edit file `README.md` in a text editor and save it to the directory.

git status (untracked file)
==
```
ramiro@walden:~/glitchLAB/git$ git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	README.md

nothing added to commit but untracked files present (use "git add" to track)
```

git add
==
```
ramiro@walden:~/glitchLAB/git$ git add README.md 
```

git status (staging area)
==
```
ramiro@walden:~/glitchLAB/git$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   README.md

```

git commit
==
```
ramiro@walden:~/glitchLAB/git$ git commit
Author identity unknown

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: empty ident name (for <ramiro@walden.local>) not allowed
```

Set user name and email.

```
testuser@walden:~/git$ git config --global user.email "ramiro.polla@gmail.com"
testuser@walden:~/git$ git config --global user.name "Ramiro Polla"
```

Try again.
```
ramiro@walden:~/glitchLAB/git$ git commit
```

The command-line editor (nano) opens.

```
first commit

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Committer: Ramiro Polla <ramiro@walden.local>
#
# On branch main
#
# Initial commit
#
# Changes to be committed:
#       new file:   README.md
#

```

Ctrl+O <Enter> Ctrl+X <Enter> to save and exit the editor

```
[main (root-commit) 55f1ce4] first commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
```

git log
==
```
ramiro@walden:~/glitchLAB/git$ git log
commit 55f1ce462e5dc981ce8b96b40fca253caab10c34 (HEAD -> main)
Author: Ramiro Polla <ramiro.polla@gmail.com>
Date:   Fri Apr 17 14:37:28 2026 +0200

    first commit
```

git show
==
```
ramiro@walden:~/glitchLAB/git$ git show
commit 55f1ce462e5dc981ce8b96b40fca253caab10c34 (HEAD -> main)
Author: Ramiro Polla <ramiro.polla@gmail.com>
Date:   Fri Apr 17 14:37:28 2026 +0200

    first commit

diff --git a/README.md b/README.md
new file mode 100644
index 0000000..16b14f5
--- /dev/null
+++ b/README.md
@@ -0,0 +1 @@
+test file
```

git status (modified)
==

```
ramiro@walden:~/glitchLAB/git$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

```
ramiro@walden:~/glitchLAB/git$ git diff
diff --git a/README.md b/README.md
index 16b14f5..252484c 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,3 @@
 test file
+addnig lines to the test file
+(one more line just to be sure)
```

```
ramiro@walden:~/glitchLAB/git$ git add README.md 
```

```
ramiro@walden:~/glitchLAB/git$ git commit -m "add more lines to README"
[main db3a587] add more lines to README
 1 file changed, 2 insertions(+)
```

```
ramiro@walden:~/glitchLAB/git$ git diff
diff --git a/README.md b/README.md
index 252484c..35fe901 100644
--- a/README.md
+++ b/README.md
@@ -1,3 +1,3 @@
 test file
-addnig lines to the test file
+adding lines to the test file
 (one more line just to be sure)
```

```
ramiro@walden:~/glitchLAB/git$ git add README.md
```

```
ramiro@walden:~/glitchLAB/git$ git commit -m "fix typo"
[main 74122fd] fix typo
 1 file changed, 1 insertion(+), 1 deletion(-)
ramiro@walden:~/glitchLAB/git$ git log
commit 74122fdbaba06436e4316f342cf42ffa3c20186a (HEAD -> main)
Author: Ramiro Polla <ramiro.polla@gmail.com>
Date:   Fri Apr 17 14:43:51 2026 +0200

    fix typo

commit db3a587ea6b113b11983ec57b291ac4a9e0b045d
Author: Ramiro Polla <ramiro.polla@gmail.com>
Date:   Fri Apr 17 14:43:16 2026 +0200

    add more lines to README

commit 55f1ce462e5dc981ce8b96b40fca253caab10c34
Author: Ramiro Polla <ramiro.polla@gmail.com>
Date:   Fri Apr 17 14:37:28 2026 +0200

    first commit
```

```
ramiro@walden:~/glitchLAB/git$ git log --pretty=oneline 
74122fdbaba06436e4316f342cf42ffa3c20186a (HEAD -> main) fix typo
db3a587ea6b113b11983ec57b291ac4a9e0b045d add more lines to README
55f1ce462e5dc981ce8b96b40fca253caab10c34 first commit
```

git show (with hash)
==

```
ramiro@walden:~/glitchLAB/git$ git show db3a587ea6b113b11983ec57b291ac4a9e0b045d
commit db3a587ea6b113b11983ec57b291ac4a9e0b045d
Author: Ramiro Polla <ramiro.polla@gmail.com>
Date:   Fri Apr 17 14:43:16 2026 +0200

    add more lines to README

diff --git a/README.md b/README.md
index 16b14f5..252484c 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,3 @@
 test file
+addnig lines to the test file
+(one more line just to be sure)
```

```
ramiro@walden:~/glitchLAB/git$ git show db3a587
commit db3a587ea6b113b11983ec57b291ac4a9e0b045d
Author: Ramiro Polla <ramiro.polla@gmail.com>
Date:   Fri Apr 17 14:43:16 2026 +0200

    add more lines to README

diff --git a/README.md b/README.md
index 16b14f5..252484c 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,3 @@
 test file
+addnig lines to the test file
+(one more line just to be sure)
```

git show (with hash^)
==

```
ramiro@walden:~/glitchLAB/git$ git show db3a587^
commit 55f1ce462e5dc981ce8b96b40fca253caab10c34
Author: Ramiro Polla <ramiro.polla@gmail.com>
Date:   Fri Apr 17 14:37:28 2026 +0200

    first commit

diff --git a/README.md b/README.md
new file mode 100644
index 0000000..16b14f5
--- /dev/null
+++ b/README.md
@@ -0,0 +1 @@
+test file
```

git show (with hash~n)
==
```
ramiro@walden:~/glitchLAB/git$ git show HEAD~2
commit 55f1ce462e5dc981ce8b96b40fca253caab10c34
Author: Ramiro Polla <ramiro.polla@gmail.com>
Date:   Fri Apr 17 14:37:28 2026 +0200

    first commit

diff --git a/README.md b/README.md
new file mode 100644
index 0000000..16b14f5
--- /dev/null
+++ b/README.md
@@ -0,0 +1 @@
+test file
```

```
ramiro@walden:~/glitchLAB/git$ mkdir split
ramiro@walden:~/glitchLAB/git$ cp README.md split/1.txt
ramiro@walden:~/glitchLAB/git$ cp README.md split/2.txt
ramiro@walden:~/glitchLAB/git$ cp README.md split/3.txt
ramiro@walden:~/glitchLAB/git$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	split/

nothing added to commit but untracked files present (use "git add" to track)
```

```
ramiro@walden:~/glitchLAB/git$ git add split/*
ramiro@walden:~/glitchLAB/git$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   split/1.txt
	new file:   split/2.txt
	new file:   split/3.txt

ramiro@walden:~/glitchLAB/git$ git commit -m "split into subdirectory"
[main 6958208] split into subdirectory
 3 files changed, 3 insertions(+)
 create mode 100644 split/1.txt
 create mode 100644 split/2.txt
 create mode 100644 split/3.txt
```

```
ramiro@walden:~/glitchLAB/git$ git rm README.md 
rm 'README.md'
ramiro@walden:~/glitchLAB/git$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	deleted:    README.md

ramiro@walden:~/glitchLAB/git$ git commit -m "remove README.md"
[main b0d0318] remove README.md
 1 file changed, 3 deletions(-)
 delete mode 100644 README.md
```
