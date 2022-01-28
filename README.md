# wp-dot-htaccess

My recommended `.htaccess` settings for WordPress in a production environment.

```txt
# Always use SSL
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]
</IfModule>

# Deny all access to this location
<Files ~ "^\.(htaccess|htpasswd)$">
deny from all
</Files>

# Hide a directory list
Options -Indexes

# Protect config and cron
<FilesMatch "^(wp-config\.php|wp-cron\.php)">
order allow,deny
deny from all
</FilesMatch>
```
