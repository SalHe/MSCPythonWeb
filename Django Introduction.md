# Django Introduction

SalHe



## 预备知识

- Python
- Git
- Html



## 准备工作

- 运行环境：Python/Anaconda
- Python Package：Django
- 开发环境：PyCharm/VS Code



## Django 特点

- 强大的数据库功能

  我们不需要自己编写SQL查询语句，一切的数据库相关操作都可以借助Django的Model进行实现。

  - 自己编写代码操作数据库（创建表）

    ```python
    import MySQLdb
    
    # 打开数据库连接
    db = MySQLdb.connect("localhost", "testuser", "test123", "TESTDB", charset='utf8' )
    
    # 使用cursor()方法获取操作游标 
    cursor = db.cursor()
    
    # 如果数据表已经存在使用 execute() 方法删除表。
    cursor.execute("DROP TABLE IF EXISTS EMPLOYEE")
    
    # 创建数据表SQL语句
    sql = """CREATE TABLE EMPLOYEE (
             FIRST_NAME  CHAR(20) NOT NULL,
             LAST_NAME  CHAR(20),
             AGE INT,  
             SEX CHAR(1),
             INCOME FLOAT )"""
    
    cursor.execute(sql)
    
    # 关闭数据库连接
    db.close()
    ```

  - Django操作数据库

    1. 建立模型

    ```python
    class Employee(models.Model):
        first_name = models.CharField(max_length=20)
        last_name = models.CharField(max_length=20)
        age = models.DecimalField()
        sex = models.BooleanField()
        income = models.FloatField()
    ```

    2. 通过借助manage.py更新表

    ```
    $ python3 manage.py migrate   # 创建表结构
    
    $ python3 manage.py makemigrations TestModel  # 让 Django 知道我们在我们的模型有一些变更
    $ python3 manage.py migrate TestModel   # 创建表结构
    ```

- 自带强大的后台功能

  Django已经为我们实现好了一套后台系统，我们可以基于它进行定制，比起自己实现，方便太多了。

- 优雅的网址

  优雅的配置路由，将请求导航到不同页面。

- MTV

  Django处理请求和返回响应内容的设计模式。

  ![img](https://www.runoob.com/wp-content/uploads/2020/05/1589777036-2760-fs1oSv4dOWAwC5yW.png)

  



## 相关概念

### Request/Response

目前请先关注图中的右边部分内容：

![img](https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=1937176861,2704737492&fm=26&gp=0.jpg)

### 网页的呈现与HTML

### View/Template

### 数据库和Model

