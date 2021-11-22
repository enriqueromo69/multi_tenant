##
composer require hyn/multi-tenant
php artisan vendor:publish --tag=tenancy

## creaccion de modelos
php artisan make:model Models/Tenant/User

## creacion de controladores
php artisan make:controller /System/UserController --resource
php artisan make:controller /Tenant/UserController --resource

## creando la actualizacion y los permisos de apache

sudo a2enmod rewrite

sudo nano /etc/apache2/apache2.conf

<Directory /mnt/ntfs/htdocs/*>
        Options Indexes FollowSymLinks
        #AllowOverride None
        AllowOverride All
        Require all granted
</Directory>


sudo service apache2 restart
