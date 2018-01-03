# docker-lnmp  
docker-compose for lnmp  
php-fpm 加强为安装php扩展,将/var/www映射到物理机的www工作区间，作为laravel工程运行环境  
并且安装了composer, 可使用此安装laravel工程  

# 测试方法  
拉去后执行 docker-compose up -d  
进入php-fpm容器  
docker-compose exec php-fpm bash  
新建 laravel  
laravel new starter  
cd starter  
php artisan make:Auth   
php artisan migrate  

vim .env  
数据库设置  
DB_CONNECTION=mysql  
DB_HOST=mysql  
DB_PORT=3306  
DB_DATABASE=laravel  
DB_USERNAME=root  
DB_PASSWORD=FZ123456  

设置session驱动  
SESSION_DRIVER=redis  

设置redis  
REDIS_HOST=redis  
REDIS_PASSWORD=123456  
REDIS_PORT=6379  

exit  

进入mysql容器
docker-compose exec mysql bash  
mysql -uroot -pFZ123456   
执行  
CREATE DATABASE laravel;  
exit  

开启8082端口(测试环境里80已经有nginx)  
firewall-cmd --zone=public --add-port=8082/tcp --permanent  
systemctl restart firewalld.service  
访问本机8082端口  







