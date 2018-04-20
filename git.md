## Git命令有如下:
1. git clone url 将你的github中的相关文件克隆到本地之中
2. git branch 查看分支信息
3. git checkout -b ljl 创建ljl分支
4. git checkout ljl 进入ljl分支
5. git branch -D ljl 删除ljl分支(注意,删除分支的时候不要在该分支中)
6. git status 查看状态
7. git add . 将所有改变的添加到索引（暂存区）
8. git commit -m '注解'  提交文件
9. giit push origin ljl 推送到ljl分支
10. git config --global user.name "jealous"
11. git config --global user.email "344887562@qq.com"
12. git commit -am '注解' 合并add和commit操作
13. ssh-keyge -t rsa -C 账号  创建密钥
14. 将users/administrator/.ssh中的id_rsa.pub中的值拷贝到github中
15. git diff master ljl  查看master和ljl的分支不同之处
16. git merge ljl 将ljl分支合并到当前的分支中
17. git tag -a 版本号 -m 注解  添加版本号
18. git push origin 版本号   推送版本号
19. git tag -d 版本号 删除版本号
20. git push origin --delete 版本号/tag 版本号  删除远程的版本号
21. git push origin --delete 分支 删除远程分支
22. git stash 添加缓存
23. git stash list 查看缓存
24. git stash apply stash@{n} 下载第n个缓存
25. git clone ssh的链接 
26. git stash clear 清除所有的缓存
27. git stash drop stash@{num} 删除num号缓存
28. git log 查看日志
29. git resert --hard 历史版本  恢复到历史版本

