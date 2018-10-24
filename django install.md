```
sudo apt-get install python3
sudo apt-get install python3-pip
sudo pip install virtualenv
sudo apt-get install python3-dev libpq-dev
```
```
mkdir django
```
```
#sudo apt-get install libmariadbclient-dev
#export PATH=$PATH:/usr/local/mysql/bin/
```

####run this outside of project:
```
 virtualenv -p /usr/bin/python3 env_name

source /path_to/env_name/bin/activate
```

go to settings file and change DATABASES config
```
#source>pip3 install Django==version_nubmer
#source>pip3 install psycopg2
#source>django-admin.py startproject project_name
#source>python manage.py startapp app_name
```
```
source>pip3 install --upgrade -r requirements.txt
source>python3 manage.py makemigrations
source>python3 manage.py migrate
```
```
pip3 install --upgrade -r requirements.txt
```


django-widget-tweaks

django-haystack


install tar.bz2 kali
```
tar xvzf PACKAGENAME.tar.gz.
```
644-264
```
DATABASES = {
    'default': {
        'NAME': 'your_db_name',
        'ENGINE': 'django.db.backends.mysql',
        'USER': 'your_db_username',
        'PASSWORD': 'your_db_pass',
        'HOST': 'localhost',
        'PORT': '3306',
        'OPTIONS': {
            'autocommit': True,
        },
    }
}
```
```
yum -y -q install http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-6
```
Then Apache...
```
yum -y -q install httpd mod_ssl httpd-devel
```
Then for Python (including some very commonly used pre-reqs):
```
yum -y -q groupinstall development
yum -y -q install zlib2-devel openssl-devel sqlite-devel bzip2-devel python-devel openssl-devel openssl-perl libjpeg-turbo libjpeg-turbo-devel zlib-devel giflib ncurses-devel gdbm-devel xz-devel tkinter readline-devel tk tk-devel kernel-headers glibc libpng gcc-c++ wget
```
Install Python 3.6.0:
```
wget 'http://www.python.org/ftp/python/3.6.0/Python-3.6.0.tgz'
tar -xzf 'Python-3.6.0.tgz'
cd ./Python-3.6.0
CXX=g++ 
./configure --prefix=/usr --build=x86_64-pc-linux-gnu --host=x86_64-pc-linux-gnu --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --libdir=/usr/lib64 --with-fpectl --enable-shared --enable-ipv6 --with-threads --infodir=${prefix}/share/info --mandir=${prefix}/share/man --with-computed-gotos --with-dbmliborder=gdbm --with-libc= --with-system-expat --with-system-ffi 
make
make install
echo "/usr/lib/python3.6" > /etc/ld.so.conf.d/python36.conf
echo "/usr/lib" >> /etc/ld.so.conf.d/python36.conf
```
Make and compile mod_wsgi (or look into MOD WSGI Express!):
```
yum install ea-apache24-devel

wget "https://github.com/GrahamDumpleton/mod_wsgi/archive/4.5.14.tar.gz"
tar -xzf '4.5.14.tar.gz'
cd ./mod_wsgi-4.5.14
./configure --with-python=/usr/bin/python3.6
make
make install
```
