# 初始化安装

在云服务器上部署 Discuz 预装包之后，请参考下面的步骤快速入门。

## 准备

1. 在云控制台获取您的 **服务器公网IP地址** 
2. 在云控制台安全组中，检查 **Inbound（入）规则** 下的 **TCP:80** 端口是否开启
3. 若想用域名访问 Discuz，请先到 **域名控制台** 完成一个域名解析

## Discuz!Q 安装向导

1. 本地电脑浏览器访问网址：*http://域名/dl.php* 或 *http://服务器公网IP/dl.php*, 进入安装向导界面
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuzq-wizard-websoft9.png)

2. 设置站点名称、数据库连接和管理员账号，其中**数据库连接无需修改**，然后点击【下一步】
  ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuzq-setting-websoft9.png)

3. 安装完成，手机扫描右侧二维码可以进入移动端页面。  
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuzq-installok-websoft9.png)

4. 本地电脑浏览器访问网址：输入*http://域名/admin* 或 *http://Internet IP/admin*, 进入登录页面
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuzq-admin-websoft9.png)

5. 输入账号密码（[不知道账号密码？](/zh/stack-accounts.md#superset)），成功登录到 Discuz!Q 后台 
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuzq-index-websoft9.png)
    
6. 其他设置：微信公众号，小程序，微信支付等
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuzq-waychat-websoft9.png)

## Discuz 安装向导

1. 使用本地电脑的 Chrome 或 Firefox 浏览器访问网址：*http://域名* 或 *http://Internet IP*, 就进入引导首页

2.  首先点击【我同意】，确认用户许可协议
    ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/ds01.png)

3.  通过环境检测后，点击【下一步】。  
    ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/ds02.png)

4.  选择需要安装的程序组，建议选择【全新安装】，然后点击【下一步】。  
    ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/ds03.png)

5.  配置数据库连接信息：默认项已经可用，即直接点击【下一步】而不做任何修改便可以完成连接。   
    ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/ds04.png)

    > 预装的 MySQL 数据库信息（[查看数据库密码](/zh/stack-accounts.md#mysql)）

6.  安装完成后的界面如下
    ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/ds05.png)

7.  进入论坛后，可以通过右上角登录对论坛进行管理。
    ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/ds06.png)


## 常见问题

#### 本地浏览器访问： *http://服务器公网IP* 显示 "该站点未安装"？

问题原因： 没有完成 DiscuzQ 初始化  
解决方案： 本地浏览器访问： *http://服务器公网IP/dl.php* 开始安装

#### 安装的时候显示Discuz! Database Error

如果数据库名称、数据库账号与数据库密码填写与实际不符合，安装就会失败，显示“Discuz! Database Error”错误，具体解决办法：

1. 使用 [phpMyAdmin](/zh/admin-mysql.md) 验证你填写的数据库账号是否与实际匹配
2. 请到服务器上删除./data/install.lock文件
3. 通过网址 *http://服务器公网IP/discuz/install* 或 *http://域名/install* 重装

#### WordPress&Discuz 组合类安装

如何你使用的是 Wordpress+Discuz等组合类部署包，请阅读[《Wordpress&Discuz 安装向导》](https://support.websoft9.com/docs/wordpress/zh/stack-installation.html#wordpress-discuz-安装向导)

#### 浏览器打开IP地址，无法访问 Discuz（白屏没有结果）？

您的服务器对应的安全组80端口没有开启（入规则），导致浏览器无法访问到服务器的任何内容

#### 本部署包采用的哪个数据库来存储 Discuz 数据？

MySQL

#### 是否可以采用云厂商提供的 RDS 来存储 Discuz 数据？

可以

#### Discuz 默认界面为什么这么普通？

是的，Discuz 默认的界面非常简单，但你可以通过后台的【应用中心】去购买模板，安装插件，对 Discuz 进行十足的个性化设置。
