# Toba
### Fresh Debian 10 Install

`sudo apt update -y && apt upgrade`

**Log Superusuario**

`su`

**Install wget:**

`apt-get install wget`

**Install Curl:**

`apt-get install curl`

**Install npm:**

`apt-get install npm`

**Debian php Repository:**
[packages.sury.org](https://packages.sury.org/php/README.txt)

```
apt-get -y install apt-transport-https lsb-release ca-certificates
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
sh -c 'echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'
apt-get update
```

**Install PHP7.1**

`apt-get install php7.1 php7.1-cli  php7.1-gd php7.1-curl php7.1-mcrypt php7.1-xsl php7.1-mbstring php7.1-zip php7.1-xml php7.1-soap php7.1-pgsql`

**Install Apache2 (Check)**

`apt-get install apache2 libapache2-mod-php7.1`

**Activate rewrite:**

`sudo a2enmod rewrite`

**Restart Apache:**

`systemctl restart apache2`

**Install Postgresql 9.6**

`wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -`

**Add Repository**

```
RELEASE=$(lsb_release -cs)
echo "deb http://apt.postgresql.org/pub/repos/apt/ ${RELEASE}"-pgdg main | sudo tee  /etc/apt/sources.list.d/pgdg.list
sudo apt update
```

**Install time!**

`sudo apt -y install postgresql-9.6`

**Check status**

`systemctl status postgresql`

**Set Postgres admin Password**

`sudo -u postgres psql postgres`

- **Crear password:**

`\password `

- **Salir**

`\q`

**Install Nodejs**

_Add Repository_

`curl -sL https://deb.nodesource.com/setup_6.x | bash -`

`apt-get install -y nodejs n`


**#Development tools for native addons**

`apt-get install gcc g++ make`

**Install Yarn**

_Add Repository_

```
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
apt-get update && sudo apt-get install yarn
```

**Install Bower**

`npm install -g bower`

**Install Composer**

`curl -sS https://getcomposer.org/installer | php`


`mv composer.phar /usr/local/bin/composer`

`chmod +x /usr/local/bin/composer`

**Test it**

`composer 
`
### Time to install Toba

**Install Git**

`apt-get install git`

**Clone git**

> cd _/lugar_donde_quiero_el_toba/_

`git clone https://github.com/siu-toba/framework`

> cd framework/

          > Para cambiar la version editar el archivo VERSION

`composer install`

> cd bin/

`./instalar`

**Quedariamos asi:**

> 1) Ejecutar el siguiente comando como superusuario: 
>  
>       ln -s /siu/framework/instalacion/toba.conf /etc/apache2/sites-enabled/toba_2_7.conf
>  
>  Reiniciar el servicio apache e ingresar al framework navegando hacia 
>  
>       http://localhost/toba_editor/3.2
>  
>  
>  2) Se genero el siguiente archivo:
>  
>     /siu/framework/instalacion/entorno_toba.env
>  
>  Para usar los comandos toba ejecute antes el .env precedido por un punto y espacio
>  
>  3) Entre otras cosas puede crear un nuevo proyecto ejecutando el comando
>  
>     toba proyecto crear
> 

**Cargar variables:**

`cat /siu/framework/instalacion/entorno_toba.env`

Ej:
> export TOBA_DIR=/siu/framework
> export TOBA_INSTANCIA=desarrollo
> export TOBA_INSTALACION_DIR=/siu/framework/instalacion
> export PATH="$TOBA_DIR/bin:$PATH"

**Cambiar permisos usuario/apache2** (Recomendado en Desarrollo)

`nano /etc/apache2/apache2.conf`

Ej:
> #User ${APACHE_RUN_USER}

> #Group ${APACHE_RUN_GROUP}

> #User Tu_Usuario

> #User Tu_Usuario

`chown Tu_Usuario /Directorio_Toba/ -R`

