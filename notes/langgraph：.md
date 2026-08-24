langgraph核心三件套:state,node,edge:state用于保存处理前后的数据,node决定state应该怎么处理,edge决定state去往那个node(下面是一个最简单的langgraph)
![](attachments/Pasted%20image%2020260813141226.png)
==***State:***==
	1.reducer:决定后续数据经过node后如何处理(覆盖,添加等等,默认为覆盖）
	![](attachments/Pasted%20image%2020260813141353.png)
	这其中add_message就是graph中自带的一种reducer添加方法，也可以自己写函数去定义一个新的reducer方法
		overright:(不理会reducer规则,直接覆盖写入)
		![](attachments/Pasted%20image%2020260813153300.png)
		需要时在单一节点中使用,
		![](attachments/Pasted%20image%2020260813153414.png)
		需要更新state中的哪些内容,就在节点中return对应的内容,系统会自动根据reducer规则更新state,未返回的字段会保持原样
		![](attachments/Pasted%20image%2020260813153635.png)
	状态类型:
	![](attachments/Pasted%20image%2020260813182736.png)
	
![](attachments/Pasted%20image%2020260813182808.png)
![](attachments/Pasted%20image%2020260813182821.png)
	==输入状态和输出状态应当是全局状态的子集==
	![](attachments/Pasted%20image%2020260813191121.png)
	![](attachments/Pasted%20image%2020260813191249.png)
	==私有状态应当避免与其他状态的字段重名==
	==节点函数应当明确声明入参函数的状态,同时也声明函数返回的状态类型==
![](attachments/Pasted%20image%2020260813184803.png)
	==节点函数中不应该访问入参状态中不存在的字段==
![](attachments/Pasted%20image%2020260813184858.png)
	对应视频:[25_入门基础_四种状态的案例讲解_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1z3NY66EY1?spm_id_from=333.788.player.switch&vd_source=ad4229bd35480150486fcfc67765604e&p=25)

==预定义状态==(官方设置的一种状态,方便开发)
![](attachments/Pasted%20image%2020260813193444.png)
将状态的父类改为官方提供的MessagesState父类,然后在此基础上进行字段的拓展![](attachments/Pasted%20image%2020260813193806.png)
==***Edge:***==
![](attachments/Pasted%20image%2020260814171429.png)
![](attachments/Pasted%20image%2020260814171439.png)
1.静态分支:
	==并行节点:==
	![](attachments/Pasted%20image%2020260814172745.png)
	![](attachments/Pasted%20image%2020260814173325.png)
	==条件分支:==通过定义函数方法决定state的node去向
	![](attachments/Pasted%20image%2020260814203958.png)
	![](attachments/Pasted%20image%2020260814204131.png)
	![](attachments/Pasted%20image%2020260814204250.png)
	当需要state通过分支条件映射多个节点时,分支条件的return需要装进列表![](attachments/Pasted%20image%2020260814212832.png)
	通过path_map映射时则需要把每一个都映射到node上
	![](attachments/Pasted%20image%2020260814212909.png)
	![](attachments/Pasted%20image%2020260814212927.png)
	多节点映射必须使用path_map,否则无法生成正常流程图,后期维护困难
	==延时节点==:创建节点是在节点名后加上defer = True,延时节点会在其他所有正常节点执行完毕后再执行,拿到的state也是其他正常节点执行完毕后的state
	![](attachments/Pasted%20image%2020260815163030.png)
	![](attachments/Pasted%20image%2020260815163044.png)

***==动态分支==***:
==并行节点:==
	==*langgraph中动态分支通过Send方法实现(from langgraph.types import Send),通过定义一个函数方法(需传入对应的state),方法一般是取出改变state的各种值的集合(广义),在return是通过Send创建各个传入不同state的node节点并行运行,最后通过对应的reducer方法整合完整的state继续运行*==
	![](attachments/Pasted%20image%2020260815193038.png)
	**![](attachments/Pasted%20image%2020260815212135.png)==动态分支函数也相当于一个节点,将state引进一个节点进行处理==
条件分支:
![](attachments/Pasted%20image%2020260815213154.png)
![](attachments/Pasted%20image%2020260815214402.png)
动态分支的条件分支与静态分支的条件分支类似,不过动态分支的条件分支通过Command()实现,可以通过update={}方法更新state中的内容,然后通过goto去往指定的节点
![](attachments/Pasted%20image%2020260816151526.png)
![](attachments/Pasted%20image%2020260816151539.png)
![](attachments/Pasted%20image%2020260816151549.png)

==***扇入***==(与扇出相对立,之前的静态分支和动态分支都是扇出,相对应的,扇入也分为静态扇入和动态扇入)
	==静态扇入==(分为“与(and)”扇入和“或(or)”扇入):
		**与(and)扇入:只有当规定好的节点全部执行完毕后才会执行扇入的节点**
		![](attachments/Pasted%20image%2020260816154140.png)
		当"node_c"和"node_d"都执行完成后才会执行"node_e"
		**或(or)扇入:某一节点执行完成后就会执行扇入的节点,扇入节点可以多次执行**
		![](attachments/Pasted%20image%2020260816154323.png)
		“node_c"和"node_d"执行完成后都会执行"node_e",所以"node_e"会执行两次
		==动态扇入==:
		扇入和扇出常常结伴出现,Send代表某个节点并行,并行的情况下总是包含扇入和扇出的,不过扇出不是一定存在,可以并行后直接结束

==***节点错误处理***==(节点处理state时不是100％运行成功,这时候就需要节点的错误处理机制)
==一般的错误处理机制有三种:==这当中,Retry是最常用的错误处理机制,Timeout与Error Handing处理时langgraph新版本的机制,目前只做了解
![](attachments/Pasted%20image%2020260817182145.png)
	==Retry(在创建节点时创建类RetryPolicy的实例,并按需要填入属性)==
	![](attachments/Pasted%20image%2020260817182507.png)
	![](attachments/Pasted%20image%2020260817182807.png)
	==超时控制(Timeout)==:
	![](attachments/Pasted%20image%2020260817183626.png)
	![](attachments/Pasted%20image%2020260817184957.png)
	![](attachments/Pasted%20image%2020260817185109.png)
	==错误处理==(接受抛出的异常,对异常进行处理):
	![](attachments/Pasted%20image%2020260817185636.png)
	![](attachments/Pasted%20image%2020260817185737.png)
	==***节点缓存(如果某一数据重复使用,可以将该数据缓存,需要时随时调用,不需要重复访问)***==】
		适用场景:
		1.节点函数具有确定性,即函数的返回结果是固定值
		 2.节点执行成本较高(大模型的返回结果,API请求,复杂计算等)
		 3.相同输入会重复出现,即重复执行相同流程
		 4.输入能够被缓存键函数稳定处理(缓存是以键值对形式存储的，每个缓存都有唯一的Key，缓存键函数用于生成唯一键)
	![](attachments/Pasted%20image%2020260817191427.png)
	![](attachments/Pasted%20image%2020260817191517.png)
	==***全局默认配置***==
	![](attachments/Pasted%20image%2020260817193430.png)
	![](attachments/Pasted%20image%2020260817193502.png)
	![](attachments/Pasted%20image%2020260817193941.png)

持久化机制(可恢复执行):
	持久化机制即整个图的运行过程中中断了,langgraph能够自行返回关键节点重新运行(与retry不同,retry只针对单个节点,这个保证全图运行)
	![](attachments/Pasted%20image%2020260818102620.png)
	==chenckpointer保存逻辑==(一般推荐异步保存):
	![](attachments/Pasted%20image%2020260818193616.png)
	![](attachments/Pasted%20image%2020260818193727.png)
==**用PostgreSQL保存checkpointer**==:需要先在项目虚拟环境下安装下面两个库![](attachments/Pasted%20image%2020260818155638.png)
==创建pgsql连接==
![](attachments/Pasted%20image%2020260818165828.png)
![](attachments/Pasted%20image%2020260818172338.png)

*==**如何查看checkpoint(方便回滚):**==*
![](attachments/40f8852de980c5f2a9317e983550526e.png)
查看指定的checkpoint时,需要在config中填入具体的checkpoint_id

![](attachments/Pasted%20image%2020260818204623.png)
***==如何从对应的检查点回滚==***
![](attachments/Pasted%20image%2020260819161910.png)
*==**fork操作:不满意最终state结果,可以更新state,然后从想要的checkpoint重新运行**==*
![](attachments/Pasted%20image%2020260819191046.png)
==***长期记忆(这里的长期记忆指长时间不动的信息,如收集的不同用户的性格,性别等,或者给ai设置的固定提示词,可以不同用户分别保存)***==
	==长期记忆的存储==
	![](attachments/Pasted%20image%2020260820163634.png)
	==长期记忆的读取==
	![](attachments/Pasted%20image%2020260820164717.png)
	==如何实现长期记忆==
	![](attachments/Pasted%20image%2020260820171627.png)


==***中断机制(使得用户可以改变state,重新运行)***==
	==中断机制也分为静态中断和动态中断,静态中断即创建时就设定好的固定的中断节点,动态中断则是在运行时根据当前的state状态中断运行(动态中断有一定的规范要求)==
	![](attachments/Pasted%20image%2020260821101353.png)
	**==动态中断==**:
	![](attachments/Pasted%20image%2020260821165300.png)
	![](attachments/Pasted%20image%2020260821170527.png)
	![](attachments/Pasted%20image%2020260821172658.png)
	![](attachments/Pasted%20image%2020260821173819.png)
	==动态并行节点的动态分支(多个interrupt如何处理)==
	![](attachments/Pasted%20image%2020260822103326.png)
	![](attachments/Pasted%20image%2020260822103341.png)
	![](attachments/Pasted%20image%2020260822103401.png)
	![](attachments/Pasted%20image%2020260822103905.png)


	
==**动态中断的使用规范**==:
	1.不要将中断写在try catch当中,try catch的本意是处理异常，中断节点会中断异常处理
	2.一个节点当中如果有多个中断,那么中断的顺序要确定,不能混乱,否则可能导致语义混乱,一般建议一个节点当中只设置一个中断即可
==**静态中断**==
![](attachments/Pasted%20image%2020260824101809.png)


==***工具调用:***==
![](attachments/Pasted%20image%2020260824102539.png)
	==在langgraph当中,与工具调用相关有三个部分:==
	1.ToolNode()这是langgraph官方定义的一个快速创建工具调用节点的一个类方法,只需要传入工具列表,就可以帮开发者创建一个工具调用的节点加入graph图中运行
	![](attachments/Pasted%20image%2020260824102629.png)
	![](attachments/Pasted%20image%2020260824102928.png)
	2.ToolRuntime:ToolRuntime能够记录图在运行过程中的各种内部数据,在工具调用需要时通常通过"runtime.state","runtime.store"等方法直接调用![](attachments/Pasted%20image%2020260824103107.png)
	![](attachments/Pasted%20image%2020260824103320.png)
	3.wrap_tool_call:是在工具实际调用前对传入的信息进行先行一步的处理,判断是否真的需要调用工具进行处理,如果需要,再调用handler(request)真正执行工具,一般在真正执行前会进行
	![](attachments/Pasted%20image%2020260824104924.png)
	![](attachments/Pasted%20image%2020260824105249.png)
	![](attachments/Pasted%20image%2020260824104207.png)
	创建一个工具调用的包装器方法:
	![](attachments/Pasted%20image%2020260824104621.png)
***==流式输出==***
![](attachments/Pasted%20image%2020260824163825.png)
异步情况用astream
![](attachments/Pasted%20image%2020260824190158.png)
	==astream_events():==
	![](attachments/Pasted%20image%2020260824190137.png)
	![](attachments/Pasted%20image%2020260824174802.png)
	![](attachments/Pasted%20image%2020260824184601.png)
	![](attachments/Pasted%20image%2020260824190121.png)
	