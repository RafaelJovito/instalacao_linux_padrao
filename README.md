# Minha instalação Linux padrão


* Instalar alguns pacotes necessárias

```shell
sudo apt-get -y install sudo vim vim-scripts unzip zip p7zip-full htop iotop wget lynx curl locate ssh nano build-essential software-properties-common
```

* Instalar e configurar o **Git**

```shell
sudo apt-get install git

git config --global user.name "username"

git config --global user.email username@email
```

* Instalar o **PHP 8.1** e suas dependências

>Link instalar: https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/how-to-install-php-8-0-on-ubuntu-20-04-ubuntu-18-04.html

```shell
sudo apt install -y curl wget gnupg2 ca-certificates lsb-release apt-transport-https
sudo apt-add-repository ppa:ondrej/php
sudo apt update
sudo apt-get install -y php8.1 php8.1-cli php8.1-common php8.1-mysql php8.1-zip php8.1-gd php8.1-mbstring php8.1-curl php8.1-xml php8.1-bcmath php8.1-pspell php8.1-xmlrpc php8.1-ldap aspell graphviz php8.1-soap

php -v

```

* Instalar e configurar o **Apache**

```shell
sudo apt-get install apache2 libapache2-mod-php8.1

sudo vim /etc/apache2/sites-available/000-default.conf
sudo service apache2 reload

```

* Instalar e configurar o **MySQL**

```shell
sudo apt-get install mysql-server
```
* Resolvendo problemas com o root do **MySQL 8.0**

```shell
sudo mysql -uroot -p
UPDATE mysql.user SET authentication_string=null WHERE User='root';
FLUSH PRIVILEGES;

ALTER USER 'root'@'localhost' IDENTIFIED WITH caching_sha2_password BY 'yourpasswd';

exit;
sudo /etc/init.d/mysql restart
sudo /etc/init.d/apache2 restart

```

* Instalar e configurar o **PHPMyAdmin**

```shell
sudo apt-get install phpmyadmin

sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf

sudo a2enconf phpmyadmin

sudo service apache2 reload
```
```shell
sudo vim /etc/apache2/apache2.conf

```
Adicione a seguinte linha ao final do documento apache2.conf:

```shell
Include /etc/phpmyadmin/apache.conf
```
```shell
sudo service apache2 reload

```

* Instalar o **Terminator**

```shell
sudo apt-get install terminator
```

* Instalar e configurar o [**Oh-my-zsh**](https://github.com/robbyrussell/oh-my-zsh)

```shell
sudo apt-get install zsh

sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"

chsh -s /bin/zsh
```

* Baixar e instalar o **PIP**

>Link para Download: https://pip.pypa.io/en/stable/installing/

```shell
sudo python get-pip.py
```

* Instalar o [**NodeEnv**](https://github.com/ekalinin/nodeenv)

```shell
sudo pip install nodeenv
```
* Instalar o [**Composer**](https://getcomposer.org)

```shell
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === '55ce33d7678c5a611085589f1f3ddf8b3c52d662cd01d4ba75c0ee0459970c2200a51f492d557530c71c15d8dba01eae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```
```shell
sudo mv composer.phar /usr/local/bin/composer
```

* Instalar o **Google Chrome**

>Link para download: https://www.google.com.br/chrome/browser/desktop/

* Instalar o **Atom**

>Link para download: https://atom.io/

* Instalar o **Code**

>Link para download: https://code.visualstudio.com/Download

* Instalar o [**Spotify**](https://www.spotify.com/br/download/linux/)

```shell
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 0DF731E45CE24F27EEEB1450EFDC8610341D9410

echo deb http://repository.spotify.com stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list

sudo apt-get update

sudo apt-get install spotify-client
```
