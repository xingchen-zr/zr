修改文件后可用  ==git  status==  查看文件状态![Pasted image 20260720144347](attachments/Pasted%20image%2020260720144347.png)
然后通过  ==git add 文件名==  提交文件到缓冲区
![Pasted image 20260720144432](attachments/Pasted%20image%2020260720144432.png)
最后通过  ==git commit  -m  备注==     将所有缓冲区文件提交到本地仓库
![Pasted image 20260720144546](attachments/Pasted%20image%2020260720144546.png)

如果文件误删除
	1.如果还未提交,则可通过  ==git  restore==  文件名恢复文件
	![Pasted image 20260720144737](attachments/Pasted%20image%2020260720144737.png)
	2.如果文件已经提交至本地仓库,则可通过  ==git  reset --hard  版本号==  恢复提交之前的各个版本(不建议用,可能导致数据缺失)
	![Pasted image 20260720144938](attachments/Pasted%20image%2020260720144938.png)
	==如果通过reser来恢复的话会丢失恢复版本之后的所有提交数据==
	3.如果不想丢失提交数据可以通过  ==gti revert 版本号==  来恢复数据,这样能够新增一个反向提交，不改变提交信息
	![Pasted image 20260720153418](attachments/Pasted%20image%2020260720153418.png)

4.创建分支  ==git branch 分支名==
![Pasted image 20260720154624](attachments/Pasted%20image%2020260720154624.png)
==**注意:**==创建分支前一定要有提交操作,也就是一定要有master分支,如果创建一个空文件夹后直接创建分支会无法创建
5.查看目前已有分支 ==git branch -v==       *  代表目前位于哪一个分支
![Pasted image 20260720154855](attachments/Pasted%20image%2020260720154855.png)
6.切换分支  ==git chenkout 分支名==
![Pasted image 20260720155030](attachments/Pasted%20image%2020260720155030.png)
		创建一个分支并切换  ==git checkout -b 分支名==
		![Pasted image 20260720155347](attachments/Pasted%20image%2020260720155347.png)
7.删除分支 ==git branch -d 分支名==
![Pasted image 20260720155505](attachments/Pasted%20image%2020260720155505.png)
8.合并分支 ==git merge 分支名==
![Pasted image 20260720181939](attachments/Pasted%20image%2020260720181939.png)
**文件冲突后需自己手动修改文件内容并提交保存**

![Pasted image 20260720182129](attachments/Pasted%20image%2020260720182129.png)
9.给提交的版本号打上一个标签==git tag 标签名 版本号==
![Pasted image 20260720182847](attachments/Pasted%20image%2020260720182847.png)
查询则是 ==git log 标签名==
10.删除标签 ==git tag -d 标签名==
![Pasted image 20260720183104](attachments/Pasted%20image%2020260720183104.png)
11.关于远程仓库的所有知识
![Pasted image 20260720184957](attachments/Pasted%20image%2020260720184957.png)
12.通过git命令行进行本地仓库的推送和拉取
![Pasted image 20260720204643](attachments/Pasted%20image%2020260720204643.png)
![Pasted image 20260720204700](attachments/Pasted%20image%2020260720204700.png)
