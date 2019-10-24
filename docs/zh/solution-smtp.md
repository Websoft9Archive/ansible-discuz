# SMTP

大量用户实践反馈，使用**第三方 SMTP 服务发送邮件**是一种最稳定可靠的方式。  

请勿在服务器上安装sendmail等邮件系统，因为邮件系统的路由配置受制与域名、防火墙、路由等多种因素制约，非常不稳定，且不易维护、诊断故障很困难。

下面以**网易邮箱**为例，提供设置 Discuz 发邮件的步骤：

1. 在网易邮箱管理控制台获取 SMTP 相关参数
   ```
   SMTP host: smtp.163.com
   SMTP port: 465 or 994 for SSL-encrypted email
   SMTP Authentication: must be checked
   SMTP Encryption: must SSL
   SMTP username: websoft9@163.com
   SMTP password: #wwBJ8    //此密码不是邮箱密码，是需要通过163邮箱后台设置去获取的授权码
   ```
2. 进入 Discuz 后台，打开：【站长】>【邮件设置】，仔细填写 SMTP 参数项   
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuz-smtp-1-websoft9.png)

	- 选择第二项
	- 根据你的 SMTP 邮箱选择 SMTP服务器域名，前面的”ssl://“一定不能省略
	- 端口栏输入 SMTP 服务器提供的端口号，一般为 465 ，具体的可根据自己的邮箱地址到官网查看
	- 发件人邮件地址输入你自己的邮箱（**需要与SMTP身份验证用户名所填的邮箱地址一致**）
	- 输入提供 SMTP 服务的邮箱地址
	- 输入 SMTP 服务验证码（和邮箱登陆密码不一样）
 
3. 在 Discuz 后台，打开【全局】>【站点信息】，设置全局管理员邮箱，尽量和 SMTP 发件人邮箱保持一致
    ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuz-smtp-2-websoft9.png)
    
4. 测试，如出现如图所示的对话框则证明 SMTP 设置正确，另外，如果出现该对话框却在收件箱内没有邮件，请到垃圾邮件列表查看
	![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/discuz-smtp-3-websoft9.png)
 
> 更多邮箱设置（QQ邮箱，阿里云邮箱，Gmail，Hotmail等）以及无法发送邮件等故障之诊断，请参考由Websoft9提供的 [SMTP 专题指南](https://support.websoft9.com/docs/faq/zh/tech-smtp.html)