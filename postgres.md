```
sudo apt-get install postgresql
```
 for django
```
sudo apt-get install binutils libproj-dev gdal-bin
sudo apt-get install postgis
sudo -i -u postgres
createuser --interactive --pwprompt
Enter name of role to add: your_username
Enter passsword for new role:
Enter it again:
Shall the new role be a superuser?(y/n) n
Shall the new role be allowed to create databases?(y/n) y
Shall the new role be allowed to create more new roles?(y/n) n


createdb your_project_name
psql
grant all privileges on database your_project_name to your_username;

\q
$ psql <db name>
> CREATE EXTENSION postgis;

exit
```
postgres -D /usr/local/var/postgres

ALTER USER myuser WITH SUPERUSER;

MAC RESTART

```
pg_ctl -D /usr/local/var/postgres -l /usr/local/var/postgres/server.log restart
```

CENTOS
```
yum install postgresql10-server postgresql10

service postgresql-10 start
chkconfig postgresql-10 on

su - postgres -c "psql"
```

## CentOS/RHEL - 7
```
rpm -Uvh https://yum.postgresql.org/10/redhat/rhel-7-x86_64/pgdg-centos10-10-2.noarch.rpm
```
## CentOS/RHEL - 6
```
rpm -Uvh https://yum.postgresql.org/10/redhat/rhel-6-x86_64/pgdg-redhat10-10-2.noarch.rpm
```
## Fedora - 28
```
rpm -Uvh https://yum.postgresql.org/10/fedora/fedora-28-x86_64/pgdg-fedora10-10-4.noarch.rpm
```
## Fedora - 27
```
rpm -Uvh https://yum.postgresql.org/10/fedora/fedora-27-x86_64/pgdg-fedora10-10-4.noarch.rpm
```
## Fedora - 26
```
rpm -Uvh https://yum.postgresql.org/10/fedora/fedora-26-x86_64/pgdg-fedora10-10-4.noarch.rpm
```
