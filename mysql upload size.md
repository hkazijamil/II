
```
sudo gedit /etc/php/7.0/apache2/php.ini
```
```
max_execution_time = 5000
max_input_time = 5000
memory_limit = 1000M
post_max_size = 750M
upload_max_filesize = 750M
```

```
ini_set('upload_max_filesize', '750M');     
ini_set('max_execution_time', '5000');
ini_set('memory_limit', '1000M');
ini_set('post_max_size', '750M');
ini_set('max_input_time', '5000');
```