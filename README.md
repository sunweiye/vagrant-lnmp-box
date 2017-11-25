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

### Add custom variables and roles configuration
You can specify the custom variables files path and roles path to add or override the current configurations.
- `custom_vars_path`: Define the customized variables files path. Default value is the directory under the `custom/vars`
in the current playbook directory. You can also specified an absolute path.
- `custom_play_role`: You can it with the role name, which should override the default `project` role. If this variable
is not set or in the role name directory under the `custom_roles_path` doesn't have `tasks/main.yml` file, the default
`project` role will be used to create a simple website project to print the php configurations.
- `custom_roles_path`: Define the customized roles path, which will override the default `project` role. The default value
is the directory under the `custom/roles` in the current playbook directory.

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
