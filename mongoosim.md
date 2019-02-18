```
wget https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb
sudo dpkg -i erlang-solutions_1.0_all.deb

wget https://packages.erlang-solutions.com/ubuntu/erlang_solutions.asc
sudo apt-key add erlang_solutions.asc


sudo apt-get update
sudo apt-get install erlang


wget https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb
sudo dpkg -i erlang-solutions_1.0_all.deb


wget https://packages.erlang-solutions.com/debian/erlang_solutions.asc
sudo apt-key add erlang_solutions.asc

sudo apt-get update
sudo apt-get install mongooseim


```



```
sudo apt-get update
sudo apt-get install mysql-server
mysql_secure_installation

```


### MYSQL
```
set global innodb_large_prefix = `ON`;
set global innodb_file_format = `BARRACUDA`;
set global innodb_file_format_max = `BARRACUDA`;
set global innodb_file_per_table = `ON`;
```

```
mysql -h localhost -u root -p -e 'create database mongooseim'
wget https://raw.githubusercontent.com/hkazijamil/II/master/mysql.sql
mysql -h localhost -u root -p mongooseim < mysql.sql

echo "SHOW TABLES;" | mysql -h localhost -D mongooseim -u root -p --table

sudo /etc/init.d/mysql restart


```
