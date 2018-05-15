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
8.创建django工程
```
	django-admin startproject 名称
```
	修改setting里面的编码   LANGUAGE_CODE = 'zh-hans'
							TIME_ZONE = 'Asia/Shanghai'

9.启动Django项目
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

10.配置相关的文档
	__init__.py:初始化
	admin.py 后台注册模型
	settings.py 配置信息，如databases等。
	urls.py：url路由
	wsgi.py：网关

11.创建app
	python manage.py startapp app

12.配置
	在settting.py文件中installed_app中写入app的name

13.模型modle
	在modles.py中定义class模型名称继承models.Model
	db_tables:定义数据库中的表名称

14.迁移
	python manage.py makemigrations 生成映射文件
	python manage.py migrate 执行映射文件

15.保存数据
	stu = Student()
	stu.name = 'xxx'
	stu.save()

16.创建admin用户
	python manage.py createsuperuser

17.ORM 对象关系映射，翻译机

18.模型字段
```
	CharField: 字符串
	BooleanField：布尔类型
	DateField: 年月日
		auto_now_add: 第一次创建时候赋值
		auto_now: 每次修改的时候
	DataTimeField：年月日 时分秒
		auto_now_add
		auto_now


	AutoField: 自动增长
	DecimalField:
    	models.DecimalField(max_digits=3, decimal_places=1)
		max_digits:总位数
		decimal_places:小数后有几位


	TextField:存文本信息
	IntegerField:整数
	FloatField:浮点


	FileField:文件上传字段
	ImageField:上传图片
		upload_to=''指定上传图片的路径
```
19.模型参数
	default:默认
	null: 设置是否为空，针对数据库中的字段(True/False)
	blank：设置是否为空，针对表单提交的信息(True/False)
	primary_key:创建主键(True/False)
	unique:是否唯一(True/False)

20.post -- 提交数据隐藏了
  get -- 提交数据在url上, ?后跟参数，&用来连接多个参数，但是对参数的数量有限制，每个浏览器的限制不同
  put 更新全部数据
  patch 更新局部数据
  delete:删除数据
  example:  stu_id = request.GET.get('stu_id')
            Student.objects.filter(id=stu_id).delete()

21.cokie
	cookie:在浏览器
	session:在服务器
	set_cookie(key, value,max_ages,)
	del_cookie()
	牌有过期时间，可以设置并存放在mysql或mongodb
     1）绑定令牌到cookie里面，并将cookie存在前端
        ticket = 'lalala'
        response = HttpResponse()
        response.set_cookie('ticket',ticket)
        return response
     2）cookie存在数据库中
        user.u_ticket = ticket
        user.save()
     3）从浏览器及数据库中删除cookie
		response = HttpResponseRedirect("/shopapp/login/")
		   ticket = request.COOKIES.get("ticket")
		   response.delete_cookie("ticket")
		   UserSession.objects.get(session_data=ticket).delete()
		   return response

22.Ajax
	前端JS
	function add(){
	    csrf = $('input[name="csrfmiddlewaretoken"]').val();
	    s_name = $('#s_name').val();
	    s_tel = $('#s_tel').val();
	    $.ajax({
	        url:'/stuapp/student/',
	        type:'POST',
	        data:{'s_name':s_name,'s_tel':s_tel},  //向后端传递数据，以字典的形式
	        dataType:'json',
	        headers:{'X-CSRFToken':csrf},
	        success:function (msg) {
	            alert('添加成功')  
	        },
	        error:function () {
	            alert('添加失败')
	        }
	    });
	}
	前端HTML页面
	{% csrf_token %}

	后端逻辑处理函数
	JsonResponse(data)  data不能是QuerySet

	-- form表单提交(POST) 删除(DELETE) 局部更新(PATCH)
	1)开启中间件django.middleware.csrf.CsrfViewMiddleware
	2){% csrf_token %},等同如下:
	<input type='hidden' name='csrfmiddlewaretoken' value='duRoaLbyewAO7aLxV0HZyOWB9npPqLs01a27Y3nnqg2h8lTJjkcQdeiKzfpZJdX0' />
	3)(ajax之外用不到
	)csrf = $('input[name="csrfmiddlewaretoken"]').val()
	  headers:{'X-CSRFToken': csrf}


model操作
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
		
```

mvt的运行流程(个人理解)

1 用户进入页面通过点击确定其操作（urls）
2 通过urls中的url进入对应的views控制层对应的方法
3 通过views的方法操作model中的数据  model对应数据库
4 将数据返回给用户层（templates）