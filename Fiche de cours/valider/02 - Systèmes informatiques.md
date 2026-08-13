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

## Notes personnelles, exercices et captures d’origine

> Cette section conserve **intégralement** le contenu personnel présent avant la refonte : formulations de cours, exercices, rappels et captures d’écran. Les sections précédentes servent de complément structuré; elles ne remplacent pas ces notes.

##  1)Systèmes de fichiers (HDD/SSD) — mémo

- **NTFS (Windows)**
    - ✅ Journalisation, **droits/ACL**, quotas, audit, chiffrement
    - 🎯 Idéal : **disque système / disque interne Windows**
- **FAT32 (très compatible)**
    - ✅ Compatibilité maximale (appareils, clés USB)
    - ⚠️ **Fichier ≤ 4 Go** ; formatage Windows souvent limité à **32 Go**
- **exFAT (externe moderne)**
    - ✅ Très bon pour **USB/disques externes** + **gros fichiers**
    - 🎯 Idéal : transferts **Windows ↔ macOS** (et souvent Linux selon support)
- **APFS (Apple)**
    - ✅ Optimisé SSD, chiffrement, gestion moderne de l’espace
    - 🎯 Idéal : volumes macOS/iOS
- **EXT4 (Linux)**
    - ✅ Standard Linux, robuste, performant
    - 🎯 Idéal : systèmes et données Linux

---

## 2) Partitionnement & tables (MBR / GPT) — mémo
14
- **MBR (legacy / BIOS)**
    - ⚠️ Disques jusqu’à **~2 To**
    - ⚠️ **4 partitions primaires** max (ou 3 + 1 étendue)
    - ❌ Pas de redondance → plus sensible à la corruption
    - 🔹 Notions : **partition active** (boot), **partition étendue** (lecteurs logiques)
- **GPT (moderne / UEFI)**
    - ✅ Disques **> 2 To**
    - ✅ Jusqu’à **128 partitions**
    - ✅ Table plus robuste (copie + vérifications)
    - 🔹 Notion : **ESP (EFI System Partition)** pour le démarrage
- **Règle rapide**
    - PC récent / UEFI / grand disque → **GPT**
    - Compatibilité ancien matériel/OS (BIOS) → **MBR**


## 4) Gestion des disques — contrôler le type de table 🧭

* ✅ Pour vérifier si un disque est en **MBR** ou **GPT** :

  * Gestion des disques → clic droit **Disque 0** → **Propriétés** → onglet **Volumes**
  * Lire **Type de partition** (MBR/GPT) 


## 6) Systèmes de fichiers — choix rapide 💾

* **NTFS** ✅ : standard Windows (interne, droits NTFS, robustesse)
* **FAT32** ✅ : très compatible, mais limitations (notamment taille de fichier)
* **exFAT** ✅ : conçu pour les supports externes, “successeur” moderne de FAT32 

---



## 8) Clé USB bootable (Rufus) — mapping BIOS/UEFI 🧩

* 🧱 Machine **BIOS (ancien)** → schéma **MBR** + cible **BIOS**
* 🚀 Machine **UEFI (moderne)** → schéma **GPT** + cible **UEFI**
* 💾 Système de fichiers : **NTFS** (cas standard) 

Voici les **2 blocs à ajouter** à ton mémo (copier-coller). 👇

---

## 9) Gestion de l’ordinateur — droits utilisateur & groupes (Windows) 🛡️


### ⚠️ Windows Home vs Pro (impact admin)

* Sur **Windows Familiale**, l’outil **Gestion de l’ordinateur** ne permet pas de gérer les utilisateurs (fonctionnalité absente/bridée) 
* Sur **Windows Pro**, tu peux gérer **groupes locaux** + rôles plus fins (ex. **Opérateur de sauvegarde**) 

### 👥 Groupes locaux (RBAC “light”)

Exemples de groupes (selon besoins) : **Administrateurs**, **Utilisateurs**, **Invités**, **Opérateurs de configuration réseau**, **Opérateur de sauvegarde**, **Utilisateurs du Bureau à distance**, etc. 
➡️ Pour voir la définition/descriptions : **Gestion de l’ordinateur → Outils système → Utilisateurs et groupes locaux → Groupes** 

### 🧬 Point critique : SID ≠ nom d’utilisateur

* Un compte est associé à un **SID** (identifiant sécurité).
* Si tu supprimes un utilisateur puis recrées le “même nom”, **c’est un autre compte** (SID différent) → effets sur permissions NTFS/accès 

### 🔐 Droits sur fichiers/dossiers : NTFS obligatoire

* Les **droits d’accès**, **quotas** et **audit** reposent sur **NTFS** (FAT32/exFAT ne gèrent pas ces mécanismes au même niveau) 


## 10) Windows 11 — mémo express 🪟

### 🧩 Pré-requis (focus compatibilité)

Recommandé : CPU 64-bit (≥2 cœurs), **8 Go RAM**, **SSD 128 Go+**, **UEFI + Secure Boot**, **TPM 2.0**, GPU DirectX 12/WDDM 2.0+, écran 1080p+, Internet. 
⚠️ **Compte Microsoft** requis pour certaines fonctionnalités / configuration initiale (selon édition/scénario) 


🧩 11) Activer .NET Framework 3.5 (Windows 10)
✅ Méthode UI (la plus simple)

Panneau de configuration → Programmes → Activer ou désactiver des fonctionnalités Windows

Cocher .NET Framework 3.5 (inclut 2.0 et 3.0) → OK

rajout protentiel gest ion ordi pr les droits utilisateur
