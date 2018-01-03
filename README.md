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
composer update  
exit  


在www下同名laravel过程下  
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

开启8082端口(测试环境里80已经有nginx)  
开启8083端口(用于反向代理到百度)  
firewall-cmd --zone=public --add-port=8082/tcp --permanent  
firewall-cmd --zone=public --add-port=8083/tcp --permanent  
systemctl restart firewalld.service  
访问本机8082端口,实现登录  
访问本机8083端口,跳转到百度  








