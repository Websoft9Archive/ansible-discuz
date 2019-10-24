# SSL/HTTPS

Discuz deployment package has installed the SSL module of Nginx and open Certificate Authority **[Let's Encrypt](https://letsencrypt.org/)** for you configure the HTTPS quickly and conveniently.

> In addition to the vhost configuration file, HTTPS settings do not need to modify any files in Nginx

## Quick configuration

If you want to use a free certificate, just run the one command `certbot` on your instance to start the HTTPS deployment.
```
sudo certbot
```

If you have applied for a commercial certificate, complete the HTTPS configuration in just three steps:

1. Upload your certificate to the directory of your instance: */data/cert* 
2. Edit the vhost configuration file: */etc/httpd/conf.d/vhost.conf* 
3. Insert the **HTTPS template**  segment `<VirtualHost *:443>--</VirtualHost>` into `vhost.conf`
   ``` text
   #-----HTTPS template start------------
   <VirtualHost *:443>
    ServerName  discuz.yourdomain.com
    DocumentRoot "/data/wwwroot/discuz"
    #ErrorLog "logs/discuz.yourdomain.com-error_log"
    #CustomLog "logs/discuz.yourdomain.com-access_log" common
    <Directory "/data/wwwroot/discuz">
    Options Indexes FollowSymlinks
    AllowOverride All
    Require all granted
    </Directory>
    SSLEngine on
    SSLCertificateFile  /data/cert/discuz.yourdomain.com.crt
    SSLCertificateKeyFile  /data/cert/discuz.yourdomain.com.key
    </VirtualHost>
   #-----HTTPS template end------------
   ```
4. Modify ServerName, SSLCertificateFile, SSLCertificateKeyFile
5. Save it and [Restart Apache service](/admin-services.md#apache)


## Special Guide

For details on configuring HTTPS pre-conditions, HTTPS configuration segment templates, precautions, detailed steps, and troubleshooting, refer to the [HTTPS Special Guide](https://support.websoft9.com/docs/faq/tech-https.html#nginx) provided by Websoft9 