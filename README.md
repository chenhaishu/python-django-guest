# python-django-guest
基于python django框架的访客登记签到功能

环境安装部署步骤
1、安装python软件，推荐python3版本，python下载的路径如下。当前20200204 python3最新版本为3.9.0
https://npm.taobao.org/mirrors/python/3.9.0/

2、安装完python3后进入cmd命令行使用pip的方式安装django的库,pypi的源可以使用清华的镜像源，速度比较快
pip install django https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple/

3、安装python IED开发环境pycharm，pycharm分为两个版本，社区版和专业版，其中社区版本是免费的，专业版是收费的且支持django项目创建。
pycharm安装教程(仅供参考)
https://www.cnblogs.com/dcpeng/p/9031405.html

--------------
将guest2的mysql替换成默认数据库的操作：
1、 执行python.exe .\manage.py runserver报错如下：
  File "<frozen importlib._bootstrap>", line 219, in _call_with_frames_removed
  File "D:\Source\django-guest\guest2\guest2\__init__.py", line 1, in <module>
    import pymysql
ModuleNotFoundError: No module named 'pymysql'
  将guest2\guest2\__init__.py文件中的mysql相关的屏蔽掉，再次执行runserver命令
  
2、提示报错如下：
  File "<frozen importlib._bootstrap>", line 1006, in _gcd_import
  File "<frozen importlib._bootstrap>", line 983, in _find_and_load
  File "<frozen importlib._bootstrap>", line 965, in _find_and_load_unlocked
ModuleNotFoundError: No module named 'bootstrap3'
  安装前端库bootstrap3,pip install -i https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple/ django-bootstrap3
  
3、报错如下：
  File "D:\Source\django-guest\guest2\sign\views\views_api_sec.py", line 9, in <module>
    from Crypto.Cipher import AES    # 请安装 Crypto
ModuleNotFoundError: No module named 'Crypto'
  安装pip install -i https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple/  pycryptodome
  
4、至此可以正常运行，提示如下：
PS D:\Source\django-guest\guest2> python.exe .\manage.py runserver
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).

You have 4 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, sign.
Run 'python manage.py migrate' to apply them.
February 04, 2020 - 11:13:27
Django version 2.2.7, using settings 'guest2.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.

浏览器打开http://127.0.0.1:8000/，可以查看到登录界面

上面提示进行migration,执行如下：
PS D:\Source\django-guest\guest2> python manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions, sign
Running migrations:
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying auth.0010_alter_group_name_max_length... OK
  Applying auth.0011_update_proxy_permissions... OK
  Applying sign.0002_auto_20190310_1848... OK
PS D:\Source\django-guest\guest2>

5、创建admin登录用户名密码
PS D:\Source\django-guest\guest2> python.exe .\manage.py changepassword admin
Changing password for user 'admin'
Password:
Password (again):
Password changed successfully for user 'admin'
PS D:\Source\django-guest\guest2>
PS D:\\Source\django-guest\guest2> python.exe .\manage.py runserver
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
February 04, 2020 - 11:20:31
Django version 2.2.7, using settings 'guest2.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.

至此使用amdin账户以及刚创建的密码可以登录到发布系统。
