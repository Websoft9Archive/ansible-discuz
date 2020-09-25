# 故障处理

此处收集使用 Discuz 过程中最常见的故障，供您参考

> 大部分故障与云平台密切相关，如果你可以确认故障的原因是云平台造成的，请参考[云平台文档](https://support.websoft9.com/docs/faq/zh/tech-instance.html)

#### Discuz后台系统首页的文件校验显示大量文件被修改，这是系统风险或网站漏洞吗？

websoft9为了优化用户体验，初始设定了随机密码；同时为了用户安全，修改了网站的访问权限，这样造成安装文件被修改的假象。
例如，discuzX3.4显示318文件被修改，60个文件丢失，这个是正常的，请务必担心。请参照下图
![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuz-risk-websoft9.png)

#### Discuz 重定向错误？

重定向错误比较常见。处理办法：分析网站根目录下的 `.htaccess` 文件，看看有没有死循环规则

#### Discuz 密码输入错误多次被锁，怎么解决？

1. 10分钟后会自动解锁。
2. 管理员登录，组织→用户 操作栏里有解锁按钮。

#### 修改了数据库密码 Discuz 不能访问？

若已完成 Discuz 安装，后通过 phpMyAdmin 修改数据库密码，Discuz 就会连不上数据库。解决办法[参考](/zh/solution-more.html#discuz-修改数据库配置)

#### Discuz 出现“对不起，您的网站已被设置禁止下载此应用”问题

该问题出现的原因：由于 Discuz 官方设置了一个应用中心开发平台[Discuz!扩展中心防骗云平台](http://www.kuozhan.net/blacklist-index.html)专门针对所谓的盗版网站进行屏蔽网站授权，导致众多无辜站长用户无法更新和下载应用中心插件、模板，并且出现”对不起，您的网站已被设置禁止下载此应用“的提示。  

解决方法：

 1. 登录到phpmyadmin，找到pre_common_setting这个表（默认表前缀pre_，请以你自己的为准。）
 2. 在找到的表里删除掉siteuniqueid这个数据（pre_common_setting表中的第10页位置。）
 3. 再重新进入网站后台——应用——获取更多应用，再次下载更新试下吧！

#### Discuz 手机版访问报错“接口错误 err05 微社区域名已更换”

错误原因：Discuz官方提供的接口地址由http://wsq.discuz.qq.com/ 换成了现在 http://wsq.discuz.com/
解决方法：

  1. 登录服务器，找到Discuz根目录下的 *class\helper\helper_form.php* 文件
  2. 


#### Discuz GBK版本乱码?

Websoft9提供的 Discuz 部署包默认都是UTF-8，一般情况下也可以支持 GBK 版本的Discuz。即当您用Discuz(GBK) 替换 Discuz00(UTF-8) 源码的时候，安装或使用若出现乱码，请参考如下解决办法：

1. 使用SFTP工具（例如“WinSCP”）连接服务器，修改 ect/php.ini 文件，保存
    ```
    默认
    default_charset = "UTF-8"

    修改为
    default_charset = "GBK"
    ```
2. 重启服务或重启服务器后生效
    ```
    systemctl restart httpd
    ```


#### Apache httpd 服务无法启动？

请通过分析日志文件定位原因： */var/log/httpd*

#### 数据库服务无法启动

数据库服务无法启动最常见的问题包括：磁盘空间不足，内存不足，配置文件错误。  
建议先通过命令进行排查  

```shell
# 查看磁盘空间
df -lh

# 查看内存使用
free -lh
```

