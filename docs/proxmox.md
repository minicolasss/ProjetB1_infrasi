# Serveur Proxmox

## Sommaire

- [Présentation de Proxmox](#presentation-de-proxmox)
- [Installation de Proxmox](#installation-de-proxmox)
- [Configuration et gestion](#configuration-et-gestion)
- [Sauvegarde et hébergement](#sauvegarde-et-hebergement)

## Présentation de Proxmox

Proxmox Virtual Environment (PVE) est une plateforme de virtualisation open-source basée sur Debian. Elle permet de gérer des machines virtuelles et des conteneurs en utilisant KVM et LXC.

## Installation de Proxmox

L'installation de Proxmox se fait en téléchargeant l'ISO depuis le site officiel :

[https://www.proxmox.com/en/downloads](https://www.proxmox.com/en/downloads)

Ensuite, il faut créer une clé USB bootable avec un outil comme `dd` sous Linux ou `Rufus` sous Windows.

### Création d'une clé USB bootable sous Linux :
```bash
sudo dd if=/chemin/vers/proxmox.iso of=/dev/sdX bs=1M status=progress
```
*(Remplacez `/dev/sdX` par l'identifiant de votre clé USB.)*

Une fois la clé prête, démarrez le serveur dessus et suivez les instructions d'installation.

## Configuration et gestion

Une fois installé, accédez à l'interface web de Proxmox via :

```bash
https://<IP_du_serveur>:8006
```

Proxmox permet de créer et gérer des machines virtuelles (VM) et des conteneurs (LXC). L'interface web facilite l'administration, l'allocation des ressources et la gestion des permissions.

## Sauvegarde et hébergement

### Gestion des sauvegardes

Proxmox intègre un système de sauvegarde via **Proxmox Backup Server (PBS)** ou d'autres solutions comme **Veeam** et **rsync**. Les sauvegardes peuvent être planifiées et stockées sur un NAS ou un serveur distant.

### Hébergement des services

Proxmox héberge plusieurs services critiques :
- **pfSense** : Pour la gestion du pare-feu et du routage réseau.
- **WordPress** : Serveur web pour héberger des sites dynamiques.
- **Nextcloud** : Solution de stockage et de partage de fichiers en cloud privé.
- **OpenVPN** : Gestion des connexions VPN pour sécuriser l'accès distant.

Avec Proxmox, tous ces services sont centralisés et optimisés, assurant une haute disponibilité et une gestion efficace des ressources.

