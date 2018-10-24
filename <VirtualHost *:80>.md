```
sudo apt-get install libapache2-mod-wsgi
sudo apt-get install libapache2-mod-wsgi-py3
sudo a2enmod wsgi
```
```
chmod u+x domain_name.wsgi
```
```
LoadModule wsgi_module     /usr/lib/apache2/modules/mod_wsgi.so
LoadModule alias_module    /usr/lib/apache2/modules/mod_alias.so

<VirtualHost *:80>
 ServerName local.domain_sort_name.com
 DocumentRoot /var/www/html/domain_name/
 WSGIScriptAlias / /var/www/html/wsgi_scrips/domain_sort_name.wsgi

 <directory /var/www/html/domain_name/>
   AllowOverride all
   Require all granted
   Options FollowSymlinks
 </directory>

 Alias /static/ /var/www/html/static/

 <Directory /var/www/html/>
  Require all granted
 </Directory>
</VirtualHost>

<VirtualHost *:80>
    #My site Name
    ServerName local.domain_sort_name.com

    DocumentRoot /var/www/html/domain_name
	   ErrorLog /var/www/html/error.log

    #Demon process for multiple virtual hosts
    WSGIDaemonProcess domain_name threads=5

    #Pointing wsgi script to config file
    WSGIScriptAlias / /var/www/html/wsgi_scripts/domain_name.wsgi
    WSGIProcessGroup domain_name

    #Your static files location
    Alias /static/ "/var/www/html/domain_name/static/"
    Alias /media/ "/var/www/html/domain_name/media/"
    <Location "/media">
        SetHandler None
    </Location>
    <LocationMatch "\.(jpg|gif|png|js|css)$">
        SetHandler None
    </LocationMatch>
    <Directory /var/www/html/domain_name >
        WSGIProcessGroup domain_name
        WSGIApplicationGroup %{GLOBAL}
        Order deny,allow
        Allow from all
    </Directory>
    <Directory "/var/www/html/wsgi_scripts">
       <Files "domain_name.wsgi">
              Require all granted
       </Files>
	</Directory>
	 <Directory /var/www/html/static> 
	 	Order deny,allow
  		Require all granted 
 	</Directory> 
 	<Directory /var/www/html/media>
	    Order deny,allow
	    Allow from all
	</Directory>
 	<Directory /var/www>
	    Order deny,allow
	    Allow from all
	</Directory>
</VirtualHost>


<VirtualHost *:80>
	ServerAdmin webmaster@mydomain.com
	ServerName example.redirectme.net
	ServerAlias www.example.redirectme.net
	WSGIScriptAlias / /var/www/example.wsgi
	 
	Alias /static/ /var/www/example/static/
	       <Location "/static/">
	            Options -Indexes
	        </Location>
	 
	<Directory /var/www/example>
	Order deny,allow    
	Allow from all
	</Directory>
</VirtualHost>

```
