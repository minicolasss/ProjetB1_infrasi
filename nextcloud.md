# serveur Nextcloud

## Sommaire


## monter un serveur Nextcloud

### installation des paqués

Dans un premier temps, il faut vérifier qu'aucune mise à jour n'est nécessaire sur le serveur :

```bash
apt-get update
apt-get upgrade
```

Ensuite, nous allons installer les modules nécessaires pour monter notre serveur :

```bash
apt-get install apache2 mariadb-server php8.1 php8.1-common php8.1-curl php8.1-gd php8.1-intl php8.1-mbstring php8.1-xmlrpc php8.1-mysql php8.1-xml php8.1-cli php8.1-zip wget unzip
```

pour une question de praticiter je me deplace dans :

```bash
cd /var/www/html
```

nous allons installer nextcloud et le unzip :

```bash
wget https://download.nextcloud.com/server/releases/latest.zip
unzip latest.zip
```

le fichier latest.zip ne nous sert plus donc je prefere directement le supprimer :

```bash
rm latest.zip
```

Il ne reste plus qu'à changer le propriétaire des données de Nextcloud pour que ce soit l'utilisateur d'Apache2 :

```bash
chown -R www-data:www-data /var/www/html/nextcloud
```

### création de la base de données

pour cela nous allons utiliser mariadb :

```bash
mysql_secure_installation
```

Une fois que c'est fait, connectez-vous à votre instance MariaDB avec le compte root et le mot de passe que vous venez de définir.

```bash
mysql -u root -p
```

nous allons créer la base de données de nextcloud :

```bash
CREATE DATABASE nextcloud;
```

```bash
GRANT ALL ON db23nextcloud.* TO 'usrnextcloud'@'localhost' IDENTIFIED BY 'MOT DE PASSE';
```

bien evidament je ne vait pas montrer mon mot de passe.

```bash
FLUSH PRIVILEGES;
EXIT;
```

### configuration de NextCoud 

il suffit de rentrer l'adresse ip du serveur nextcloud en temps qu'url.


![](https://www.it-connect.fr/wp-content-itc/uploads/2023/03/Installer-Nextcloud-sur-Debian-11-Etape-1.jpg)


Sur cette page on rentre les information créer au prealable est c'est bon le serveur nextcloud et terminer.

## Interface utilisateur 

![](image/interfaceclientnextcloud.png)

sur mon image on voit la version pc mais nextcloud a aussi une version mobile ce que je prouve bien pratique.
De plus on peut aussi ajouter d'autre utilisateur si on veut partager le cloud.