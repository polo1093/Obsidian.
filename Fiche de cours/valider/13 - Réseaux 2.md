# Fiche courte — Dossiers, profils AD et droits NTFS
<img src="https://github.com/user-attachments/assets/1daf6c66-1d69-4aa2-859c-b556c16218ab" width="50%">

## 1. Préparation

- Vérifier qu’Active Directory est déployé.
- Vérifier les réglages réseau du serveur et du client.
- IP client : 192.168.48.159
- Passerelle : 192.168.48.2
- DNS : 192.168.48.159
- Vérifier que le client rejoint bien le domaine.
- Utiliser le script de création d’utilisateurs :

[Script PowerShell — création utilisateurs](https://github.com/polo1093/Cours_DEP_SI/blob/main/script/Creation_users_reseau_2.ps1)

---

## 2. Arborescence

Créer le dossier principal sur D: :

**Pr les users commande**
```bat
\\NOMDUSERVEUR\ZZ\Personnels\%username%
```

```text
D:\WEB20
├── Direction
├── Comptabilite
│   └── Payes
├── Operations
└── Personnels
    ├── user1
    ├── user2
    └── ...
```
[Script PowerShell — Delete droit admin et ts le monde à mettre dans le dossier **Personnels**](https://github.com/polo1093/Cours_DEP_SI/blob/main/script/delete%20droits%20users.ps1))

---

## 3. Partage réseau

- Partager seulement `D:\WEB20`
- Nom du partage : `WEB20` ou `WEB20$`
- Ne pas partager tout le disque D:
- Droits de partage : large
- Droits précis : en NTFS

---

## 4. Sécurité NTFS

Dossier principal `D:\WEB20` :

- Admins : contrôle total
- SYSTEM : contrôle total
- Utilisateurs du domaine : lecture seulement

Dossiers de groupe :

- `GG_Direction` → Modification
- `GG_Comptabilite` → Modification
- `GG_Operations` → Modification
- `GG_Secretaire` → Modification ou lecture selon consigne

Dossier `Payes` :

- Désactiver l’héritage
- Garder seulement les personnes autorisées

Dossiers personnels :

- Désactiver l’héritage
- Utilisateur concerné : modification
- Admins : contrôle total
- SYSTEM : contrôle total
- Autres utilisateurs : aucun accès

---

## 5. Lecteur personnel W:

Dans AD :

- Propriétés utilisateur
- Onglet Profil
- Dossier de base
- Connecter W: vers :

```bat
\\SRV-AD\WEB20\Personnels\%username%
```

---

## 6. Script d’ouverture de session

Exemple :

```bat
@echo off
msg %username% "C'est réussi !"
if not exist W:\ net use V: \\SRV-AD\WEB20
start calc.exe
```

À placer selon l’énoncé :

- Profil utilisateur AD
- Ou GPO utilisateur
- Emplacement classique : `NETLOGON`

---

## 7. GPO utilisateur

Créer une GPO liée à l’OU des utilisateurs :

- Bloquer le Panneau de configuration
- Assigner le script d’ouverture de session
- Imposer un fond d’écran si demandé

Note : la stratégie de mot de passe se règle normalement au niveau domaine.

---

## 8. Client Windows 10/11

- Joindre le client au domaine.
- Ouvrir une session avec plusieurs utilisateurs.
- Vérifier :
  - message affiché
  - script lancé
  - lecteur W: présent
  - lecteur V: présent si demandé
  - droits NTFS corrects
  - fond d’écran appliqué si demandé

---

## 9. Sauvegarde

- Installer Sauvegarde Windows Server.
- Planifier une sauvegarde quotidienne à 20 h.
- Source : `D:\WEB20`
- Destination : 2e disque.
- Lancer une sauvegarde unique.
- Tester une restauration dans un dossier `Restauration`.

---

## 10. Sécurité Windows

Vérifier les 4 voyants verts :

- Antivirus / menaces
- Pare-feu réseau
- Applications / navigateur
- Sécurité de l’appareil

---

## Ordre conseillé

AD + réseau → script utilisateurs → arborescence → partage → NTFS → héritage → lecteur W: → script/GPO → test client → sauvegarde → sécurité
