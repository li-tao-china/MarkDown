# 遇到的麻烦
- push到远程库
```
To ssh://git@localhost:*/user/project.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'ssh://git@localhost:*/user/project.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
**这是为什么呢？**  
>　　原因是，在你关联本地库和远程库以后，两者的文件是一致的，之后，你修改了本地库的文件，同时远程库的文件也被你修改了。当两者都有修改的时候，由push方（这里是本地库）来先做远程库和本地库的合并之后，再提交本地库的修改到远程库。因此需要在commit和push之间，做pull操作，即按以下步骤提交修改：
```
git add *
git commit -m 'change'
git pull
git push origin master
```
