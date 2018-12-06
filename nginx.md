
sudo ln -s /etc/nginx/sites-available/reactjs /etc/nginx/sites-enabled/

sudo nano /etc/nginx/sites-available/
cat /etc/nginx/sites-enabled/

sudo nginx -t
sudo systemctl restart nginx

cat /var/log/nginx/error.log


sudo ufw enable

sudo ufw allow 
