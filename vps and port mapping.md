you cannot direct assign the subdomain to a port

first create subdomain
Type: A record
Host: subdomain_name
Value: port
TTL: Automatic



https://serverfault.com/questions/695686/redirect-subdomains-to-services-on-different-ports-of-same-server

<VirtualHost *:80>
        ServerName service1.mydomain.com
        ProxyPreserveHost On
        ProxyPass / http://service1.mydomain.com:8080/
        ProxyPassReverse / http://service1.mydomain.com:8080/
</VirtualHost>

<VirtualHost *:80>
        ServerName service2.mydomain.com
        ProxyPreserveHost On
        ProxyPass / http://service2.mydomain.com:8081/
        ProxyPassReverse / http://service2.mydomain.com:8081/
</VirtualHost>

important
sudo a2enmod proxy
sudo a2enmod proxy_http
sudo a2enmod rewrite
