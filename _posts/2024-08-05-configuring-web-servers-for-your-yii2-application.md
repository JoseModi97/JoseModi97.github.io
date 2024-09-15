---
title: Configuring Web Servers for Your Yii2 Application
description: A Comprehensive Guide on how to configure yii2 web server
author: modi
date: 2024-08-05 16:51:00 +0300
categories: [Yiiframework, Server]
tags: [php]
pin: false
math: true
mermaid: true
---

When deploying your Yii2 application to a production server, you'll want to configure your web server to optimize the application's performance and security. Yii2 supports deployment on popular web servers like Apache, Nginx, and Microsoft IIS.

## Apache Configuration
To configure Apache for your Yii2 application, you can use the following directives in your httpd.conf file or a virtual host configuration:

```apache
# Set document root to be "basic/web"
DocumentRoot "path/to/basic/web" 

<Directory "path/to/basic/web">
    # use mod_rewrite for pretty URL support
    RewriteEngine on
    
    # if $showScriptName is false in UrlManager, do not allow accessing URLs with script name
    RewriteRule ^index.php/ - [L,R=404]
    
    # If a directory or a file exists, use the request directly
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    
    # Otherwise forward the request to index.php
    RewriteRule . index.php
    
    # ...other settings...
</Directory>
```

This configuration sets the document root to the basic/web directory, which is the recommended approach to prevent unauthorized access to your application's private code and data files. It also uses mod_rewrite to create search-engine friendly URLs.


## Nginx Configuration
For Nginx, you can use the following configuration, replacing path/to/basic/web with the actual path and mysite.test with your hostname:

```nginx
server {
    charset utf-8;
    client_max_body_size 128M;

    listen 80; 
    server_name mysite.test;
    root        /path/to/basic/web;
    index       index.php;

    access_log  /path/to/basic/log/access.log;
    error_log   /path/to/basic/log/error.log;

    location / {
        # Redirect everything that isn't a real file to index.php
        try_files $uri $uri/ /index.php$is_args$args;
    }

    # uncomment to avoid processing of calls to non-existing static files by Yii
    #location ~ \.(js|css|png|jpg|gif|swf|ico|pdf|mov|fla|zip|rar)$ {
    #    try_files $uri =404;
    #}

    # deny accessing php files for the /assets directory
    location ~ ^/assets/.*\.php$ {
        deny all;
    }

    location ~ \.php$ {
        include fastcgi_params;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        fastcgi_pass 127.0.0.1:9000;
        try_files $uri =404;
    }

    location ~* /\. {
        deny all;
    }
}
```
This Nginx configuration sets the document root to the basic/web directory, denies access to PHP files in the /assets directory for security, and forwards all non-static requests to the PHP interpreter.

## IIS Configuration
For Microsoft IIS, you'll need to create a web.config file in the basic/web directory with the following content:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
<system.webServer>
<directoryBrowse enabled="false" />
  <rewrite>
    <rules>
      <rule name="Hide Yii Index" stopProcessing="true">
        <match url="." ignoreCase="false" />
        <conditions>
        <add input="{REQUEST_FILENAME}" matchType="IsFile" 
              ignoreCase="false" negate="true" />
        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" 
              ignoreCase="false" negate="true" />
        </conditions>
        <action type="Rewrite" url="index.php" appendQueryString="true" />
      </rule> 
    </rules>
  </rewrite>
</system.webServer>
</configuration>
```

This configuration hides the index.php file from the URL and ensures that all non-file and non-directory requests are forwarded to the index.php script.

By following these recommendations, you can ensure that your Yii2 application is properly configured and optimized for deployment on popular web servers. Remember to adjust the paths and settings to match your specific environment.