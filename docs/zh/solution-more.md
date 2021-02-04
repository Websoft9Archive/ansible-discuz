# 更多...

下面每一个方案，都经过实践证明行之有效，希望能够对你有帮助

## 域名绑定

绑定域名的前置条件是：已经完成域名解析（登录域名控制台，增加一个A记录指向服务器公网IP）  

完成域名解析后，从服务器安全和后续维护考量，需要完成**域名绑定**：

Discuz 域名绑定操作步骤：

1. 使用 SFTP 工具登录云服务器
2. 修改 [虚拟机主机配置文件](/zh/stack-components.html#apache)，将其中的域名相关的值
   ```text
     <VirtualHost *:80>
     ServerName  www.mydomain.com # 修改成您的实际域名
     DocumentRoot "/data/wwwroot/discuz"
     ...
   ```
3. 保存配置文件，[重启服务](/zh/admin-services.html#apache)

## Discuz 更换域名

Discuz 更换域名非常繁琐，参考论坛上的热心帖子：[discuz! X3 更改域名全程记录](https://www.discuz.net/thread-3528253-1-1.html)

### Discuz 模板/主题/应用中心使用

Discuz 有非常强大生态，大量在线安装模板、插件，您通过登录到 Discuz 后台，并连接您的【应用中心】账号，你就可以通过后台在线购买（免费或收费）插件模板，并在线安装就可以使用了。

![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuz-appcenter-websoft9.png)

> 声明：Websoft9 不擅长 Discuz 具体功能的使用，更无法提供此类问题指出。请自行参阅 [Discuz 官方论坛](http://www.discuz.net/forum.php) 完成你要做的吧

## DiscuzQ 修改数据库配置

DiscuzQ 安装目录下的 *config/config.php* 存储数据库连接信息，可以通过此文件来应对数据库账号信息发送变化。

## Discuz 修改数据库配置

在你的 Discuz 安装目录下，有三个与数据库相关的配置文件：

- config/config_global.php
- config/config_ucenter.php
- uc_server/data/config.inc.php

一旦你修改了初始化安装所用的的数据库信息，你需要配套修改以上三个文件以适用新的数据库配置


## Discuz 重置管理员密码

Discuz 密码忘记了，怎么找回？ 如下方案经过实践可用：

1. 适用 SFTP 工具连接服务器，编辑 Discuz 根目录下的 *uc_server/data/config.inc.php* 文件
2. 用下面两行代码替换 `config.inc.php` 中已有的同名段
   ```
   define('UC_FOUNDERPW','047099adb883dc19616dae0ef2adc5b6');
   define('UC_FOUNDERSALT','311254');
   ```
3. [重启服务](/zh/admin-services.md)
4. 此时 Ucenter 创始人的密码就变为: `123456789`
5. 访问 *http://服务器公网IP/uc_server*，以`123456789`作为密码登录 Ucenter
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuz-ucpwlogin-websoft9.png)
6. 通过【用户管理】中修改管理员密码
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuz-ucentermodifyadmin-websoft9.png)

## Discuz 集成 WordPress

参考[此处](https://support.websoft9.com/docs/wordpress/zh/solution-more.html##wordpress-与-discuz-集成)

## Discuz 更换默认 Logo

参考论坛上的热心帖子：[如何替换程序默认Logo](http://www.discuz.net/thread-3185527-1-1.html) 

## Discuz 设置伪静态

Discuz论坛安装完成后，想使连接里面显示文章名，应怎么开启它的伪静态功能？

1. 网站安装完成后，登录进入后台，在全局>SEO优化设置>将要设置的页面勾选上，然后提交； 
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuz-rewrite001-websoft9.png)

2. 重新回到上图页面，点击【查看当前的 Rewrite 规则】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuz-rewrite002-websoft9.png)

3. 页面会列出多种规则，请选择【Apache Web Server(虚拟主机用户)】模板（内容如下）
   ```
   # 将 RewriteEngine 模式打开
   RewriteEngine On

   # 修改以下语句中的 /discuz 为您的论坛目录地址，如果程序放在根目录中，请将 /discuz 修改为 /  对于websoft9提供的镜像，如果服务器内只有一个dicuz网站，则改成如下即可
   RewriteBase / 

   # Rewrite 系统规则请勿修改
   RewriteCond %{QUERY_STRING} ^(.*)$
   RewriteRule ^topic-(.+)\.html$ portal.php?mod=topic&topic=$1&%1
   RewriteCond %{QUERY_STRING} ^(.*)$
   RewriteRule ^article-([0-9]+)-([0-9]+)\.html$ portal.php?mod=view&aid=$1&page=$2&%1
   RewriteCond %{QUERY_STRING} ^(.*)$
   RewriteRule ^forum-(\w+)-([0-9]+)\.html$ forum.php?mod=forumdisplay&fid=$1&page=$2&%1
   RewriteCond %{QUERY_STRING} ^(.*)$
   RewriteRule ^thread-([0-9]+)-([0-9]+)-([0-9]+)\.html$ forum.php?mod=viewthread&tid=$1&extra=page\%3D$3&page=$2&%1
   RewriteCond %{QUERY_STRING} ^(.*)$
   RewriteRule ^group-([0-9]+)-([0-9]+)\.html$ forum.php?mod=group&fid=$1&page=$2&%1
   RewriteCond %{QUERY_STRING} ^(.*)$
   RewriteRule ^space-(username|uid)-(.+)\.html$ home.php?mod=space&$1=$2&%1
   RewriteCond %{QUERY_STRING} ^(.*)$
   RewriteRule ^blog-([0-9]+)-([0-9]+)\.html$ home.php?mod=space&uid=$1&do=blog&id=$2&%1
   RewriteCond %{QUERY_STRING} ^(.*)$
   RewriteRule ^(fid|tid)-([0-9]+)\.html$ archiver/index.php?action=$1&value=$2&%1
   RewriteCond %{QUERY_STRING} ^(.*)$
   RewriteRule ^([a-z]+[a-z0-9_]*)-([a-z0-9_\-]+)\.html$ plugin.php?id=$1:$2&%1
   ```

4. 在 Discuz 的根目录下，新建一个`.htaccess` 文件，将上面的模板内容拷贝进去，保存
   如果是Windows服务器，请选择【另存为】，文件类型选择【所有文件】，否则无法命名
  
5. [重启服务](/zh/admin-services.md) 后生效
  
## Discuz 修改上传附件大小

如果 [PHP](http://support.websoft9.com/docs/lamp) 上传参数已经足够大，但 Discuz 用户上传大小无法满足需求，请通过如下的方式进行修改：

1.进入后台，选择【用户】选项，在【管理者】中选择相应用户组，进入基本设置

![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuz-modifyfilesize001-websoft9.png)

2.选择【论坛相关】，选中【附件相关】

![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuz-modifyfilesize002-websoft9.png)

3.进入附件相关，在【论坛最大附件尺寸】中设置附加最大尺寸

![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuz-modifyfilesize003-websoft9.png)
