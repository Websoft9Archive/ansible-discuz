# More

Each of the following solutions has been proven to be effective and we hope to be helpful to you.

## Domain binding

The precondition for **Domain binding** is have completed the **Domain resolution** for Discuz Instance.

From the perspective of server security and subsequent maintenance considerations, the **Domain Binding** step cannot be omitted.

Discuz domain name binding steps:

1. Connect your Cloud Server
2. Modify [vhost configuration file](/stack-components.md#apache), change the domain name item for you
   ```text
   #### Discuz (LAMP) bind domain #### 

     <VirtualHost *:80>
     ServerName joomla.mydomain.com # modify it for you
     DocumentRoot "/data/wwwroot/Discuz"
     ...
     
   #### Discuz (LEMP) bind domain #### 

     server {
      listen 80;
      server_name joomla.example.com; # modify it for you
     ...

   ```
3. Save it and restart [Web Service](/admin-services.md#apache)

## Discuz Change domain

Refer to [discuz! X3 更改域名全程记录](https://www.discuz.net/thread-3528253-1-1.html)

## Discuz modify database connection

In your Discuz installation directory, there are three database-related configuration files:

- config/config_global.php
- config/config_ucenter.php
- uc_server/data/config.inc.php

Once you have modified the database information used to initialize the installation, you will need to modify the above three files to apply the new database configuration.


## Discuz recover administrator password

1. Use SFTP to login Server, edit the *uc_server/data/config.inc.php* file in the root directory of Discuz
2. Replace two items below with 
   ```
   define('UC_FOUNDERPW','047099adb883dc19616dae0ef2adc5b6');
   define('UC_FOUNDERSALT','311254');
   ```
3. [Restart Service](/admin-services.md)
4. Then, your Ucenter administrator password is: `123456789`
5. Visit URL *http://Internet IP/uc_server*, us `123456789` as your password to login Ucenter
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuz-ucpwlogin-websoft9.png)
6. Modify adminitrator password from 【用户管理】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuz-ucentermodifyadmin-websoft9.png)

## Discuz change Logo

Refer to Discuz forum [如何替换程序默认Logo](http://www.discuz.net/thread-3185527-1-1.html) 