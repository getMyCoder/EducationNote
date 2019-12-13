## 语法基础 ##
#### 变量 ####
- 变量不用定义，直接声明使用  
	name='hello'
- 可以连续赋值   
	name=name1='hello'   
- 赋值方式2  
	a,b,c='山东省','济南市','历下区'  
- 作用域
	- 由范围限制
	- 分为两类
		- 全局(global)：在函数外部定义
		- 局部(local)：在函数内部定义
	- 变量的作用范围
	- 在函数外边定义的变量在函数内部可以访问，但是在函数内部调用之后又定义声明了一下全局变量，这里就会报错，问题是变量提升
	<pre>
	a=100
	def fun():
	    print(a)
	    a=200
	    print(a)
	fun()
	</pre>
	- 提升局部变量为全局变量
		- 用global,这里注意在函数外边调用函数内部的全局变量的时候，需要先执行函数，才能调到函数内部的全局变量
			<pre>
			def fun():
			    global a
			    a=10
			    print(a)
			fun()
			print(a)
			</pre>
	- globals,locals函数
		- 可以用globals和locals显示出全局变量和局部变量,用法如下  
		<pre>
		def fun():
		    global a
		    a=10
		    print(a)
		    print(globals())
		    print(locals())
		fun()
		print(a)
		</pre>
	- eval()函数
		- 把一个字符串当做一个表达式来执行
		<pre>
		a=10
		b=10
		c=eval('a+b')
		print(c)
		</pre>
	- exec和上边的eval功能相似，但是没有返回结果exec内部放置的是函数体
		<pre>
		a=10
		b=10
		d=exec('print(a+b)')
		</pre>
#
#####  变量类型  #####
- 数字Number  
	- 数字没有大小限制
	- 正数，负数，0
	- 二进制  
		- 0b开头 例如0b0010
	- 八进制  
		-0o 开头
	- 十六进制  
		- 0x开头
	- 浮点数  
		- 小数 0.5,0.45
		- 科学计数法 5e-10 print(250) print(2.5e2)
		- 复数 a+bi
	- 布尔值
		- 表示真假
		- True/False
		- 当数字使用 True=1 False=0 print(100+True)值为101
		- 除了0以外的都是True
	- 类型转换
		- int(text)把字符串转为Number类型
- 字符串类型str
	- 用单双引号
	- 三引号 保持字符串的格式 可以换行
	- 转义字符、格式化
		- 转义字符  \ 转义字符不同系统有不同的表示方法
		- 格式化  
			- 传统格式化（不提倡使用）（显示小数点后几位用 %.2f为显示小数点后两位）  
			**print('number:%d,age:%d,name:%s'%(10,20,'张三丰'))**
			- format 用函数形式格式化  
			**print('number:{0},age:{1},name:{2}'.format(10,20,'张三丰'))<br>
			print('number:{},age:{},name:{}'.format(10,20,'张三丰'))**
				- 如果没有不写下标，format中的数据的个数要和字符串中的要传入的参数对应起来
				- 使用命名参数  
			**print('number:{num},age:{age},name:{name}'.format(num=15,age=20,name='张三'))**
				- 有浮点小数的写法  {:.2f}
			**print('number:{:.2f},age:{:.2f},name:{}'.format(5.265,20.336,'张三丰'))**
			- 解包操作  \*\*b  
			**a='number:{num},age:{age},name:{name}'<br>
			b={"num":15,"age":20,"name":'张三'}<br>
			print(a.format(\*\*b))**  
			这里是把b对象{}转为()，在b对象的前边用两个星号**
	- 空字符串为False，非空的字符串为True
	- 内置函数  
		- find()如果不存在返回一个-1
		- index()如果不存在返回一个错误
		- s.find(s,25)为在25的位置开始查找  
	**print('hello world'.find('world'))<br>
	print('hello world'.index('world'))**
		- 判断类函数
			- 一般用is开头
			- isalpha判断是会否是字母，如果没有返回False
			- 数字建议用正则表达式
			- islower判断是都是大小写
			- 内容判断类
				- startswith/endswith判断是否已xxx开头或是以xxx结尾
				- suffix被检查的字符串，必须有
				- start开始
				- end 结束  
				**print('hello world'.startswith('hello'))<br>
				print('hello world'.endswith('hello'))**
		- 操作类
			- format格式化使用
			- strip用于删除开头和结尾的空格  
				- strip('A') 清楚字符串中的开头的A和结尾的A
				- lstrip 只操作左边
				- rstrip 只操作右边
			**print(name.strip())**
			- join 拼接字符串  
			**name1='hello'<br>
			name2='$'<br>
			print(name2.join(name1))**
		- type用于查看变量的类型  
		**type(name)**    
	- 字符串补充
		- 格式化
		<pre>
		name='hello {} world {}'
		name1='hello {1} world {0}'
		name2='hello {user} world {age}'
		print(name.format('张三',40))
		print(name1.format('张三',40))
		print(name2.format(user='张三',age=40))
		</pre>
- None类型
	- 用来占位置
	- 返回表示一个空
- 列表list
	- 一种数据类型，就是数组
	- 可以不是一类数据类型
	- 创建list
		- L=[2,3,6]
		- L=list()
		- 查看类型用type(L)
	- 列表的常见操作
		- 访问 
			- 使用下标  
			- 访问的下标超标 返回indexError  
			**L=[2,3,6,2,6,66,66,55]<br>
			print(L[0])**
		- 切片操作
			- 队列表中的某一段进行截取
			- 左包括右不包括
			- L[a:b]从a截取到b，返回一个新的数组  
			**L=[2,3,6,2,6,66,66,55]<br>
			print(L[1:3])**
			- 切片控制的长度（就是跨越几个）
				- print(L[::1])跨越1个
				- print(L[::2]])跨越2个
				- ......
		- id用于判断两个数组是否是同一个数组，这个id是内存中开辟空间的id  
		**L=[2,3,6,2,6,66,66,55]<br>
		print(id(L))**
		- 下标为负数
			- 下标为负数是从最后一个开始往前数
			- 切片的步长为负数是从最后一个往前走
		- 切片和步长和下标为负数的整体使用
			- print（L[-5:-2:1]）从-5位置开始到-2位置，步长为1
			- print(L[-2,-5:-1])从-2位置开始到-5位置，步长为-1，就是到这读取获取数据
		- 获取数组的长度
			- `__len__()`
				<pre>list.__len__()</pre>
			- len()
				<pre>len(list)</pre>
		- 数组循环补充
			- 颗粒循环
			<pre>
			l=[['hello','a',1],['world','b',2]]
			for v,k,s in l:
			    print(v,k,s)
			</pre>
		- 增加元素
			- append()在结尾增加元素 L.append('hello')
			- insert()在自定义的位置中插入L.insert(3,'hello')
			- extend()把一个元素列表插入到另外的一个元素列表中 A.extend(B),把B插入到A元素的中(A元素的尾部)
			- 使用+号使两个数组连接起来
				<pre>
				a=[1,2,3]
				b=[4,5,6]
				c=a+b
				print(c)
				</pre>
		- 删除元素
			- pop()删除指定下标的元素 L.pop(num) num为下标 
			- remove()删除指定元素的 L.remove(num) num为元素
			- del删除指定元素或是指定片段的中元素
				- del L[num]num为下标
				- del L[a:b]a到b指定片段
			- clear清空，清空后的id在内存中是不变的
				- list.clear()
		- 数组翻转
			- list.reverse()
		- count查找list中的某个元素的个数
			- list.count(10)
		- copy拷贝，浅拷贝
			- list中的list的在内存中的地址是一样的
		<pre>
		l=[2,3,6,4,566,2]
		a=l.copy()
		print(id(a))
		print(id(l))
		</pre>
		<pre>
		l=[1,2,3,[5,6,7]]
		a=l.copy()
		print(id(l))
		print(id(a))
		print(id(l[3]))
		print(id(a[3]))
		</pre>
	- 列表内涵 list content
		- 通过简单的方法创建列表
		- 可以进行简单的循环筛选
		<pre>
		l=[2,4,6,7,8]
		a=[i for i in l]
		print(a)
		</pre>
		<pre>
		l=[i for i in range(0,15) if i%2==0]
		print(l)
		</pre>
- 元素tuple
	- 可以理解成是一个不更改的列表
	- 元素可以是任何类型
	- 元素可以相加  
	- tuple的创建
		- T=() 直接用（）
		- T=(100,) 括号中有一个值的时候，需要加上一个逗号，用于区分类型，是一个特例，两个元素以上的就不许要
		- T=100, 直接用逗号
	- list转为tuple  
		**L=[26,3,63,6,'hello']<br>
		T=tuple(L)<br>
		print(T)**
	- 有序
		- T[0]取值和list是一样的
		- 切片和list是一样的
		- 可以访问不可以修改
	**A=(100,22,0,11,1)<br>
	B=('hello','world')<br>
	C=A+B<br>
	print(C)**
	- 元素相乘（就是把元素复制）  
	**t=(1,3,6)<br>
	tt=t\*2<br>
	print(tt)**
	- 成员检测  
		if a in b:
	- 元祖遍历  
		for i in T:
	- 元祖嵌套  
		T=(1,(2,3))  
		嵌套的元祖循环  
		for i,j,k in T:  
		这里的i,j,k对应的是元祖中的第一个第二个第三个
	- 常用元祖函数
		- len 长度 print(len(t))
		- max求最大值 print(max(t))
		- min最小值、
		- count对元素计数 count(1)有几个1
		- index某一个元素所在的位置 T.index(1)1所在的位置
		- 特殊用法 a,b=b,a把a和b的值互换		
- 字典dict
	- 字典是一种组合数据，没有顺序的组合数据，数据以键值对的形式出现
	- 字典的声明方式(就是对象)
		<pre>
		a={'name':"张三",'age':20}
		b=dict({'name':"张三",'age':20})
		c=dict(name="张三",age=20)
		d=dict([('name','张三'),('age',20)])
		print(a)
		print(b)
		print(c)
		print(d)
		</pre>
	- 字典是序列类型，但是是无序的，没有分片和索引
	- 内容是以键值对的方式存在
	- 字典的常用操作
		- 访问数据
		<pre>
		d={'name':1,'age':2}
		print(d['name'])
		</pre>
		- 赋值操作
		<pre>
		d={'name':1,'age':2}
		d['name']='张三'
		print(d)
		</pre>
		- 删除某个元素del
		<pre>
		d={'name':1,'age':2}
		del d['age']
		print(d)
		</pre>
		- 检查成员（检测的是键值）
			- in，for in
			<pre>
			d={'name':1,'age':2}
			if 'name' in d:
			    print(d['name'])
			if 'www' not in d:
			    print('no')
			</pre>
		- 遍历的循环在2和3中的代码是不通用的
			- for a in d
			- for a in d.keys() 键名循环
			- for a in d.values()键值循环
			- for a,b in d.items()键值对循环，特殊使用
			<pre>
			d={'name':1,'age':2}
			for a in d:
			    print(a,d[a])
			for a in d.keys():
			    print(a)
			for a in d.values():
			    print(a)
			for a,b in d.items():
			    print(a,b)
			</pre>
	- 字典生成式
		<pre>
		d={'name':1,'age':2}
		dd={k for k in d.items()}
		print(dd)
		ddd={k for k in d}
		print(ddd)
		</pre>
	- 字典的相关函数
		- 通用函数len,max,min,dict
		- str:返回字典的字符串格式
		- clear：清空字典
		- items：返回字典的键值对组成的元素格式
		- keys()键名
		- values()键值
		- get:通过键名获取键值
		- formkeys:根据键名生成键值
		<pre>
		print(str(d))
		print(type(d.items()))
		print(d.keys())
		print(d.values())
		print(d.get('name'))
		#fromkeys的用法
		l=['hello','world','shandong ']
		dd=dict.fromkeys(l,'济南')
		print(dd)
		</pre>
- 集合set
	- 和数学的集合一样
	- 内容无序+内容不重复（默认去掉重复的）
	- 创建set()
		- s=set(list)创建的对象中的内容只能有一个变量，这里不能往里边添加内容
		- 使用大括号 s={1,2,3,6,1,6}
	- 集合的操作
		- in操作 if num in s:
		- for循环 for i in s:
		- 集合的另外一种遍历方法 for i,j,k in s:  {(1,2,3),(),()},对应的tuple中的第一个，第二个，第三个
	- 集合的生成式  
		s={i for i in sa}  
		s={i for i in sa if i%2==0}
		a={i*2 for i in s}
		a={n*m for n in s for m in s}
	- 集合的内置函数
		- len长度
		- max/min
		- add往集合中添加内容
		- clear清空
		- remove/discard删除  
			- set.remove(num)num是值,删除的值如果有不存在会报错
			- discard用法同上，删除的值如果不存在是不报错的
		- pop删除的内容是随机的
	- 集合的数学操作
		- intersection 求交集  
		**a={1,2,3,4,5,6}<br>
		b={7,8,9,4,5,6}<br>
		print(a.intersection(b))**
		- 求差集 difference  
		**a={1,2,3,4,5,6}<br>
		b={7,8,9,4,5,6}<br>
		print(a.difference(b))**
		 注意：a交b的差集(a-b)和b交a的差集(b-a)不一样
		- 并集 union  
		**a={1,2,3,4,5,6}<br>
		b={7,8,9,4,5,6}<br>
		print(a.union(b))**
		- issubset检查一个集合是否是另一个子集
		- issuperset检查一个集合是否是另一个集合的超级
	- frozenset冰冻集合
		- 集合不能进行任何操作
- map
### 表达式 ###
		a=1+2
### 运算符 ###
		加、减、乘、除、赋值、位运算  
### 算数运算符   ###
- 用来进行算数运算的符号
-  表示加减乘除
-  没有自增自减
-  /为除法 //为除法取整数 print(9/2) print(9//2)
	- 正数除以负数求余：证书除以负数后得到的负小数取消数整数，然后用除数减去取得的值乘以被除数后的值为余数  
	  `例如 9%-4 为9//-4等于-3，然后9-((-3)*(-4))=-3 所以9%-4的余数为-3`
-  比较运算符
	- 大于、大于等于、小于、小于等于
	- 结果是一个布尔值
	- a的4次幂的写法为a**4
-  赋值运算符
	- 就是等号
-  逻辑运算符
	- 对布尔值进行运算的符号
	- and逻辑与
	- or逻辑或
	- not逻辑非，就是取反
	- 没有亦或
	- 短路问题，知道结果后不再往下运行，直接把结果返回出来
	- 字符串乘以数字是吧字符串重复多少遍的意思
-  成员运算符
	- 用来检测一个值或是变量是否在某个集合里边
	- in 成员运算符
	- not in 不在里边的意思  
	**a=10
	c=[2,3,61,10]<br>
	b=a in c<br>
	print(b)**
-  身份运算符
	- 用来确定两个变量是否是同一个变量
	- is 变量运算符
	- is not 不是  
	- 这里的是地址中的内存用同一个为True,[-5,256]中的相同的数字用同一个内存
	**a=10<br>
	b=20<br>
	print(a is b)**
-  运算符的优先级问题
	-位运算 >> << 右移 左移
### 程序结构 ###
- 三种结构
	- 顺序
	- 循环
	- 分支
### 分支结构 ###
- 分支结构基本语法
	- if语句
	- while语句
	- input的作用
		- 在屏幕上输出括号你内的字符串
		- 接受用户输入的内容并返回带程序
		- input返回的内容一定是字符串类型
		**a=input()<br>
		if a=='man':<br>
		print('男生')<br>
		else:<br>
		print('女生')**  
		*--------------------------------------*  
		**text=input('成绩输入')<br>
		if int(text) > 90:<br>
		    print('成绩优秀')<br>
		else:<br>
		    print('成绩较差')**
### 多路分支 ###
- if 条件:	elif 条件:  else:
- if嵌套使用
- 没有switch语句 
### 循环语句 ###
- for循环
	- for 变量 in 序列：  
	**for i in range(10):<br>
    print(i)**
	- for-else语句执行完for语句后可以执行一个else语句用于结尾  
		**for i in range(10):<br>
		    print(i)<br>
		else:<br>
		    print('is none')**
- while循环
	- 条件成立执行循环
	- 另外一种表达式 while 条件:    else:
	**a=0<br>
	while a<6:<br>
	    print(a)<br>
	    a+=1<br>
	else:<br>
	    print('over')**
- 停止循环
	- break 整个循环结束
	- continue	跳出当前循环，执行后边的循环
	- pass 不做任何操作，当做占位符使用(if条件中必须要有语句，可以用pass作为占位符)
- 生成序列range
	- range(10)生成一个0到10的数字
	- range(1,10)生成一个1到10的数字
	- 左包括右不包括
	- randint是个特例
### 函数 ###
- 自定义函数
- 形参 没有值，用于占位
- 实参 调用的时候实际输入的值
- print("{0} asdf".format(val))
- 函数执行完默认会返回一个return None
- help获取函数的文档，help(print)  
###### 例子 ######
    for i in range(1,10):
    	for j in range(1,i+1):
    		print("%d*%d=%d"%(i,j,i*j),end=" ")
   		 print()
#### 参数详解 ####
- 参数分类
	- 普通参数/位置参数  
		 **def name(a,b,c):<br>
   		 print(a,b,c)**
	- 默认参数  
		**def name(a,b,c=10):<br>
   		 print(a,b,c)**
	- 关键字参数  
		**def name(a,b,c):<br>
		print(a,b,c)<br>
		name(a=1,b=2,c=3)**
	- 收集参数
		- 把没有位置，不能和定义时的参数位置相对应的参数，放入一个特性的数据结构中
		- 语法 def fun(*args)
		- 收集参数可以和其他的类型参数共存
		- 一般在不确定参数的情况下使用收集参数
		<pre>
		def fun(*args):
		    list=args
		    for item in list:
		        print(item)
		fun('张三',40,'man')
		</pre>
		- 收集参数之关键字收集参数
			- 简言之就是对象
			- 传入的参数是不确定的
			- 传入的参数要有键名键值
			- 例子
			<pre>
			def fun(**args):
			    print(args)
			    for item in args:
			        print(item,args[item])			
			fun(name='张三',age=40,sex='man')
			</pre>
	- 各种参数整体使用
		- 传入参数的顺普通参数、收集参数、关键字参数、收集参数关键字参数
	<pre>
	def fun(name,age,*args,aaa='空',**kwargs):
	    print(name)
	    print(age)
	    print(aaa)
	    print(args)
	    print(kwargs)
	fun('张三',40,'小红','小刚','小李',aaa='内容',user='adf',sex='man')
	</pre>
#### 递归函数####
- 函数调用自身
- 递归函数有一个深度，这个深度跟电脑的自身配置有关系
#### 函数文档 ####
- 函数的文档的作用是对当前函数提供使用相关的参考信息
	- 函数文档一般用于help进行查看
	- 使用stu。__doc__
	- 函数的文档定义 一般用''' 内容 '''
	<pre>
	def stu(name,age):
    '''
    参数定义
    :param name:姓名 
    :param age: 年龄
    :return: 
    '''
    return 1
	</pre>
#### 面向对象 OOP####
- 常用名词
	- OO：面向对象
	- OOA：分析
	- OOD：设计
	- OOP：编程
	- OOI：实现
	- OOA->OOD->OOI
- 类和对象
	- 类描述的是集合（如：学生）
		- 动作，函数
		- 属性，变量
	- 对象描述的是个体 （如：张三，有各种属性）
	- 类是描述集合，对象是集合中的个体，属性是描述个体的特征，方法是描述个体的动作或是事件
	- is-a
	- 定义类：class  
	<pre>
	class Student():
		pass
	</pre>
	- 类的介绍
		- 类就是对象
		- 用点调用方法或是属性
		- 检查类的所有成员
			- class_name.\_\_dict\_\_
			<pre>
			class Student():
			    name=None
			    age=18
			    def fun(self):
			        print('hello world')
			        return None
			student=Student()
			print(Student.\_\_dict\_\_)
			</pre>
		- 检查所有成员要用\_\_class_name\_\_,不能是实例化后的对象
		- 实例化后的对象，只是访问的时候，在内存中的地址和没有实例化之前的地址是一样的
		- 实例化后重新对类的成员进行重新赋值，这个值会保存到实例化的对象中，并不会改变类中的属性的值
		- 类多次实例化，是把每个实例化的对象创建一个新的对象，每个实例化的对象相互不影响
		- 类中的self和JavaScript中的this是一样的，表示对象本身
		- 类中嵌套字典的使用
		<pre>
		class Student():
		    infor={
		        'user':'',
		        'age':10
		    }
		    def fun(self):
		        self.infor['user']='adsfasdf'
		        print(self.infor['user'])
		stu=Student()
		stu.fun()
		</pre>
		<pre>
		class Student():
		    name=''
		    def __init__(self,user):
		        self.name = user
		        print('*****',id(user))
		    def fun(self):
		        print(self.name)
		        return None
		a=Student('张三')
		b=Student('李四')
		a.fun()
		b.fun()
		print(id(a.name))
		print(id(b.name))
		</pre>
	- 例子  
	    <pre>
		class Setname():
		    name='张三'
		    age='40'
		    def fun(self):
		        print(self.name)
		        return None
		getName=Setname()</pre>
	- 类的属性
	- 方法中的self
		- 指代本身
		- 不是关键字
		- 调用该方法的时候不需要传
	- 类的变量的作用域的问题  
		- 实例属性如果不存在则访问类的属性
	- 访问类的属性
		- 类里边如果强制访问类的属性，要用\_\_class__
		- 类方法，里边没有self
		- 不定义self无法访问类的属性
			- 想要访问类的属性，使用类名，间接指代
			<pre>
			class SetAge():
			    name='李四'
			    age=20
			    def fun():
			        print(SetAge.name)
			        return None
			setage=SetAge()
			SetAge.fun()
			</pre>
			- 用\_\_class__访问,间接指代  
			<pre>
			class SetAge():
			    name='李四'
			    age=20
			    def fun01():
			        print(__class__.name)
			        return None
			setage=SetAge()
			SetAge.fun01()
			</pre>
		- 调用类的属性和方发
			- 实例化后再调用类的属性和方发
			- 直接调用类的属性Student.fun()
				- 如果这个方法中没有参数(self)，或是没有用到参数，可以直接调用，不会把报错
				- self和\_\_class__，self指向的是当前类的属性，class指向类中初始值的属性的值
				- 如果这个方法中有参数(self),在调用的时候也可以直接调用，但是要传入参数(self),但是这里如果传入随意的参数会报错，可以传入stu=Student()实例化后的stu，也可以传入一个新的类，但是类中的属性或是方法在这个新的类中都要有。这种类型称为鸭子模型
				<pre>
				class Student():
				    name='张三'
				    def fun(self):
				        self.name='hello'
				        print(self.name)
				    def aa(self):
				        print(__class__.name)
				    def ab():
				        print('this is no value')
				    def ac(self):
				        print(self.name)
				stu=Student()
				stu.fun()
				Student.fun(stu)
				Student.ab()
				class A():
				    name='山东省济南市'
				Student.ac(A)
				</pre>
				- 类中的方法有属性的值的设置的时候，在方法执行完成后，整个类中的属性值也会发生变化
				<pre>
				class Student():
				    name='张三'
				    def fun(self):
				        self.name='hello world'
				        print(self.name)
				    def aa(self):
				        print(self.name)
				st=Student()
				st.aa()
				st.fun()
				</pre>
- 构造函数
	- 类的实例化的时候执行初始化的工作
	- 使用特殊的名称和写法  
		<pre>
		def __init(self)__:
			pass
		</pre>
	- 构造函数是在实例化的时候自动执行的
	- 构造函数内部不能直接访问类内部构造函数外部的变量，但是可以方位类的外部的变量
- 继承
	- 继承
		- 子类可以使用父类的内容和行为
		- 继承的实现
			- 父类，基类，超类：被继承的类，Base Class，Super Class
			- 子类：有继承行为的类
		- 所有的类都必须有父类
			- 如果没有，默认给一个object的子类
			- print(issubclass(Parse,object))object是最外成的父类
		- 如果继承的子类中的变量和父类中的变量存在冲突的时候优先使用子类的变量
		- 子类如果想扩充父类的方法，可以在定义的新方法中调用父类的方法进行重用，也可以用super().父类成员
			<pre>
			class Parse():
			    name = '李四'
			    def setName(self):
			        print('this is parse fun')
			class Son(Parse):
			    name='www.baidu.com'
			    age='20'
			    def setNames(self):
			        self.setName()
			        print('this is son fun')
			son=Son()
			son.setNames(),
			</pre>
			- 第二种写法
			<pre>
			class Parse():
			    name = '李四'
			    def setName(self):
			        print('this is parse fun')
			class Son(Parse):
			    name='www.baidu.com'
			    age='20'
			    def setNames(self):
			        Parse.setName(self)
			        print('this is son fun')
			son=Son()
			son.setNames()
			</pre>
			- 用super()
			<pre>
				class Parse():
				    name = '李四'
				    def setName(self):
				        print('this is parse fun')
				class Son(Parse):
				    name='www.baidu.com'
				    age='20'
				    def setName(self):
				        super().setName()
				        print('this is son fun')
				son=Son()
				son.setName()
			</pre>
		- issubclass 验证两个类是否是父子关系
		- 子类没有构造函数会自动继承父类的构造函数
		- 多继承
			- 两个类可以让子类同时继承
			- 子类同时继承的两个类不能是父子类
			- 被继承的两个类可以是同时继承的父类的兄弟类
			- 子类可以同时继承两个父类，但是如果父类中的变量存在相同的，则取第一个
			<pre>
			class Person():
			    name='张三'
			class Student01(Person):
			    age01=10
			class Student02(Person):
			    age02=20
			class me(Student01,Student02):
			    def fun(self):
			        print(self.name)
			        print(self.age01)
			        print(self.age02)
			        return None
			m=me()
			m.fun()
			</pre>
		- 代码案例
		<pre>
       	class Person():
		    name='person'
		class Student(Person):
		    def fun(self):
		        print(self.name)
		        return None
		class Teacher(Person):
		    age=10
		    def fun(self):
		        print(self.name)
		        return None
		class Sex():
		    sex='man'
		class me(Person,Sex):
		    def fun(self):
		        print(self.name)
		        print(self.age)
		        return None
		teacher=Teacher()
		teacher.fun()
		print(issubclass(Student,Person))
        </pre>
		- 构造函数的继承
			- 构造函数默认是自动继承的
			- 如果构造函数中有需要传递参数的，在继承的子类需要把参数传递进去
			- 构造函数的默认参数self必须要有
			- 代码案例
			<pre>
			class Person():
			    def __init__(self,name,age):
			        print(name,age)
			class Student(Person):
			    pass
			student=Student('张三',20)
			</pre>
		- 继承变量函数的查找顺序问题
			- 优先查找自己的变量
			- 没有则查找父类
			- 本类中如果没有构造函数，则自动查找父类的构造函数
		- 构造函数
			- \_\_init__(self)
			- 构造函数的写法是固定的
			- 实例化的时候自动执行，无需调用
			<pre>
			class Dog():
			    def __init__(self):
			        print('this is dog')
			        return None
			dog=Dog()
			</pre>
			- 如果本类中没有构造函数则向上查找
			<pre>
			class Animal():
			    def __init__(self):
			        print('this is animal')
			class Dog(Animal):
			    def __init__(self):
			        print('this is dog')
			        return None
			class Cat(Animal):
			    pass
			dog=Dog()
			cat=Cat()
			</pre>
			- 构造函数中如果有参数，则需要在实例化的时候传递
			<pre>
			class Animal():
			    def __init__(self):
			        print('this is animal')
			class Dog(Animal):
			    def __init__(self,name):
			        print('this is dog',name)
			dog=Dog(20)
			</pre>
			- 父类的所有成员
				- A.\_\_mor__
	- 单继承多继承
		- 单继承
			- 只能有一个父类
			- 使用较多
			- 但是功能不能无限扩展
		- 多继承
			- 可以继承多个父类
			- 不太建议使用
			- 类的功能扩展方便
			- 继承关系混乱
		- 继承表
			- MRO是继承的父子多层的关系
			- python采用c3算法
		- 继承的构造函数，需要注意的是如果父类的构造函数需要传参数，如果不传参会报错
		- 使用super调用父类中的构造函数
		- 构造函数继承(就是有一部分功能在父类的构造函数中已经实现了，现在只需要继承过来)
			- 直接继承
			<pre>
			class A():
			    def __init__(self):
			        print('this is A')
			class B(A):
			    def __init__(self,name):
			        print('this is B',name)
			class C(B):
			    def __init__(self,name):
			        B.__init__(self,name) #用B.__init__()
			        print('this is C')
			c=C('CCCC')
			</pre>
			- 拓展父类的构造函数，使用super继承
			<pre>
			class A():
			    def __init__(self):
			        print('this is A')
			class B(A):
			    def __init__(self,name):
			        print('this is B',name)
			class C(B):
			    def __init__(self,name):
			        super(C,self).__init__(name)
			        print('this is C')
			#在调用的时候传参
			c=C('张三')
			</pre>
			<pre>
			class A():
			    def __init__(self):
			        print('this is A')
			class B(A):
			    def __init__(self,name):
			        print('this is B',name)
			class C(B):
			    def __init__(self):
			        # 在继承构造函数的时候继承
			        super().__init__('李四')
			        print('this is C')
			c=C()
			</pre>
			上边两种方法区别是怎么传参的问题
		- 构造函数中一般是用于初始化的作用
	- 封装
		- 对对象的成员进行访问限制
		- 三个级别
			- 公开 public
			- 受保护的 protected
			- 私有的private
			- public、protected、private不是关键字
		- 访问限制在python中更像是一种思想
		- 私有
			- 在当前的类中或是对象中访问
			- 私有变量的定义 __name,在属性前边加上两个下划线
			<pre>
			class Student():
			    name = 'hello world'
			    __age=20
			    def fun(self):
			        print(self.name,self.__age) #只有在类的内部才能使用
			st=Student()
			st.fun()
			print(st.name)
			print(st.__age) #访问不到
			</pre>
			- 私有不是真正的私有，如果要访问私有属性的方法
				- 检查类成员
				- 调用
				<pre>
				class Student():
				    name = 'hello world'
				    __age=20
				    def fun(self):
				        print(self.name,self.__age)
				st=Student()
				print(Student.__dict__) #检查成员
				print(st._Student__age)	#访问私有属性__age			
				</pre>
			- 在成员内部可以访问，在外部不行
	- 多态
		- 多态就是在同一个对象中不同的情况表现出的不同的状态
		- 不是语法，是一种设计思想
		- Mixin设计模式
			- 主要采用多继承对功能的扩展
			- 必须表示某一个单一的功能，
			- 简单来讲就是方法父子类中的方法是一样的，表示单一功能（就是多继承）
	- 类的相关函数
		- issubclass，用于判断类的父子关系
		<pre>
		class Fash(Person):
		    def run(self):
		        print('鱼在游.....')
		class FashA(Fash):
		    print('this is fasha')
		print(issubclass(FashA,Fash))
		</pre>
		- isinstance()，用于判断一个对象是否是一个类的实例
		<pre>
		class Fash(Person):
		    def run(self):
		        print('鱼在游.....')
		class FashA(Fash):
		    print('this is fasha')
		fly = Fly()
		fash = Fash()
		print(issubclass(FashA,Fash))
		print(isinstance(fashA,Fash))
		</pre>
		- hasattr，检测一个对象时候有某个成员,检测的成员要用引号
		<pre>
		class Fash(Person):
		    def run(self):
		        print('鱼在游.....')
		class FashA(Fash):
		    print('this is fasha')
		fly = Fly()
		fash = Fash()
		print(hasattr(fash,"run"))
		</pre>
		- setattr设置成员对象
		- getattr获取成员对象
		- delattr删除成员对象
		- dir获取对象的成员列表
	- 类的成员检测符
		- 类的成员属性就是对类的某些属性进行一定的操作
			<pre>
			class Student():
			    name='张三'
			    def __init__(self):
			        self.setName()
			    def setName(self):
			        print(self.name)
			s=Student()
			</pre>
			- 简单讲就是在构造函数中执行对某些属性操作的方法
			- get获取属性的操作
			- set修改或是添加属性的操作
			- delete删除属性操作
		- 使用类的成员描述符
			- 使用类实行
			- 类的属性
			- 使用property函数
				- property(fget,fset,fdel,doc)
				- 使用方法
				<pre>
				class Person():
				    def fget(self):
				        print('this is fget',self._name)
				        return self._name
				    def fset(self,name):
				        self._name=name
				        print('this is fset',name)
				    def fdel(self):
				        self._name='NoneName'
				        print('this is fdel')
				    name=property(fget,fset,fdel,'this is doc')
				p=Person()
				p.name='张三'
				print(p.name)
				</pre>
				参数解析：对于传入的参数只能透过fset进行设置，获取的fget是不能传入参数的，只能获取数据和返回，fdel是执行的对参数或是变量的结尾操作
		- 类的内置属性
			- \_\_dict__ 以字典的方式显示类的成员组成
			- \_\_doc__获取类的文档信息
			- \_\_name__获取类的名称，如果在模块中使用获取的是模块的名称
			- \_\_bases__获取某个类的所有父类，以元祖的形式显示
			<pre>
			class Student():
			    '''
			    说明文档
			    '''
			    name='张安',
			    def setName(self):
			        print('this is setName')
			print(Student.__dict__)
			print(Student.__doc__)
			print(Student.__name__)
			print(Student.__bases__)
			</pre>
- 下划线
	- '_A'一个下划线表示只有类和子类能够使用 无法通过important引用
	- '__A'两个下划线表示只能当前的类的对象的本身使用
	- '__A__'表示系统函数
- 魔法函数
	- 魔法函数概述
		- 不要认为的调用，在特殊的时刻自动执行
		- 特征，方法名被前后两个下划线包裹
		- 需要学习的时候在什么时候调用什么魔法函数
	- 操作类
		- \_\_init__:类中自动初始化的函数
		- \_\_new__:对象实例化方法，类中首先被调用方法，一般不使用
		- \_\_call__:对象当做函数使用的时候触发
			- 实例化类后直接把实例化的类当做方法执行
			<pre>
			class A():
			    def __init__(self):
			        print('this is __init')
			a=A()
			a()
			</pre>
			这里a是一个类的实例化对象，但是不是方法，如果要调用，这里默认的是调用一个\_\_call__的方法
			<pre>
			class A():
			    def __init__(self):
			        print('this is __init')
			    def __call__(self, *args, **kwargs):
			        print('这是一个__call__函数')
			a=A()
			a()
			</pre>
			使用方法如上
		- \_\_str__:当把对象当做字符串使用的时候引发的函数
			<pre>
			class A():
			    def __init__(self):
			        print('this is __init')
			    def __str__(self):
			        return 'this is __str__'
			a=A()
			print(a)
			</pre>
			把实例化的a对象直接使用的时候自动执行\_\_str__方法，返回的值就是a对象的
		- \_\_repr__返回字符串，和上边的str方法一样，也有区别
	- 描述服相关
		- \_\_get__
		- \_\_set__
		- \_\_delet__
	- 属性操作相关
		- \_\_getattr__访问一个不存在的属性的时候触发
			<pre>
			class A():
			    def __getattr__(self, item):
			        print('__getattr__')
			a=A()
			print(a.setName)
			</pre>
			该方法会把要调用的方法当做参数传递进\_\_getattr\_\_方法中，如果传递进去的方法存在则执行，如果不存在则会执行\_\_getattr\_\_内部的方法
		- \_\_setattr__对成员属性进行设置的时候触发
			- 存在三个参数，(self,key,val)
			- self当前对象
			- key设置属性名称
			- value设置属性或是名称的值
			- 不能对属性进行直接赋值操作
			<pre>
			class A():
			    def __init__(self):
			        print('this is init')
			    def __setattr__(self, key, value):
			        print("执行到此处了")
			        super().__setattr__(key,value)
			a=A()			
			a.setName=100			
			print(a.setName)
			</pre>
			此处需要调用父类的setattr方法，如果直接使用该类中的setattr会出现死循环，在使用的时候赋值就可以进行正常赋值
	- 运算分类相关魔术方法
		- \_\_gt__进行大于运算的时候触发
			- 参数self，本省
			- 第二个对象
				- 返回任意值，推荐boole
			<pre>
			class A():
			    def __init__(self,name):
			        self.name=name
			    def __gt__(self, other):
			        return self.name>other.name
			a1=A(10)
			a2=A(1000)
			print(a1>a2)
			</pre>
			使用方法如上，需要比较的是两个实例化传入的参数，
			用于比较的两个参数会默认\_\_init\_\_为第一个参数，\_\_gt\_\_的参数为第二个参数进行比较
	- 类和对象的三种方法
		- 实例方法
			- 需要实例化对象才能使用的方法，使用的时候需要截止对象的的其他对象的方法完成
		- 静态方法
			- 不需要实例化，通过类直接访问(也可以通过实例化后的对象进行调用)；参数随意，没有“self”和“cls”参数，但是方法体中不能使用类或实例的任何属性和方法；
		- 类方法
			- 不需要实例化(也可以通过实例化后的对象进行调用)；该参数名一般约定为“cls”，通过它来传递类的属性和方法（不能传实例的属性和方法）；
		<pre>
		class A():
		    def setName(self):  #实例化方法
		        print('this is 实例化方法')
		    @classmethod；    #类方法
		    def name(cls):
		        print('this is 类方法')
		    @staticmethod   #静态方法
		    def staticName():
		        print('this is 静态方法')
		a=A()
		#实例化
		a.setName()
		#类方法
		a.name()
		A.name()
		#静态方法
		a.staticName()
		A.staticName()
		</pre>
		- 区别
	- 成员描述符
		- 变量的三种用法
			- 查询（调用）
			- 修改（修改变量）
			- 删（删除变量）
			<pre>
			class A():
			    def __init__(self):
			        self.name='www'
			a=A()
			print(a.name) #查询
			a.name='http' #修改
			print(a.name)
			del a.name  #删除
			print(a.name)
			</pre> 
		- 属性property
			<pre>
			class A():
			    def __init__(self):
			        self.name='张三'
			    def fget(self):
			        print('我被执行了')
			        return self.name
			    def fset(self,name):
			        self.name='百度:'+name
			    def fdel(self):
			        print('删除成功')
			    user=property(fget,fset,fdel,'this is property')
			a=A()
			print(a.name)
			a.user='AAA'
			print(a.user)
			</pre>
			property方法是默认是调用fget方法，当给user设置值的时候才会调用fset方法，如果直接调用a.user是只调用fget而不调用fset
		- 抽象类
			- 抽象方法的定义：没有具体实现内容的方法成为抽象方法
			- 抽象方法不是在父类中定义具体的方法，需要在继承的子类中实现具体的方法
			<pre>
			class A():
			    def say(self):
			        pass
			class B(A):
			    def say(self):
			        print('this is person')
			class C(A):
			    def say(self):
			        print('this is animal')
			a=A()
			a.say()
			b=B()
			b.say()
			c=C()
			c.say()
			</pre>
			- 抽象的类需要借助abc模块，import abc
			- 声明抽象类的方法
				- class Human(metaclass=abc.ABCMeta) 这种写法是死的，只能这么写
				- 抽象方法的定义
					@abc.abstractmethod
					<pre>
					import abc
					class Human(metaclass=abc.ABCMeta):
					    # 定义一个抽象的方法
					    @abc.abstractmethod
					    def person(self):
					        pass
					        # print('this is person')
					    # 定义类抽象方法
					    @abc.abstractclassmethod
					    def animal(cls):
					        pass
					        # print('this is animal')
					    # 定义静态抽象方法
					    @abc.abstractstaticmethod
					    def god():
					        pass
					</pre>
			- 抽象类的使用(抽象方法使用较少)
				- 抽象类可以包含抽象方法，也可以是具体的方法
				- 抽象类中可以有方法可以有属性
				- 抽象类不能直接实例化
				- 必须继承才可以使用，且继承的子类必须实现所有继承类的抽象方法
				- 假定子类没有实现继承的所有的抽象方法，子类也是不能实例化的
				- 抽象类的主要作用是设定类型的标准，以便于开发的时候具有统一的规范
				<pre>
				import abc
				class Human(metaclass=abc.ABCMeta):
				    # 定义一个抽象的方法
				    @abc.abstractmethod
				    def person(self):
				        pass
				    # 定义类抽象方法
				    @abc.abstractclassmethod
				    def animal(cls):
				        pass
				    # 定义静态抽象方法
				    @abc.abstractstaticmethod
				    def god():
				        pass
				class Other(Human):
				    def person(self):
				        print('我继承了父类person')
				    def animal(cls):
				        print('我继承了父类animal')
				    def god():
				        print('我继承了父类god')
				other=Other()
				other.person()
				other.animal()
				Other.god()
				</pre>
			- 自定义类
				- 函数名称可以当做变量使用
				- 外面定义的类要用参数
				<pre>
				class A():
				    pass
				def setName(self):
				    print('this is fun')
				A.setName=setName
				a=A()
				a.setName()
				</pre>
				同
				<pre>
				class A():
				    def setName(self):
				        print('this is fun')
				a=A()
				a.setName()
				</pre>
				- 类就是一堆属性和一堆方法的集合，可以自定义的组装
				- 组装的类需要在实例化之前赋值完成，也就是说往类上绑定方法(带参数)，而不是往实例化上绑定方法
					- 对于往实例化上绑定方法需要借助于第三发木块 from types impor MethodType
					<pre>
					from types import MethodType
					class A():
					    pass
					def B(self):
					    print('this is B')
					a=A()
					a.B=MethodType(B,A)
					a.B()
					</pre>
				- 把单独的类和单独的方法组装起来
				- 借助于type实现
				- type参数(类的名、继承的父类、类中的方法)
				<pre>
				def name(self):
				    print('this is name')
				def age(self):
				    print('this is age')
				A=type('Aname',(object,),{'class_Name':name,'class_Age':age})
				a=A()
				a.class_Name()
				a.class_Age()
				</pre>
				- 利用元类实现，Metaclass,
				- 元类的写法是固定的，必须继承type
					- class A(type)
					<pre>
					class person(type):
					    def __new__(cls, name,bases,attrs):
					         attrs['id']='001'
					         return type.__new__(cls,  name,bases,attrs)					
					class getPerson(object,metaclass=person):
					    pass
					get=getPerson()					
					print(get.id)
					</pre>
					metaclass为动态创建类的写法，创建类的内容为person继承的type的类，需要注意创建的person的类中的__new__的参数
#### Python包 ####
- 模块
	- 一个模块就是一个包含python代码的片段，文件后缀为.py，模块就是python文件
	- 模块的有点
		- 程序拆分，方便维护
		- 重复使用
		- 当做命名空间使用
	- 定义
		- 就是普通文件
		- 为了规范，最好在模块中书写
			- 函数（最好功能单一）
			- 类（相似功能的组合）
			- 测试代码
	- 如何使用
		- 模块直接导入
		- 语法
			<pre>
			import module
			module.className
			module.function()
			A=module.AB()
			A.function()
			</pre>
		- 案例
			- 包文件
			<pre>
			class Student():
			    def __init__(self,name,age):
			        self.name=name
			        self.age=age
			    def setName(self):
			        print('this is student:{0},age:{1}'.format(self.name,self.age))
			def say():
			    print('hello world')
			</pre>
			- 引用包文件
			<pre>
			import p01
			A=p01.Student('张三',33)
			A.setName()
			p01.say()			
			</pre>
		- 包名为数字的不能直接导入
			- 借助importLib
		- import 模块 as 别名
			<pre>
			import p01 as AA
			A=AA.Student('张三',33)
			A.setName()
			AA.say()
			</pre>
		- from module import func\_name,class\_name
			<pre>
			from p01 import Student,say
			A=Student('张三',33)
			A.setName()
			say()
			</pre>
		- from module\_name import *把模块中的所有的都导入,好处是不用再用模块引包了
			<pre>
			from p01 import *
			A=Student('张三',33)
			A.setName()
			say()
			</pre>
		- 对于导入的文件会自动执行函数和类外边的程序
			- 加判断 if  \_\_name\_\_=='\_\_main\_\_'
				- 这里的\_\_name\_\_是当前文件的名，'\_\_main\_\_'是当前文件当做主线程执行的时候(非引入)的文件名称或是包的名称
			- 程序的入口就是被当做主线程巡行的名称(所有的主线程文件的名称都是\_\_main\_\_)
	- 模块的路径
		- 引用包
			<pre>
			import sys			
			sys.path #显示路径
			</pre>
			搜索路径后，把包放在搜到的路径中，如果不想放在搜索到的文件路径中,往sys.path中添加路径  
			sys.path.append(dir)dir为设置的路径
		- 路径的查找顺序
			- 先在内存中查找
			- 搜索python内置模块
			- 搜索sys.path中的路径
		- 包是大于模块，包中是放置模块的文件夹
			- 包大于模块
			- 模块是文件
			- 包是文件夹
		- 项目文件夹的文件
			- 包的结构
				- 每一个包中包含一个\_\_init\_\_.py文件(有且只有一个)
				- 模块文件.py
				- 可以包中嵌套包
		- 包的导入操作
			- import package\_name
				- 直接导入的包可以使用\_\_init\_\_.py中的内容
				- 使用方式
					- package\_name.fun()
					- package\_name.class\_name.fun()
					- 也可以用别名 import packageName as packageNewName
				- 案例01
					- \_\_init\_\_.py文件
					<pre>
					def AA():
					    print('hello world')
					</pre>
					- 调用
					<pre>
					import bao01
					bao01.AA()
					</pre>
				- 案例02，导入包文件
					- import package.module
						- package.module.fun_name
						- package.module.class.fun()
						- package.module.class.var
						- 包内容
						<pre>
						def BB():
						    print('hello world')
						</pre>
						- 调用
						<pre>
						import bao01.bao01
						bao01.bao01.BB()
						</pre>
					- import package.module as pm重命名
					- from ... import
						- from package import module，module01
							- 这种导入方法不执行\_\_init.py\_\_文件
						- from package import *全部导入
							- 导入\_\_init.py\_\_中的所有函数和类
						- from module import *导入包中指定模块的多有内容
						<pre>
						from bao01 import bao01
						bao01.BB()
						</pre>
				
			- 开发环境中的导入包和模块是一样的
				 - import 完整的包货值木块的路径
			- \_\_all\_\_的用法,写在\_\_init\_\_.py中，用于定义那些包导出
				- \_\_all\_\_=['mudule01','module02',...]
				- 使用方法 
				- \_\_init\_\_
				<pre>
				__all__=['pp2']
				def inF():
				    print('this is __init__.py')
				</pre>
				- 调用
				<pre>
				from bao01 import *
				pp2.BB()
				</pre>
		- 命名空间
			- 用去区分不同位置不同功能但是函数或是变量名相同的
			- 放置命名冲突
#### 异常使用 ####
- 异常
	- 错误分为错误和异常
		- 错误指的是人为
		- 异常指语法逻辑正确但是出现问题
		- python中异常时一个类，可以处理和使用
		- 异常分类，异常为系统的异常
		<pre>
		BaseException	所有异常的基类
		SystemExit	解释器请求退出
		KeyboardInterrupt	用户中断执行(通常是输入^C)
		Exception	常规错误的基类
		StopIteration	迭代器没有更多的值
		GeneratorExit	生成器(generator)发生异常来通知退出
		StandardError	所有的内建标准异常的基类
		ArithmeticError	所有数值计算错误的基类
		FloatingPointError	浮点计算错误
		OverflowError	数值运算超出最大限制
		ZeroDivisionError	除(或取模)零 (所有数据类型)
		AssertionError	断言语句失败
		AttributeError	对象没有这个属性
		EOFError	没有内建输入,到达EOF 标记
		EnvironmentError	操作系统错误的基类
		IOError	输入/输出操作失败
		OSError	操作系统错误
		WindowsError	系统调用失败
		ImportError	导入模块/对象失败
		LookupError	无效数据查询的基类
		IndexError	序列中没有此索引(index)
		KeyError	映射中没有这个键
		MemoryError	内存溢出错误(对于Python 解释器不是致命的)
		NameError	未声明/初始化对象 (没有属性)
		UnboundLocalError	访问未初始化的本地变量
		ReferenceError	弱引用(Weak reference)试图访问已经垃圾回收了的对象
		RuntimeError	一般的运行时错误
		NotImplementedError	尚未实现的方法
		SyntaxError	Python 语法错误
		IndentationError	缩进错误
		TabError	Tab 和空格混用
		SystemError	一般的解释器系统错误
		TypeError	对类型无效的操作
		ValueError	传入无效的参数
		UnicodeError	Unicode 相关的错误
		UnicodeDecodeError	Unicode 解码时的错误
		UnicodeEncodeError	Unicode 编码时错误
		UnicodeTranslateError	Unicode 转换时错误
		Warning	警告的基类
		DeprecationWarning	关于被弃用的特征的警告
		FutureWarning	关于构造将来语义会有改变的警告
		OverflowWarning	旧的关于自动提升为长整型(long)的警告
		PendingDeprecationWarning	关于特性将会被废弃的警告
		RuntimeWarning	可疑的运行时行为(runtime behavior)的警告
		SyntaxWarning	可疑的语法的警告
		UserWarning	用户代码生成的警告
		</pre>
		- 异常处理模块语法
		<pre>
		try:
			尝试实现某个操作
		except 异常类型1:
			解决方案1
		except 异常类型2:
			解决方案2
		except (异常类型1,异常类型2...)
			针对多个异常使用相同的处理方式
		except:
			所有异常的解决方案
		else:
			如果没有出现异常，执行此代码
		finally:
			无论有没有出现异常都会执行此代码
		</pre>
		- 对于异常结果的处理
			- 捕获异常后，把异常实例化，异常信息会在实例中，实例化就是把出错的描述返回出来
			- 例如ZeroDivisionError as e中的e就是把ZeroDivisionError的错误信息描述返回出来
			- exit()是退出程序
			<pre>
			try:
			    num = int(input('please:'))
			    print(100 / num)
			except ZeroDivisionError as e:
			    print('分母不能为0')
			    print(e)
			    # 退出程序
			    exit()
			else:
			    print('没有异常')
			finally:
			    print('无论有没有异常都会之行我')			
			</pre>
			- 如果不知道是什么异常，用Exception
				- except Exception as e:
			- 对于写except具体的错误写在前边，如果不知道是什么错误写在后边用Excetion
			- 处理异常的时候，执行到异常处，直接推出程序
			- 所有异常都是集成Exception，Exception包括所有的错误，所以Exception后边不能except，因为Exception会捕获所有的错误
			- 用户手动发生异常，可以使用raise，即为手动发生异常
			- 手动发生异常的错误类型也需要时系统中的异常类型，不能自定义类型，否则会报错
				<pre>
				try:
				    print('执行到此处')
				    raise TypeError
				    print('我应该不会被执行')
				except TypeError as e:
				    print('TypeError类型的错误')
				    exit()
				except UserWarning as e:
				    print('UserWarning类型的错误')
				    exit()
				except Exception as e:
				    print(e)
				    exit()
				finally:
				    print('程序已执行完毕')
				</pre>
			- 自定义异常错误
				- 自定义异常必须是系统异常的子类,是什么异常类型就需要继承什么异常的类
				- 如果在except中没有发现自定义异常类型的类，则会捕获父类的异常类型
				- 关于自定义异常，只要是raise就推荐自定义异常
					- 自定义发生异常的异常代码
					- 自定义发生异常后的提示问题
					- 自定义发生异常的行数
					- 目的，快速定义到出现问题的位置
				<pre>
				class MyError(ValueError):
				    print('ValueError的子类异常')
				try:
				    print('执行到此处')
				    raise MyError
				    print('我应该不会被执行')
				except TypeError as e:
				    print('TypeError类型的错误')
				    exit()
				except MyError as e:
				    print('MyError类型的错误')
				    exit()
				finally:
				    print('程序已执行完毕')
				</pre>
#### 常用包 ####
- 常用模块
	- calendar
		- 日历
		- w=每个日期之间的间隔字符数
		- l=每周所占用的行数
		- c=每个月之间的间隔字符数
		- calendar.calendar(2017),2017年所有
		<pre>
		import calendar
		call=calendar.calendar(2017,w=0,l=0,c=5)
		</pre>
		- isleap判断是否是闰年calendar.isleap(2017)
		- leapdays指定年份之间的闰年的个数calendar.leapdays(2017,3000)
		- month()获取某个月份的字符串calendar.month(2018,3)
		- mothrange表示月份有多少天，calendar.monthrange(2018,3)表示2018年的3月份有多少天
		- mothcalendar(年,月)返回一个也月每天的矩阵，calendar.monthcalendar(2018,3)，二维数组
		- prcal(年)直接打印日历calendar.prcal(2018)，打印一年的日历
		- prmoth(年,月)获取月份
		- weekday(年,月,日)获取周几
	- time
		- 时间戳，1970年到现在
		- utc时间
		- 夏令营
		- 时间元组
		- timezone当前时间和UTC时间差值
		- altzone获取当前时间和UTC时间差值，在夏令时情况下
		- daylight，当前时候是夏令时
		- time()，获取时间戳
		- localtime(),获取本地时间的时间结构time.localtime().tm_hour
		- asctime返回元祖的正常字符串之后的事件格式
		- ctime获取字符串的当前时间
		- mktime()使用时间元祖转为时间戳，时间互换
		- clock获取cpu时间，3.0-3.3版本使用
		- sleep程序进入睡眠时间，即为延迟
		- strftime把元祖转为自定义的字符创
			- %y 两位数的年份表示（00-99）
			- %Y 四位数的年份表示（000-9999）
			- %m 月份（01-12）
			- %d 月内中的一天（0-31）
			- %H 24小时制小时数（0-23）
			- %I 12小时制小时数（01-12）
			- %M 分钟数（00=59）
			- %S 秒（00-59）
			- %a 本地简化星期名称
			- %A 本地完整星期名称
			- %b 本地简化的月份名称
			- %B 本地完整的月份名称
			- %c 本地相应的日期表示和时间表示
			- %j 年内的一天（001-366）
			- %p 本地A.M.或P.M.的等价符
			- %U 一年中的星期数（00-53）星期天为星期的开始
			- %w 星期（0-6），星期天为星期的开始
			- %W 一年中的星期数（00-53）星期一为星期的开始
			- %x 本地相应的日期表示
			- %X 本地相应的时间表示
			- %Z 当前时区的名称
			- %% %号本身
		<pre>
		import time
		print(time.timezone)
		print(time.altzone)
		print(time.daylight)
		print(time.time())
		print(time.localtime())
		print(time.asctime())
		print(time.ctime())
		print(time.mktime(time.localtime()))
		# print(time.clock())
		time.sleep(3)
		print('睡眠过后')
		t=time.localtime()
		d=time.strftime("%Y-%m-%d %H:%M",t)
		print(d)
		</pre>
	- datetime
		- 表示日期
		- data一个理想的日期提供year,month,day属性
		- datetime提供日期和时间的组合
			- today
			- now
			- utcnow
			- fromtimestamp
		- timedelta提供一个时间差，时间长度
		<pre>
		import datetime
		t=datetime.date(2019,10,5)
		print(t)
		print(t.year)
		print(t.month)
		print(t.day)
		from datetime import datetime
		dt=datetime(2019,11,5)
		print(dt.today())
		print(dt.now())
		print(dt.utcnow())
		print(dt.fromtimestamp(time.time()))
		</pre>
	- timeit
		- 时间测量工具
		- timeit.timeit(stmt=fun,number=1000)用于测量程序执行的时间，这里返回出来的是一个时间值
	- os
		- 和操作系统相关的东西
		- 主要是文件操作
		- 主要包含三个模块
		- os，和系统目录相关
		- os.path和系统路径相关
		- shutil高级文件操作，对文件的赋值，删除，移动
		- os
			- os.getcwd()获取当前的工作目录
			- os.chdir()改变当前的工作目录
			- os.lidtdir()获取一个子目录中所有子目录和文件
			- os.makedirs()递归创建文件夹
			<pre>
			import os
			print(os.getcwd()) #获取当前目录
			print(os.listdir()) #获取当前目录中的子目录和文件
			print(os.makedirs('BBB')) #创建文件夹
			os.chdir('F:\python\AAA') #更改当前的工作目录
			print(os.getcwd())
			</pre>
			- os.system()运行系统的shell命令
				- 一般推荐使用subprocess代替
			- getenv()获取指定的系统环境变量值，os.getenv('环境变量值')
			- putenv（）设置环境变量
			- exit()退出当前程序
			<pre>
			import os
			print(os.system("touch ASD.CC"))
			print(os.getenv('PATH'))
			</pre>
			- 值部分
				- os.curdir当前目录
				- os.pardir父目录
				- os.set当前系统的目录分隔符
				- os.linesep当前系统的换行符
				- os.name当前系统名称
				<pre>
				import os
				print(os.curdir)
				print(os.pardir)
				print(os.sep)
				print(os.linesep)
				print(os.name)
				</pre>
		- os.path和路径相关的模块
			- os.path.abspath()将路径转为绝对路径
			- os.path.abselute绝对路径
			- os.path.basename()获取路径中的文件名部分
			- os.path.join(路径1，路径2)
			- os.path.split('文件件路径/文件')切割文件路径中的路径和当前文件
			- os.path.isdir('路径')判断是否是目录
			- os.path.exists()检测文件或是目录是否存在
			<pre>
			import os.path as op
			print(op.abspath('.'))
			print(op.basename('F:\python'))
			p=op.join('path01/AA','path02.txt')
			print(p)
			print(op.split(p))
			print(op.isdir('adf/adsf'))
			print(op.exists('F:\python\AAA'))
			</pre>
	- shutil
		- 常用的文件模块
		- shutil.copy('源文件路径','目标文件路径')复制文件
		- shutil.copy2('源文件路径','目标文件路径')复制文件，尽量保留源文件的元数据
		- shutil.copyfile('源文件路径','目标文件路径')将一个文件中的内容复制到另一个文件中去
		- shutil.move('源文件路径','目标文件路径')移动文件/文件件
		<pre>
		import shutil
		shutil.copy('F:\python/box.py','F:\python\AAA')
		shutil.copyfile('F:\python/copy.html','F:\python\AAA\A.html')
		shutil.move('F:\python/copy.html','F:\python\AAA')
		</pre>
		- 归档和压缩
			- 归档:把多个文件或是文件夹合并到一个文件中
			- 压缩:用算法把文件或是文件夹合并到一个问价中
			- shutil.make_archive('归档之后的文件名或是目录','后缀','需要归档的文件夹')归档操作
			- shutil.unpack_archive('解包的文件地址','解包后的文件地址')解包操作
			<pre>
			import shutil
			shutil.make_archive('F:\python\ABC','zip','F:\python\AAA') #压缩文件
			shutil.unpack_archive('F:\python\ABC.zip','F:\python\BBB')
			</pre>
		- zip-压缩包
			- zipfile.ZipFile('压缩包的路径')实例化
			- zipfile.ZipFile('压缩包的路径').getinfo(name)获取压缩的内容
			- zipfile.ZipFile('压缩包的路径').nameList()获取压缩内的文件名
			- zipfile.ZipFile('压缩包的路径').extractall()解压缩
			<pre>
			import zipfile
			zf=zipfile.ZipFile('F:\python\ABC.zip')
			print(zf.getinfo('A.html'))
			print(zf.namelist())
			zf.extractall('F:\python\CCC')
			</pre>
	- random
		- 随机模块，伪随机
		- random.random()生成随机数
		- random.choice()随机选择数列中的某个值
		- random.shuffle()随机打乱列表，打乱的是原来的列表
		- random.randint(0,100)随机产生一个整数(0到100)，包含0和100
		<pre>
		import random
		print(random.random())
		print(int(random.random()*100))
		l=[i for i in range(10)]
		print(l)
		print(random.choice(l))
		l1=random.shuffle(l)
		print(l)
		print(random.randint(0,20))
		</pre>
	- zio
	- math
	- string
	- 上述引用的模块需要先导入，string是特例
#### 函数式编程 ####
- 高级特性
- 基于lambda盐酸的一种编程方式
	- 程序中只有函数
	- 函数可以作为参数，同样可以作为返回值
	- 纯函数式编程:lisp,Haskell
- 函数
	- 高阶函数
	- 返回函数
	- 匿名函数
	- 装饰器
	- 偏函数
- lambda表达式
	- 最大程度上服用代码
	- 匿名函数
	- 一个表达式，函数体相对简单
	- 仅仅是一个表达式
	- 用法
		- 以lambda开头
		- 紧跟一定的参数
		- 参数后用冒号和表达式主题隔开
		- 只有一个表达式
		<pre>
		num=lambda i:i*20
		print(num(20))
		sum=lambda a,b,c:a+b*2+c*3
		print(sum(1,2,3))
		</pre>
	- 递归函数
- 高阶函数
	- 把函数作为参数的使用的函数
	- 高阶函数就是javascript的回调函数
	<pre>
	def AA():
	    setName='张三'
	    return setName
	def BB(callback):
	    getName=callback()
	    print(getName)
	BB(AA)
	def A(n):
	    return n*10
	def B(m,f):
	    return f(m)*30
	print(B(2,A))
	</pre>
- 系统高阶函数-map
	- 愿意就是映射，把集合或是列表都进行操作，从而得到新的集合
	- map返回一个迭代对象
	- map(fun,list),map是一个类，迭代完成后还是一个map对象，需要用for循环输出迭代后的值
	<pre>
	l=[i for i in range(10)]
	def C(n):
	    return n*10
	l2=map(C,l)
	for i in l2:
	    print(i)
	</pre>
- reduce
	- 愿意是归并，缩减
	- 把一个可迭代的对象归并成一个结果
	- 参数：两个参数，必须有返回结果
	- reduce()
	- 需要应用functool包
	<pre>
	from functools import reduce
	l=[i for i in range(10)]
	def sum(a,b):
	    return a+b
	getSum=reduce(sum,l)
	print(getSum)
	</pre>
- filter
	- 对一组数据进行过滤
	- 和map比较
		- 相同：都对每一个元素注意进行操作
		- 不同
			- map生成新的数列和原数列是一对一的
			- filter是过滤，符合调价的留下
	- 利用给定的函数就行判断
	- 返回值是一个布尔值
	- filter(f,data),参数分别问过滤函数、数列，生成的新的数列是一个filter类，如果要数列的数据，需要循环
	<pre>
	l=[i for i in range(10)]
	def setNumber(n):
	    return n%2==0
	num=filter(setNumber,l)
	for i in num:
	    print(i)
	</pre>
- 高阶函数-排序
	- 把一个序列按照给定的方法进行排序
	- sorted(list,reverse=True)倒序
	<pre>
	l=[99,23,6,-565,69,-5,3,2,1]
	l1=sorted(l)
	l2=sorted(l,key=abs,reverse=True)
	print(l1)
	print(l2)
	</pre>
- 返回函数
	- 可以返回一个具体的值，也可以返回一个函数
	- 例子如下，同时如下的例子也是一个闭包函数
	<pre>
	def f1(*args):
	    def f2():
	        sum=0
	        for i in args:
	            sum+=i
	        return sum
	    return f2
	f=f1(1,2,3,4,5,6)
	print(f())
	</pre>
- 闭包函数
	- 问题，返回闭包时，返回函数不能引用任何循环变量
	<pre>
	def count():
	    fs=[]
	    for i in range(1,4):
	        def A():
	            return i*i
	        fs.append(A) #fs中添加的是A函数，只是添加进去，现在并不立即执行
	    return fs #把列表返回，这里的列表中是三个方法，但是这三个方法是不能用for循环的
	f1,f2,f3=count() #把返回的列表中的三个函数分别赋值给f1,f2,f3
	print(f1()) #在调用的时候此时的i为3
	print(f2()) #在调用的时候此时的i为3
	print(f3()) #在调用的时候此时的i为3
	</pre>
	- 解决方法
	<pre>
	def count():
	    def f(n):
	        def A():
	            return n*n
	        return A    #这里返回的方法，并且此时方法内部的参数的运算已经完成
	    fs=[]
	    for i in range(1,4):
	        fs.append(f(i)) #fs中添加进去的是三个方法，但是方法中的运算已经完成，此时只剩输出
	    return fs   #返回列表中的方法
	f1,f2,f3=count()
	print(f1()) #在没有运行该方法之前，方法内部的运算已经完成，这里的调用只是把方法内部的值输出
	print(f2())
	print(f3())
	</pre>
- 装饰器
	- 在当前的函数上增加新的需求，不改变原有的代码
	- 一个返回函数的高阶函数
	- 装饰器的使用:使用@语法，在每次要扩展的方法前边定义使用@+函数名
	- 装饰器可以多次使用
	- 装饰器的理解，定义一个需求，可以多次使用，虽说往装饰器中添加新的需求，但是同一个装饰器的不同地方调用是相互不影响的(有点像javascript的封装)。
	- 装饰器的写法一般固定
	- 第一种写法
	<pre>
	def A(f): #高阶函数，参数为一个函数，这里的参数可以认为是整个方法的一个中间变量
	    def newA(*args,**kwargs):#这个方法是写需求的方法
	        print('this is function newA')  #初始时候的要执行的方法
	        return f(*args,**kwargs)    # 这里是返回的参数函数，
	    return newA
	# 调用
	@A
	def DA():
	    print('这是一个新添加的需求')
	DA()
	@A
	def EA():
	    print('this is a new EA')
	EA()
	</pre>
	- 理解：A函数是一个外层的过度函数，起一个返回实际需求newA的作用；newA是实际要执行的方法，实际上整个方法裸露出来的是
	<pre>
	print('this is function newA')
	return f(*args,**kwargs)
	</pre>
	- 或是说是真正执行的是这一部分，return返回出来的函数是拓展要添加的函数
	- 第二种写法
	<pre>
	def A(f): #高阶函数，参数为一个函数，这里的参数可以认为是整个方法的一个中间变量
	    def newA(*args,**kwargs):#这个方法是写需求的方法
	        print('this is function newA')  #初始时候的要执行的方法
	        return f(*args,**kwargs)    # 这里是返回的参数函数，
	    return newA
	# 调用
	#第二种调用方法
	def EA():
	    print('第二种调用方法')
	EA=A(EA)
	EA()
	</pre>
	- EA=A(EA)理解：简单讲就是把EA方法穿进去，然后把EA的方法和装饰器的方法一起返回出来，然后再赋值给EA
- 偏函数
	- 参数固定的函数，相当于一个由特定参数的函数体
	- 需要用的包functool中的partial
	<pre>
	import functools
	int16=functools.partial(int,base=16)
	print(int16('20')) 
	</pre>
#### 高级语法 ####
- 高级函数
	- zip，把多个可迭代数列合并成tuple元素类型
	<pre>
	l1=[1,2,3,4,5]
	l2=[1,2,3,4,5]
	print(zip(l1,l2))
	for i in zip(l1,l2):
	    print(i)
	</pre>
	- enumerate
		- 和zip相似
		- 对可迭代对象里的每一个元素配上一个索引
		- 迭代的索引是从0开始
		- enumerate(l1，start=100)设置从100开始
		<pre>
		l1=[22,33,6,5,2,8,5]
		for i in enumerate(l1):
		    print(i)
		</pre>
	- collections模块
		- namedtuple
			- tuple类型
			- 可命名的tuple
			- 理解：使用方法类似于javascript的对象和数组
			- tuple新型的数据结构
			- 设置数组的时候Point(12,23)，为设置当前的p的数据，非数据列表
			<pre>
			import collections
			Point=collections.namedtuple('Point',['x','y'])
			p=Point(12,23)
			print(p.x)
			print(p[0])
			</pre>
		- deque
			- 队列表的数据的操作
			<pre>
			from _collections import deque
			q=deque(['a'])
			q.append('b')
			q.appendleft('c')
			print(q)
			</pre>
		- defaultdict
			- 当直接读取dict不存在的属性时，直接返回默认值
			<pre>
			from _collections import defaultdict
			fun=lambda :'this is none'
			d=defaultdict(fun)
			d['one']=1
			print(d['one'])
			print(d['two'])
			</pre>
		- Counter
			- 统计字符串的个数
			- 字符串的字符是可迭代的
			- 不仅仅是字符串，也可以是列表
			<pre>
			from collections import Counter
			c=Counter('abcdefg hello world')
			print(c)
			</pre>
- 调试
	- 调试流程:单元调试->集成测试->交测试
	- 分类
		- 静态调试
		- 动态调试
	- pdb调试
	- pycharm调试
		- run/debug模式
	- 单元测试
- file
	- 文件，长久保存信息的一种数据信息集合
	- 常用操作
		- 打开
			- open(r'文件的路径和名称','打开方式')
			- 参数r表示字符串后边的内容不需要转义
			- 打开方式
				- r:只读方式打开文件
				- w:写方式打开，会覆盖以前的内容
				- x:创建方式打开，如果文件已经存在，报错
				- a:append方式，追加文件
				- b:binary方式，以二进制方式写入
				- t:文本方式打开
				- +：可读写
				<pre>
				f=open('F:\python\CCC\A.html','w')
				f.close()
				</pre>
		- 关闭
			- f.close()
	- width语句，会给自动关闭(推荐使用)
		- 自动判断文件袋作用域，会自动关闭不使用的文件
		- 使用方式不需要close关闭文件
		<pre>
		with open(r'F:\python\CCC\A.html','w') as f:
		    pass
		</pre>
		<pre>
		with open(r'F:\python\CCC\test.txt', 'r') as f:
		    strline = f.readline()
		    while strline:
		        print(strline)
		        strline = f.readline()
		</pre>
		- list
			- list能用打开的文件作为参数，把文件的内的每一行内容作为一个元素
			- 简单理解就是把每一行作为一个参数存入到list中的，然后再循环list使用数据
			<pre>
			with open(r'F:\python\CCC\test.txt', 'r') as f:
			    strline=list(f)
			    for i in strline:
			        print(i)
			</pre>
		- read
			- 按照文件字符读取内容
			- 允许输入参数决定读取的字符个数
			<pre>
			with open(r'F:\python\CCC\test.txt', 'r') as f:
			    strline=f.read()
			    print(strline)
			</pre>
			<pre>
			with open(r'F:\python\CCC\test.txt', 'r') as f:
			    strline=f.readline()
			    while strline:
			        print(strline)
			        strline = f.readline()
			</pre>
		- seek(offset,from)
			- 参数(偏移到哪儿,从哪儿开始偏移)
			- 移动文件的读取位置，也叫读取的指针
			- 从第几个字符处开始往后读取，单位是字节
			- from的取值范围
				- 0：从文件开头开始偏移
				- 1：从文件当前位置开始偏移
				- 2：从文件末尾开始偏移
		- tell是获取当前的指针的位置
			<pre>
			with open(r'F:\python\CCC\test.txt', 'r') as f:
			    str=f.read(3)
			    pos=f.tell()
			    while str:
			        print(str)
			        print(pos)
			        pos = f.tell()
			        str = f.read(3)
			</per>
		- 练习
			- 读取文件三个字符一组
			<pre>
			with open(r'F:\python\CCC\test.txt', 'r') as f:
			    str=f.read(3)
			    while str:
			        print(str)
			        str = f.read(3)
			</pre>
	- 文件的写入操作(不存在删除，拷贝)
		- write
			- write(str)把字符串写入文件
			- writeline(str)把字符串按行写入文件
			- 区别
				- wirte函数参数只能是字符串
				- writeline参数可以是字符串，也可以是字符序列
				<pre>
				with open(r'F:\python\CCC\w.txt', 'w') as f:
				    f.write('山东省\n')
				    f.write('济南市\n')
				    f.write('历城区\n')
				    f.writelines('山东省\n')
				    f.writelines('济南市\n')
				    f.writelines('历城区\n')
				    l=['this','is','shandong']
				    f.writelines(l)
				</pre>
- pickle
	- 序列化(持久化，就是把数据写到硬盘上)，把程序运行中的信息保存到硬盘上
	- 反序列化，把硬盘上的数据读取到程序中
	- pickle：python提供的序列化模块
	- pickle.dump序列化（数据的实时存储，一般不用文件）
	- pickle.load反序列化
	- 简单理解就是数据的读取和存入
	<pre>
	import pickle
	age=100
	with open(r'F:\python\CCC\123.txt','wb') as f:
	    pickle.dump(age,f)
	</pre>
	<pre>
	import pickle
	age=100
	with open(r'F:\python\CCC\123.txt','rb') as f:
	    print(pickle.load(f))
	</pre>

- 持久化-shelve
	- 和字典类似
	- open
	- close
	<pre>
	import shelve
	# shelve写入
	shv=shelve.open(r'shv.db')
	shv['one']='this is first'
	shv['two']='this is second'
	shv.close()
	# 读取
	shvG=shelve.open(r'shv.db')
	print(shvG['one'])
	print(shvG['two'])
	shvG.close()
	</pre>
	- 一般使用 try和finally
	<pre>
	shvG=shelve.open(r'shv.db')
	try:
	    print(shvG['one'])
	    print(shvG['two'])
	finally:
	    shvG.close()
	</pre>
	- shelve特性
		- shelve指定的是一种.db格式的数据
		- 不支持多个应用并行写入
			- 但是支持多个应用程序的读取，flag=r
			<pre>
			import shelve
			shvG=shelve.open(r'shv.db',flag='r')
			try:
			    print(shvG['one'])
			    print(shvG['two'])
			finally:
			    shvG.close()
			</pre>
		- 写回问题
			- 就是覆盖
			- 强制写回 writeback=True
			- 强制写回的是在修改数据的在关闭的文件的时候会去检测文件的内容是否发生更改，如果发生更改则进行修改，如果不加writeback=True，则不会自动去监测文件是否发生更改
			- 这里的写回问题指的是字典中的二级数据，对于一级数据不存在这样的问题
			<pre>
			#写入
			import shelve
			shvA=shelve.open(r'shv.db')
			try:
			    shvA['one']={'name':'hello world','age':'20'}
			finally:
			    shvA.close()
			# 更改
			shvB=shelve.open(r'shv.db',writeback=True)
			try:
			    shvB['one']['name']='山东省'
			finally:
			    shvB.close()
			# 读取
			shvC=shelve.open(r'shv.db')
			try:
			    print(shvC['one'])
			finally:
			    shvC.close()
			</pre>
- Log
	- 日志
	- 把日志写到磁盘上
	- logging模块
	- 日志相关概念
		- 级别
			- 不同的的用户关注不同的信息
			- DEBUG
			- INFO
			- NOTICE
			- WARNIBG
			- ERROR	到该级别，介入
			- CRITICAL	程序停止
			- ALERT
			- EMERGENCY
	- Log的作用
		- 调试
		- 了解软件的运行状况
		- 确定问题
	- 日志信息
		- time时间
		- 哪个类，地点
		- 级别level
		- 内容，错误内容
	- 第三方日志
		- log4j
		- log4php
		- logging
	- Logging模块
		- 初始化/日志需要制定级别
		- 使用方式
			- logging，封装了其他的组件
			- loging四大组件
	- logging模块级别日志
		- logging.debug(msg,\*args,**kwargs)创建一条严重级别为debug的日志
		- logging.info(msg,\*args,**kwargs)创建一条严重级别为info的日志
		- logging.warning(msg,\*args,**kwargs)创建一条严重级别为warning的日志
		- logging.error(msg,\*args,**kwargs)创建一条严重级别为error的日志
		- logging.critical(msg,\*args,**kwargs)创建一条严重级别为critical的日志
		- logging.log可以替代上边的五种日志
		- logging.log(level,\*args,**kwargs)创建一条严重级别为level的日志
		- logging.basicConfig(**kwargs)对root logger进行一次性配置
			- 只在第一次配置的时候起作用
			- 不配置logger使用默认信息
				- 输出sys.stderr
				- 级别WARNING
				- 格式level:log_name:content

		- 不进行配置的时候，低于warning级别的警告是不会显示
		- 两种用法如下，配置文件的设置可以设置log输出的文件，和log的级别，默认的级别的warning
		<pre>
		import logging
		logging.basicConfig(filename='python.log',level=logging.DEBUG)
		logging.debug('0this is debug')
		logging.info('0this is info')
		logging.warning('0this is warning')
		logging.error('0this is error')
		logging.critical('0this is critical')
		logging.log(logging.DEBUG,'this is debug')
		logging.log(logging.INFO,'this is info')
		logging.log(logging.WARNING,'this is warning')
		logging.log(logging.ERROR,'this is error')
		logging.log(logging.CRITICAL,'this is critical')
		</pre>
		- 自定义配置
		- Log_config="%(asctime)s====%(levelname)s++++%(message)s"里边的格式是basicConfig的配置参数定义的格式
		<pre>
		import logging
		Log_config="%(asctime)s====%(levelname)s++++%(message)s"
		logging.basicConfig(filename='python.log',level=logging.DEBUG,format=Log_config)
		logging.debug('0this is debug')
		logging.info('0this is info')
		logging.warning('0this is warning')
		logging.error('0this is error')
		logging.critical('0this is critical')
		logging.log(logging.DEBUG,'this is debug')
		logging.log(logging.INFO,'this is info')
		logging.log(logging.WARNING,'this is warning')
		logging.log(logging.ERROR,'this is error')
		logging.log(logging.CRITICAL,'this is critical')
		</pre>
		- basicConfig的format的参数参数有多个
	- logging默认的处理流程
		- 四大组件
			- 日志器(Logger)：生产日期的接口
			- 处理器(Handler)：把产生的日志放到相应的目的地
			- 过滤器(Filter):更精细的控制日志
			- 格式器(Formatter)：对输出的信息进行格式化
		- 四大组件的整合
			- 出现的告警信息太多，会直接保存到本地，然后发送到相应的人和位置；
			- 四大组件的作用是把相应的数据做相应的处理，然后把信息发送给相应的对象(让该看到的人看到该看到的信息)
		- Logger
			- 产生一个日志
			- 操作
				- Logger.setLevel()设置日志的需要处理的最低级别
				- Logger.addHandler(),Logger.removeHander()添加和移除处理器
				- Logger.addFilter(),Logger.removeFilter()添加和移除过滤器
				- Logger.debug()产生一个debug级别的日志
				- Logger.exception()创建类似于Logger.error的日志消息
				- Logger.log()获取一个明确的日志level参数类创建一个日志
			- 如何得到一个logger，产生一个日志
				- 实例化
				- logging.getLogger()
		- Handler
			- 把log发送到指定的位置
			- 方法
				- setLevel设置界别
				- serFormat设置参数，即为日志的格式
				- addFilter,removeFilter删除或是添加顾虑器
			- 不需要直接使用，Handler是基类
		- Format类
			- 直接实例化
			- 可以继承Format添加特殊内容
			- 三个参数
		- Filter类
			- 可以被Hander和Logger使用
			- 控制传递过来的具体内容
	- 案例待补充......
#### 多线程 ####
- 多线程 VS 多进程
	- 进程：程序运行的一种状态
		- 包含地址空间、内存、数据栈
		- 每个进程有一个单独的运行环境，过个运行程序之间互不干扰。
	- 线程
		- 一个进程的独立运行的片段，一个进程可以由多个片段组成（一个进程有多个线程）
		- 轻量化的进程
		- 共享互斥问题
	- 全局解释器锁 
	- python的伪多线程
		- 多线程是指一个程序中多个代码片段相互运行互不干扰
			- 举例：厨房中两个人同时在做饭，做饭的工具需要有两套，互不干扰
		- 伪多线程是也是指一个程序中多个代码片段运行互不干扰，但是要有一定的条件
			- 举例：厨房中两个人同时在做饭，但是做饭的工具只有一套，两个人在做饭的时候使用的工具就会有冲突，需要岔开使用，在此条件上互不干扰
	- python
		- thread有问题，不好用，python3中改成了_thread
		- threading,一般用这个包
		- 使用
			- 案例，不使用多线程
			<pre>
			import time			
			def loop1():
			    print('time01', time.ctime())
			    time.sleep(4)
			    print('time01', time.ctime())			
			def loop2():
			    print('time02', time.ctime())
			    time.sleep(4)
			    print('time02', time.ctime())			 
			def main():
			    print('main-time', time.ctime())
			    loop1()
			    loop2()
			    print('main-time', time.ctime())			
			main()
			</pre>
			- 案例，使用thread
				- 出现的问题是，在main方法中分出去的两个线程，分别执行相应从程序后，里边有延时装置的时候，延时装置后边的代码会被停掉，也就是print('loop1-02:', time.ctime())和print('loop2-02:', time.ctime())不会被执行
			<pre>
			import _thread as thread
			import time			
			def loop1():
			    print('loop1-01:', time.ctime())
			    time.sleep(4)
			    print('loop1-02:', time.ctime())			
			def loop2():
			    print('loop2-01:', time.ctime())
			    time.sleep(4)
			    print('loop2-02:', time.ctime())			
			def main():
			    print('main01:', time.ctime())
			    thread.start_new_thread(loop1,()) #方法、方法的参数
			    thread.start_new_thread(loop2,())
			    print('main02:', time.ctime())			
			main()
			</pre>
			- 案例，解决上边的为题
				- 代码中的演示器会被结束，是因为主线程已经结束，解决办法是，让主线程实时监测，如果没有执行完的代码，要实时监测执行
			<pre>
			import _thread as thread
			import time			
			def loop1():
			    print('loop1-01:', time.ctime())
			    time.sleep(4)
			    print('loop1-02:', time.ctime())			
			def loop2():
			    print('loop2-01:', time.ctime())
			    time.sleep(4)
			    print('loop2-02:', time.ctime())			
			def main():
			    print('main01:', time.ctime())
			    thread.start_new_thread(loop1,()) #方法、方法的参数
			    thread.start_new_thread(loop2,())
			    print('main02:', time.ctime())			
			if __name__=='__main__':
			    main()
			    while True:
			        time.sleep(1)
			</pre>













<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<hr/>
# 课时44#
<hr/>
