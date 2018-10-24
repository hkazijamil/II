sudo /etc/init.d/apache2 start
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 restart

tail -f 50 /var/log/apache2/error.log

sudo update-rc.d apache2 enable

sudo /etc/init.d/mysql start
sudo /etc/init.d/mysql stop
sudo /etc/init.d/mysql restart

sudo update-rc.d mysql enable



Configure Apache to Start on Boot
And then start Apache:
sudo systemctl start httpd
Be sure that Apache starts at boot:
sudo systemctl enable httpd
Other useful commands for Apache
To check the status of Apache:
sudo systemctl status httpd
To stop Apache:
sudo systemctl stop httpd


sudo systemctl stop httpd
sudo systemctl start httpd
sudo systemctl enable httpd


cd /etc/postgresql/10/main/
sudo gedit postgresql.conf

sudo /etc/init.d/apache2 restart
sudo service postgresql restart