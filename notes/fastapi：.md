例子：
![Pasted image 20260709134153](attachments/Pasted%20image%2020260709134153.png)
![Pasted image 20260709134506](attachments/Pasted%20image%2020260709134506.png)
![Pasted image 20260709134839](attachments/Pasted%20image%2020260709134839.png)
![Pasted image 20260709135222](attachments/Pasted%20image%2020260709135222.png)
![Pasted image 20260709135617](attachments/Pasted%20image%2020260709135617.png)
实例：
![Pasted image 20260709143035](attachments/Pasted%20image%2020260709143035.png)
![Pasted image 20260709180352](attachments/Pasted%20image%2020260709180352.png)
建立一个引擎engine，用于登录MySQL并且定位道具体的数据库，后面即赋值变量connection用于连结数据库，操作直接调用变量connection就行了


***==数据库的查询（DQL）==***
![Pasted image 20260709180910](attachments/Pasted%20image%2020260709180910.png)
后面数据库和引擎记得关闭，此方法相当于直接写SQL语言

![Pasted image 20260710204434](attachments/Pasted%20image%2020260710204434.png)

***where放在select()后,若要继续添加限制条件,后面继续跟where,而不是逗号,这点跟MySQL中不同***

![Pasted image 20260710204611](attachments/Pasted%20image%2020260710204611.png)

***倘若限制条件中有多个条件,需要用到and和or,则按以下写法,上面是and的一种特殊写法***

![Pasted image 20260710205658](attachments/Pasted%20image%2020260710205658.png)



***==一张表的创建（DDL）==***
 ![Pasted image 20260714155725](attachments/Pasted%20image%2020260714155725.png)
 meta_data = sqlalchemy.MetaData()最后括号不要忘！！
sqlalchemy.Table是创建表
sqlalchemy.Colum是创建字段名
meta_data为MetaData的一个对象，用于存储所有将要创建的表(未创建该表)
 
变量person是为了将创建表'person‘的数据存储在meta_data中

’person'是MySQL中真正的表名

字段名后面的约束跟MySQL中有所差别，常用如下
![Pasted image 20260709185701](attachments/Pasted%20image%2020260709185701.png)

最后一行代码:  meta_data.create_all(engine)
把 meta_data 里登记过的所有表，创建到 engine 连接的数据库中，此时才是创建meta_data中登记过的所有表，例如上面的person，如果表已经存在，通常不会重复创建。


***==对表中个字段具体数据进行修改(DML)==***
==增加数据==:
		![Pasted image 20260709203838](attachments/Pasted%20image%2020260709203838.png)
		其中 first_name,last_name 是表中的字段名。with的好处是执行结束后会自动关闭连接
		![Pasted image 20260710150844](attachments/Pasted%20image%2020260710150844.png)
		最后要记得commit()保存	
==更新数据==：
![Pasted image 20260710211227](attachments/Pasted%20image%2020260710211227.png)
 这里两个都是一样的，一般推荐写第二种
	
![Pasted image 20260711134627](attachments/Pasted%20image%2020260711134627.png)
![Pasted image 20260712180849](attachments/Pasted%20image%2020260712180849.png)


设定更新操作后记得执行

==删除数据==:
![Pasted image 20260711135155](attachments/Pasted%20image%2020260711135155.png)
删除数据与更新数据类似，将select替换为delete就行
![Pasted image 20260711135430](attachments/Pasted%20image%2020260711135430.png)
删除不需要values,只需要写出where条件即可


主,外键的创立
![Pasted image 20260711142821](attachments/Pasted%20image%2020260711142821.png)



==***多表查询***==
![Pasted image 20260711151237](attachments/Pasted%20image%2020260711151237.png)
![Pasted image 20260711193102](attachments/Pasted%20image%2020260711193102.png)



==***ORM中的映射类***==
	==什么是类==:
		![ecab86967aeaf3b43b22f05a0f714f58](attachments/ecab86967aeaf3b43b22f05a0f714f58.png)


*==**通过类来创建表(DDL):***==
![Pasted image 20260712104311](attachments/Pasted%20image%2020260712104311.png)
这是新的一种映射方式,作用是一样的,下面同理
![Pasted image 20260714155559](attachments/Pasted%20image%2020260714155559.png)

如果约束很多且常用,那么可以
![Pasted image 20260712200659](attachments/Pasted%20image%2020260712200659.png)

*==**各个字段具体数据的添加(DML):**==*
	![Pasted image 20260712104807](attachments/Pasted%20image%2020260712104807.png)
在最后要执行session.commit()上传
![Pasted image 20260712104937](attachments/Pasted%20image%2020260712104937.png)

![Pasted image 20260712134824](attachments/Pasted%20image%2020260712134824.png)
![Pasted image 20260712141322](attachments/Pasted%20image%2020260712141322.png)

==***通过类进行表的查询(DQL):***==
![Pasted image 20260712141540](attachments/Pasted%20image%2020260712141540.png)
![Pasted image 20260712143500](attachments/Pasted%20image%2020260712143500.png)
![Pasted image 20260712180320](attachments/Pasted%20image%2020260712180320.png)



==**一对多ORM,单向关联**,==下图是两个单向关联
![Pasted image 20260713192256](attachments/Pasted%20image%2020260713192256.png)
![Pasted image 20260714144032](attachments/Pasted%20image%2020260714144032.png)

![Pasted image 20260714141031](attachments/Pasted%20image%2020260714141031.png)




==**多对多ORM,双向关联**==
	表的创建:
		![Pasted image 20260714142851](attachments/Pasted%20image%2020260714142851.png)

字段数据的添加:
		![Pasted image 20260714142955](attachments/Pasted%20image%2020260714142955.png)


==**一对一的ORM:**==
	DDL:
	![Pasted image 20260714195645](attachments/Pasted%20image%2020260714195645.png)
	DML:
	![Pasted image 20260714195741](attachments/Pasted%20image%2020260714195741.png)![Pasted image 20260714195741](attachments/Pasted%20image%2020260714195741.png)
	数据库中批量增删改
	![Pasted image 20260716100653](attachments/Pasted%20image%2020260716100653.png)
	数据库一般查询
	![Pasted image 20260716100735](attachments/Pasted%20image%2020260716100735.png)
	