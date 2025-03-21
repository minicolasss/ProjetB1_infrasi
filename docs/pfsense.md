# Serveur pfSense

## Sommaire

- [Installer pfSense](#installer-pfsense)
- [Les utilités](#les-utilites)

## Installer pfSense

pfSense est un système d'exploitation destiné aux pare-feux et routeurs. Pour l'installer, il suffit de télécharger l'ISO sur leur site officiel.

Malheureusement, je n'ai plus de captures d'écran des étapes qui suivent, mais pour procéder à l'installation, il est nécessaire d'avoir au minimum deux cartes réseau sur le serveur :
- Une pour le **WAN** (connexion à Internet).
- Une pour le **LAN** (réseau interne).

Une fois l'installation terminée, connectez-vous à l'interface LAN et entrez l'adresse suivante dans un navigateur :

```bash
http://192.168.1.1
```

## Les utilités

pfSense gère le routage par défaut, ce qui est très pratique. Cependant, tout est modifiable, permettant ainsi une personnalisation avancée selon les besoins.

pfSense est également un pare-feu très performant, offrant de nombreuses fonctionnalités de sécurité pour protéger votre réseau.

