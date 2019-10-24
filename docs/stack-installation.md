# Initial Installation

If you have completed the Discuz deployment on Cloud Platform, the following steps is for you to start use it quikly

## Preparation

1. Get the **Internet IP** on your Cloud Platform
2. Check you **[Inbound of Security Group Rule](https://support.websoft9.com/docs/faq/tech-instance.html)** of Cloud Console to ensure the TCP:80 is allowed
3. Make a domain resolution on your DNS Console if you want to use domain for Discuz

## Discuz Installation Wizard

1. Using local Chrome or Firefox to visit the URL *https://domain* or *https://Internet IP*, start to install  

2. Click "我同意",accept the liecense to the next step
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/ds01.png)

3. Requirement check,then Click "下一步"
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/ds02.png)

4. Select "全新安装 Discuz!X(含 UCenter Server)" and Click "下一步"
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/ds03.png)

5. Then configure the database connection information([Don't know password?](/stack-accounts.md#mysql))
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/ds04.png)

6. Complete the installation, you can access the Discuz now
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/ds05.png)

7. In the index page of Discuz, you can see the log in area
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/discuz/ds06.png)

8. Discuz provides a very powerful function of installing templates and plug-ins online. you log in to the background of Discuz and connect your application center account, you can purchase (free or charged) plugin templates online through the background and install them online.


## Q&A

#### I can't visit the start page of Discuz?

Your TCP:80 of Security Group Rules is not allowed so there no response from Chrome or Firefox

#### Which database does this Discuz package use?

MySQL

#### Can I use Cloud database for Discuz?

Yes

#### Discuz! Database Error 

If you database configuration is incorrect,you can receive the message "Discuz! Database Error"

1. Using phpMyAdmin to check you database account
2. Connect in Cloud Server, delete the file: */data/wwwroot/discuz/data/install.lock*
3. Visit URL *https://Internet IP or Domain/install* to start re-installation

### Is there an English package?
Discuz only have Chinese language now