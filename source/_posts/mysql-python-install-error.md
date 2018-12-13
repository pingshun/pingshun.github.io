---
title: macOS下安装mysqlclient和mysql-python提示'mysql_config not found'错误
date: 2018-12-13 17:05:18
tags: [maxOS, mysql]
---

前提:
mac没有安装mysql的server端,只想安装client端利用mysql-python连接远程的mysql服务器。

错误:
用 'pip install mysql-python',安装时提示'mysql_config not found'错误:
<!--more-->

    Collecting mysql-python
    Downloading MySQL-python-1.2.5.zip (108kB)
    100% |████████████████████████████████| 110kB 30kB/s 
    Complete output from command python setup.py egg_info:
    sh: mysql_config: command not found
    Traceback (most recent call last):
      File "<string>", line 20, in <module>
      File "/private/tmp/pip-build-NP8J3v/mysql-python/ setup.py", line 17, in <module>
        metadata, options = get_config()
      File "setup_posix.py", line 43, in get_config
        libs = mysql_config("libs_r")
      File "setup_posix.py", line 25, in mysql_config
        raise EnvironmentError("%s not found" %     (mysql_config.path,))
    EnvironmentError: mysql_config not found

解决:
1. brew install mysql-connector-c
2. 找到 mysql_config 文件: which mysql_config
3. 编辑这个mysql_config文件:
    找到这行: libs="$libs -l "
    修改成: libs="$libs -lmysqlclient -lssl -lcrypto"
4. pip install mysqlclient
5. pip install MySQL-python