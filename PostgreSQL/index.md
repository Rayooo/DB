ubuntu 下安装 PostgreSQL

```shell
$ sudo apt-get update
$ sudo apt-get install postgresql postgresql-contrib
```

连接进入数据库 -d代表数据库名称，-w代表需要密码

```shell
$ psql -h 123.206.121.72 -U root -W -d postgres
```

修改密码，使用postgres 登录

```shell
$ sudo -i -u postgres
$ createuser --interactive
或者
$ postgres@VM-88-17-ubuntu:~$ psql #以某个用户登录
postgres=# \password postgres
# 输入密码
postgres=# \q 					#退出
```

修改PostgreSQL使得可以远程登录

进入 /etc/postgresql/9.3/main/ ，修改postgresql.conf 添加

```
listen_addresses = '*'
```

修改 pg_hba.conf ，添加

```
host  all  all 0.0.0.0/0 md5
```

重启服务

```shell
$ sudo /etc/init.d/postgresql restart
```

数据库的一些操作

```shell
postgres=# \l		#显示数据库名称
postgres=# \c <数据库名>  #改变数据库

\h：查看SQL命令的解释，比如\h select。
\?：查看psql命令列表。
\l：列出所有数据库。
\c [database_name]：连接其他数据库。
\d：列出当前数据库的所有表格。
\d [table_name]：列出某一张表格的结构。
\du：列出所有用户。
\e：打开文本编辑器。
\conninfo：列出当前数据库和连接的信息。
```
使用docker启动服务

```shell
$ docker pull hub.c.163.com/library/postgres:9.3.16
$ docker run --name postgres -e POSTGRES_PASSWORD=mysecretpassword -d -p 5432:5432 <镜像id>
#进入容器
$ docker exec -it <容器id> psql -U postgres -w   #不过postgresql机制是本地连接是不需要密码的，远程连接需要密码
```

