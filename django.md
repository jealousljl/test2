MVC(model, view, controller)

MVC框架的核心:解耦

降低各功能模块之间的耦合性，方便变更，更容易重构代码，最大程度上实现代码的重用

model：数据库层的封装

view：向用户展示结果

controller：处理请求，获取数据，返回结果

MVT(modle, view, template)

mvt中的vt相当于mvc中的cv

![mvt流程图](C:\Users\Administrator\Desktop\Python\上课截图\django\mvt流程图.png)

B/S 浏览器/服务器

C/S 客服端/服务器

安装虚拟环境

pip install virtualenv

在env文件夹中安装虚拟环境

```
cd env

virtualenv --no-site-packages testenv(如果版本只有一个3.x的)、

virtualenv --no-site-packages -p 路径 testenv(指定安装的版本)

```
进入虚拟环境

cd testenv\Scripts>activate

现在就可以安装我们需要的库了

deactivate 退出虚拟环境

安装django

```

pip install django==1.11

```

创建项目

```

django-admin startproject 名称

```

修改setting里面的编码  为 zh-hands

```

python manage.py runserver 运行项目 启动服务器

```

makemigrations 生成映射文件

migrate 执行映射文件
makemigrations 生成映射文件
migrate 执行映射文件
