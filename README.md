vagrant-lnmp-box
====
This project is aimed to provide a vagrant box that is full configured for a LNMP project. 
Ubuntu 16 xenial is used as the OS for the box. 

## LNMP

In the box, mariadb is used instead of mysql. Therefore, the LNMP stand for Linux, Nginx, mariadb and PHP

## What are included in the box
The box use the ubuntu image from [Vagrant Cloud Ubuntu](https://app.vagrantup.com/ubuntu), after the provision with
ansible, it provides the following things: 

- Ubuntu 16.04 LTS
- Nginx - The version is configurable. By default, the latest version will be used.
- node.js - The version is configurable. By default, the latest version of v8.x will be used
- PHP 7 - The version is configurable. The source code of specified version (default 7.1.9) will be downloaded form
php.net and compile to install it under the directory `\opt\php`
- Java (OpenJDK) - The specified version will be installed
- redis
- mariadb - The mariadb is installed with mysql secure installation
- image processing libraries: graphicsmagick, libjpeg-turbo-progs, optipng, pngcrush, pngquant, pngnq

## What are provided in the box
- Self-signed certificate
- Website root path: The root path is always under the path `/projects/{your-project-name}/website`. By default, `info.php`
will be created with `phpinfo()` for the test purpose. You can test the box with URL `https://your-ip/info.php`, it should
print the information of PHP 

## Configuration
### Configuration of the vagrant box

### Configuration of the packages
The packages that will be installed in the box is configurable. The configuration file should be placed under `vars` of
project directory.

- packages.additional
- nginx.version
- php.version
- nodejs.version
- java.version
- mysql.root_passwd
- openssl
