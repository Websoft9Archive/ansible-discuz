# install discuzq
[安装文档](https://discuz.com/docs/install.html#%E6%9C%8D%E5%8A%A1%E5%99%A8%E8%A6%81%E6%B1%82)
***
## FAQ
经过研究发现,discuzq在安装完成后,需先通过 *http://ip/install* 进入初始化界面:  
在此过程中需输入如下固定参数:  
数据库库名: discuz  
数据库用户名: discuz  
数据库密码: 随机密码 `cat /credentials/password.txt`  
其他参数由用户自定义: 站点名称,管理员账号,管理员密码;  

初始化完成后,通过 *http://ip* 可直接访问论坛首页;  
            通过 *http://ip/admin* 访问管理员界面;

其中,管理员用户名和密码均由用户自定义,那么如何修改管理员密码?  
在知道密码的前提下; 可在管理员界面修改:                     
用户 --> 搜索 --> 详情 -->  提交新旧密码;     
在忘记密码的前提下,可在数据库中修改:        
找到数据库中的user表,修改管理员用户密码为 `$2y$10$WABNyFZ5NOkiItQfMbzu4OCVhiX.ZhDikujEF0rziQxbtGtIc0JMe` ,此时密码为123456;  


