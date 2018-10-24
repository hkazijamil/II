```
LoadModule wsgi_module     /usr/lib64/apache2/modules/mod_wsgi.so
LoadModule alias_module    /usr/lib64/apache2/modules/mod_alias.so
<VirtualHost :80>
  ServerName domain_name.net
  ServerAlias mail.domain_name.net www.domain_name.net
  DocumentRoot /home/domain_sort_name/public_html
  ServerAdmin webmaster@domain_name.net
  UseCanonicalName Off
  CustomLog /etc/apache2/logs/domlogs/domain_name.net combined
  ErrorLog /home/domain_sort_name/www/error.log

    #Demon process for multiple virtual hosts
    WSGIDaemonProcess domain_name threads=5

    #Pointing wsgi script to config file
    WSGIScriptAlias / /home/domain_sort_name/www/wsgi-scripts/domain_name.wsgi
    WSGIProcessGroup domain_name

    #Your static files location
    Alias /static/ "/home/domain_sort_name/www/domain_name/static/"
    Alias /media/ "/home/domain_sort_name/www/domain_name/media/"
    <Location "/media">
        SetHandler None
    </Location>
    <LocationMatch "\.(jpg|gif|png|js|css)$">
        SetHandler None
    </LocationMatch>
    <Directory /home/domain_sort_name/www/domain_name >
        WSGIProcessGroup domain_name
        WSGIApplicationGroup %{GLOBAL}
        Order deny,allow
        Allow from all
    </Directory>
    <Directory "/home/domain_sort_name/www/wsgi-scripts">
       <Files "domain_name.wsgi">
              Require all granted
       </Files>
  </Directory>
   <Directory /home/domain_sort_name/www/static> 
    Order deny,allow
      Require all granted 
  </Directory> 
  <Directory /home/domain_sort_name/www/media>
      Order deny,allow
      Allow from all
  </Directory>
  <IfModule log_config_module>
    <IfModule logio_module>
      CustomLog /etc/apache2/logs/domlogs/domain_name.net-bytes_log "%{%s}t %I .\n%{%s}t %O ."
    </IfModule>
  </IfModule>
  ## User domain_sort_name # Needed for Cpanel::ApacheConf
  <IfModule userdir_module>
    <IfModule !mpm_itk.c>
      <IfModule !ruid2_module>
        <IfModule !mod_passenger.c>
          UserDir disabled
          UserDir enabled domain_sort_name
        </IfModule>
      </IfModule>
    </IfModule>
  </IfModule>

  # Enable backwards compatible Server Side Include expression parser for Apache versions >= 2.4.
  # To selectively use the newer Apache 2.4 expression parser, disable SSILegacyExprParser in
  # the user's .htaccess file.  For more information, please read:
  #    http://httpd.apache.org/docs/2.4/mod/mod_include.html#ssilegacyexprparser
  <IfModule include_module>
    <Directory "/home/domain_sort_name/public_html">
      SSILegacyExprParser On
    </Directory>
  </IfModule>



      <Directory "/home/domain_sort_name">
        AllowOverride All
      </Directory>



  <IfModule suphp_module>
    suPHP_UserGroup domain_sort_name domain_sort_name
  </IfModule>
  <IfModule suexec_module>
    <IfModule !mod_ruid2.c>
      SuexecUserGroup domain_sort_name domain_sort_name
    </IfModule>
  </IfModule>
  <IfModule ruid2_module>
    RMode config
    RUidGid domain_sort_name domain_sort_name
  </IfModule>
  <IfModule mpm_itk.c>
    # For more information on MPM ITK, please read:
    #   http://mpm-itk.sesse.net/
    AssignUserID domain_sort_name domain_sort_name
  </IfModule>
  <IfModule mod_passenger.c>
    PassengerUser domain_sort_name
    PassengerGroup domain_sort_name
  </IfModule>

  <IfModule alias_module>
    ScriptAlias /cgi-bin/ /home/domain_sort_name/public_html/cgi-bin/
  </IfModule>


    # Global DCV Rewrite Exclude
    <IfModule rewrite_module>
        RewriteOptions Inherit
    </IfModule>



  # To customize this VirtualHost use an include file at the following location
  # Include "/etc/apache2/conf.d/userdata/std/2_4/domain_sort_name/domain_name.net/*.conf"
</VirtualHost>
```



```
import os
import sys
import site


site.addsitedir('/home/domain_sort_name/.local/lib/python3.6/site-packages')

sys.path.append('/home/domain_sort_name/www/domain_name')
sys.path.append('/home/domain_sort_name/www/domain_name/domain_name')

os.environ['DJANGO_SETTINGS_MODULE'] = 'domain_name.settings'


from django.core.wsgi import get_wsgi_application
application = get_wsgi_application()

```