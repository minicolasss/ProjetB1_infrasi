# Serveur WordPress

## Sommaire

- [Monter un serveur WordPress](#monter-un-serveur-wordpress)
  - [Serveur LAMP](#serveur-lamp)
  - [Création de la base de données](#création-de-la-base-de-données)
  - [Installation de WordPress](#installation-de-wordpress)
- [Configuration de WordPress](#configuration-de-wordpress)

## Monter un serveur WordPress

Dans un premier temps, il faut vérifier qu'aucune mise à jour n'est nécessaire sur le serveur :

```bash
apt-get update
apt-get upgrade
```

### Serveur LAMP

Nous allons monter un serveur LAMP (Linux, Apache, MariaDB, PHP). Il s'agit d'un serveur qui repose sur quatre composants :

- L pour Linux, c'est-à-dire le système d'exploitation (Debian, dans notre cas).
- A pour Apache, c'est-à-dire le serveur Web.
- M pour MySQL/MariaDB, c'est-à-dire le système de gestion de bases de données.
- P pour PHP, c'est-à-dire le moteur de scripts.

### Installation et activation d'Apache2

```bash
apt-get install -y apache2
systemctl enable apache2
```

Activation de quelques modules pour Apache2 :

```bash
a2enmod rewrite
a2enmod deflate
a2enmod headers
a2enmod ssl
systemctl restart apache2
```

### Installation de PHP

```bash
apt-get install -y php
apt-get install -y php-pdo php-mysql php-zip php-gd php-mbstring php-curl php-xml php-pear php-bcmath
```

Vérifions l'installation de PHP en affichant la version installée :

```bash
php -v
```

### Installation de MariaDB

```bash
apt-get install -y mariadb-server
mariadb-secure-installation
```

### Création de la base de données

Nous allons maintenant créer la base de données qui sera utilisée par WordPress.

Connexion à MariaDB :

```bash
mysql -u root -p
```

Création de la base de données et de l'utilisateur associé :

```bash
CREATE DATABASE wordpressdb;
CREATE USER 'userdb'@'localhost' IDENTIFIED BY 'Votre-Super-Mot-De-Passe';
GRANT ALL PRIVILEGES ON wordpressdb.* TO 'userdb'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

Une fois la base de données créée, il est important de bien conserver ces informations, car elles seront nécessaires plus tard.

### Installation de WordPress

Nous allons maintenant installer WordPress :

```bash
cd /var/www/html
rm /var/www/html/index.html
wget https://wordpress.org/latest.zip
unzip latest.zip
rm latest.zip
```

N'oublions pas d'ajuster les privilèges :

```bash
chown -R www-data:www-data /var/www/html/
```

L'installation de WordPress est terminée. L'étape suivante est la configuration.

## Configuration de WordPress

Pour configurer WordPress, ouvrez un navigateur et entrez l'adresse IP de votre serveur.

Vous devriez arriver sur cette page :

![](image/acceiwordpress.png)

Suivez les étapes jusqu'à arriver à la page où vous devez entrer les informations de votre base de données créée précédemment :

![](image/dbwordpress.png)

Les informations affichées sur l'image proviennent d'un autre site, mais vous devez entrer celles que vous avez configurées.

Pour les prochaines étapes, suivez simplement les instructions. Vous venez de terminer l'installation et la configuration de WordPress !



