codeigniter-hmvc-public-index
=============================

Starter files with Codeigniter with Modular Extensions - HMVC and index.php placed inside a "public" to begin improving security of the application. 


##  Virtual Hosts config
```
<VirtualHost *:80>
    ServerName test.localhost
    ServerAlias test.localhost
    DocumentRoot "/Applications/MAMP/htdocs_test/public"
    
    SetEnv APP_ENV development
    SetEnv LOG_LEVEL 4

    RewriteEngine On

    #Checks to see if the user is attempting to access a valid file,
    #such as an image or css document, if this isn't true it sends the
    #request to index.php
    
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d

    #This last condition enables access to the images and css folders, and the robots.txt file
    RewriteCond $1 !^(index\.php|assets|robots\.txt)
    RewriteRule ^(.*)$ /index.php/$1 [L,PT]

    <Directory "/Applications/MAMP/htdocs_test/public">
        Options +execCGI +Indexes +FollowSymLinks +Includes    
        AllowOverride All
        Order Allow,Deny
        Allow From All
    </Directory>
</VirtualHost>
```
