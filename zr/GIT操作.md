修改文件后可用  git  status  查看文件状态![[Pasted image 20260720144347.png]]
然后通过  git add 文件名  提交文件到缓冲区
![[Pasted image 20260720144432.png]]
最后通过  git commit  -m  备注     将所有缓冲区文件提交到本地仓库
![[Pasted image 20260720144546.png]]

如果文件误删除
	1.如果还未提交,则可通过  git  restore  文件名恢复文件
	![[Pasted image 20260720144737.png]]
	2.如果文件已经提交至本地仓库,则可通过  git  reset --hard  版本号  恢复提交之前的各个版本
	![[Pasted image 20260720144938.png]]
	