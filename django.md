1.MVC(model, view, controller)
   MVC框架的核心:解耦
   降低各功能模块之间的耦合性，方便变更，更容易重构代码，最大程度上实现代码的重用
   model：数据库层的封装
   view：向用户展示结果
   controller：处理请求，获取数据，返回结果
2.MVT(modle, view, template)
   mvt中的v t相当于mvc中的c v
   ![mvt流程图]()
3.B/S 浏览器/服务器
  C/S 客服端/服务器
4.安装虚拟环境
  pip install virtualenv
5. 在env文件夹中安装虚拟环境
```
	cd env
	virtualenv --no-site-packages testenv(如果版本只有一个3.x的)、
	virtualenv --no-site-packages -p 路径 testenv(指定安装的版本)
```
6.进入虚拟环境
	cd testenv\Scripts>activate
	现在就可以安装我们需要的库了
	deactivate 退出虚拟环境
7.安装django
```
	pip install django==1.11
```
8.创建项目
```
	django-admin startproject 名称
```
	修改setting里面的编码   LANGUAGE_CODE = 'zh-hans'
							TIME_ZONE = 'Asia/Shanghai'

11.启动Django
```
	python manage.py runserver
	python manage.py runserver ip:端口号
```
	本机配置pycharm的runserver
	Run>Debug>Edit configurations> python 
	name : hello(自定义)
	script path：D:\workspase\helloworld\manage.py(我的路径)
	Parameters：runserver 8080
	建好之后apply一下

12.创建app
	python manage.py startapp app

13.配置相关的文档
	__init__.py:初始化
	admin.py 后台注册模型
	apps.py settings.py 里面注册app的时候需要使用到INSTALLED_APPS即将创建的app添加到其中。
14.在新建的app中新建一个urls.py文件

15.配置项目中的urls

16.model操作
```
	1.将settings.py中的
	DATABASES={
		# 连接数据库
		'default': {
        	'ENGINE': 'django.db.backends.mysql',
        	'HOST': 'localhost',
        	'USER': 'root',
        	'PASSWORD': 'root',
        	'PORT': '3306',
        	'NAME': 'firsthello',
    	}
	}
	2.在stu中的models中创建实体即数据库中的表结构例如：
		class Student(models.Model):
			# 创建表中的字段
    		name = models.CharField(max_length=20)
    		sex = models.BooleanField()
    		class Meta:
    		# 指定表的名字
        		db_table = 'stu'
	3.在虚拟环境中分别执行:
		python manage.py makemigrations 生成映射文件
		python manage.py migrate 执行映射文件
```

mvt的运行流程 

1 用户进入页面通过点击确定其操作（urls）
2 通过urls中的url进入对应的views控制层对应的方法
3 通过views的方法操作model中的数据  model对应数据库
4 将数据返回给用户层


