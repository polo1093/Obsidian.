# Systèmes informatiques — stockage, démarrage et comptes locaux

![Windows](https://img.shields.io/badge/Windows-Administration-0078D4?style=flat-square&logo=windows11&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-Notions-FCC624?style=flat-square&logo=linux&logoColor=black)

> **Objectif :** comprendre les composants essentiels d'un poste et effectuer des choix techniques justifiés.

## Systèmes de fichiers

| Système | Usage courant | Points importants |
| --- | --- | --- |
| **NTFS** | disques Windows | ACL, journalisation, quotas et chiffrement |
| **exFAT** | supports externes | gros fichiers et bonne compatibilité |
| **FAT32** | anciens appareils | très compatible, mais fichier limité à 4 Go |
| **APFS** | appareils Apple | snapshots, chiffrement et optimisation SSD |
| **ext4** | systèmes Linux | robuste et largement utilisé |

## GPT, MBR, UEFI et BIOS

- **GPT + UEFI** constitue le choix normal sur un poste moderne;
- **MBR + BIOS** est principalement conservé pour la compatibilité avec de vieux systèmes;
- la partition système EFI contient les fichiers nécessaires au démarrage UEFI;
- Secure Boot vérifie la confiance accordée aux composants du démarrage;
- TPM protège notamment certaines clés cryptographiques.

### Vérifier sans modifier

Dans Windows, ouvrir **Gestion des disques**, puis les propriétés du disque et l'onglet **Volumes**. Avant toute conversion ou suppression de partition, sauvegarder les données et confirmer le disque ciblé.

## Comptes et autorisations

Un compte Windows est identifié par un **SID**, pas seulement par son nom. Recréer un compte portant le même nom ne restaure donc pas automatiquement les anciennes autorisations.

Principes à appliquer :

- attribuer les droits par groupe;
- respecter le moindre privilège;
- séparer le compte quotidien du compte administratif lorsque possible;
- documenter les changements d'appartenance;
- vérifier les permissions effectives, y compris l'héritage;
- ne pas contourner les restrictions NTFS avec un partage trop permissif.

## Commandes de contrôle

~~~powershell
Get-ComputerInfo
Get-Disk
Get-Partition
Get-Volume
Get-LocalUser
Get-LocalGroup
Get-LocalGroupMember -Group "Administrateurs"
~~~

Ces commandes sont principalement en lecture. Toute commande de modification doit être validée selon la procédure de l'organisation.

## Démarrage et récupération

Ordre de diagnostic recommandé :

1. confirmer l'alimentation et les messages matériels;
2. vérifier si le disque est détecté dans le micrologiciel;
3. observer les codes ou messages de démarrage;
4. tenter l'environnement de récupération Windows;
5. consulter les journaux et l'état du disque;
6. protéger les données avant une réparation intrusive.

## Choisir un support de démarrage

Lors de la création d'une clé d'installation :

- confirmer l'architecture et l'édition nécessaires;
- vérifier le mode UEFI ou BIOS de l'appareil;
- utiliser une image provenant d'une source officielle;
- valider la clé sur un appareil de test;
- ne jamais démarrer une installation sans confirmer la sauvegarde et la cible.

## Mise en situation

Un ordinateur ne démarre plus après une modification du micrologiciel. Avant de réinstaller Windows, vérifier le mode UEFI, l'ordre de démarrage, la présence du disque et l'état de Secure Boot. Documenter les paramètres initiaux afin de pouvoir revenir en arrière.

---

[← Sommaire](./README.md) · [Diagnostic et résolution →](./04%20-%20Résolution%20de%20problèmes.md)
