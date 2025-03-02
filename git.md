اد کردن گیت به پروژه

```
PS C:\Users\VIVAN\PycharmProjects\Git & Github> git init
Initialized empty Git repository in C:/Users/VIVAN/PycharmProjects/Git & Github/.git/
```
---
برای اینکه ببینیم هر فایل در چه وضعیتی است.
```
(pro) PS C:\Users\VIVAN\PycharmProjects\Git & Github> git status
On branch master
No commits yet
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .idea/
        git.md
        test1.py
nothing added to commit but untracked files present (use "git add" to track) 
```
---
برای اینکه فایل از مرحله working  به staging area
```
(pro) PS C:\Users\VIVAN\PycharmProjects\Git & Github> git add test1.py
```
برای انتقال همه فایل ها به staging area
```
(pro) PS C:\Users\VIVAN\PycharmProjects\Git & Github> git add .       

```
---
برای اینکه یک فایل را از staging area به working directory
```
(pro) PS C:\Users\VIVAN\PycharmProjects\Git & Github> git rm --cached test1.py
rm 'test1.py'
```
---
انتقال فایل به repo
``` 
(pro) PS C:\Users\VIVAN\PycharmProjects\Git & Github> git commit -m 'create new file test2.py'
[master 24afd1c] create new file test2.py
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.py

```
---