

sudo apt install python-software-properties

sudo add-apt-repository ppa:ondrej/php

sudo a2dismod php7.0

sudo a2enmod php7.2

sudo update-alternatives --set php /usr/bin/php

sudo systemctl restart apache2