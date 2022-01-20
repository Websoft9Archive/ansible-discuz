# 参数

Discuz 预装包包含 Discuz 运行所需一序列支撑软件（简称为“组件”），下面列出主要组件名称、安装路径、配置文件地址、端口、版本等重要的信息。

目前我们提供了两种 Discuz 部署包，下面分别列出其参数

## Discuz (LAMP) 路径

Discuz (LAMP) 即以 LAMP 为基础环境的 Discuz 部署包，其路径参数如下：

### Discuz

Discuz 安装目录： */data/wwwroot/discuz*  
Discuz 配置文件： */data/wwwroot/discuz/upload/config/config_global_default.php*  

> Discuz 配置文件中包含数据库连接信息，更改了 MySQL 数据库账号密码，此处也需要对应修改

### PHP

PHP 配置文件： */etc/php.ini*  
PHP Modules 配置文件目录： */etc/php.d*

### Apache

Discuz on LAMP, the Web Server is Apache  

Apache 虚拟主机配置文件：*/etc/httpd/conf.d/vhost.conf*  
Apache 主配置文件： */etc/httpd/conf/httpd.conf*  
Apache 日志文件： */var/log/httpd*  
Apache 模块配置文件： */etc/httpd/conf.modules.d/00-base.conf*

### MYSQL

MySQL 安装路径: */usr/local/mysql*  
MySQL 数据文件 */data/mysql*  
MySQL 配置文件: */etc/my.cnf*    
MySQL 可视化管理地址: *http://服务器公网IP/phpmyadmin*，用户名和密码请见 [账号密码](/zh/stack-accounts.md) 章节。

### phpMyAdmin

phpMyAdmin installation directory: */data/apps/phpmyadmin*  
phpMyAdmin configuration file: */data/apps/phpmyadmin/config.inc.php*   
phpMyAdmin vhost configuration file: */etc/httpd/conf.d/phpMyAdmin.conf* or */etc/nginx/php.conf*  

### Redis

Redis configuration file: */etc/redis.conf*  
Redis data directory: */var/lib/redis*  
Redis logs file: */var/log/redis/redis.log*

## Discuz (WAMP) 路径

Discuz (WAMP) 即以 WAMPServer 为基础环境的 Discuz 部署包，其路径参数如下：

### Discuz

Discuz 安装目录： *C:\websoft9\wampserver\www*  
Discuz 配置文件： *C:\websoft9\wampserver\www\wp-config.php* 
虚拟机主机配置文件： *C:\websoft9\wampserver\bin\apache\apache2.4.23\conf\extra\httpd-vhosts.conf*

### WAMPServer

WAMPServer 是支持 Discuz (WAMP) 的 PHP 运行环境，包括：Apache, PHP, MySQL/MariaDB 等组件，具体参考： [《WAMPServer 管理员手册》](https://support.websoft9.com/docs/wampserver/zh/stack-components.html)

## Discuz！Q 路径

Discuz！Q 以 docker 方式安装部署，其路径参数如下：

### Discuz！Q

Discuz！Q 项目目录： */data/wwwroot/docker-discuzq*
Discuz！Q 网站目录： */data/wwwroot/docker-discuzq/volumes*  


### MYSQL

MySQL 数据文件 */data/mysql*  
MySQL 可视化管理地址: *http://服务器公网IP/phpmyadmin*，用户名和密码请见 [账号密码](/zh/stack-accounts.md) 章节。

### phpMyAdmin

phpMyAdmin installation directory: */data/apps/phpmyadmin*  
phpMyAdmin configuration file: */data/apps/phpmyadmin/config.inc.php*   
phpMyAdmin vhost configuration file: */etc/httpd/conf.d/phpMyAdmin.conf* or */etc/nginx/php.conf*  

## 端口号

在云服务器中，通过 **[安全组设置](https://support.websoft9.com/docs/faq/zh/tech-instance.html)** 来控制（开启或关闭）端口是否可以被外部访问。 

本应用建议开启的端口如下：

| 名称 | 端口号 | 用途 |  必要性 |
| --- | --- | --- | --- |
| HTTP | 80 | 通过 HTTP 访问 Discuz | 必须 |
| HTTPS | 443 | 通过 HTTPS 访问 Discuz | 可选 |
| MySQL | 3306 | 远程连接 MySQL | 可选 |
| PHPMyAdmin | 9090 | 可视化管理 MySQL | 可选 |
| Discuz! Q | 9001 | 通过 HTTP 访问 Discuz！Q  | 必须 |

## 版本号

组件版本号可以通过云市场商品页面查看。但部署到您的服务器之后，组件会自动进行更新导致版本号有一定的变化，故精准的版本号请通过在服务器上运行命令查看：

```shell
# Linux Version
lsb_release -a

# PHP Version
php -v

# List Installed PHP Modules
php -m

# Apache version on Centos
httpd -v

# Apache version on Ubuntu
apache2 -v

# List Installed Apache Modules
apachectl -M

# Nginx version
nginx -v

# List Installed Nginx Modules
nginx -V

# MySQL version:
mysql -V

# Redis version
redis-server -v
```g
