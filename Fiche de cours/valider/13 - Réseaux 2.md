# Services réseau — DHCP, DNS, partage et accès distant

![DNS](https://img.shields.io/badge/Service-DNS-5C6BC0?style=flat-square)
![DHCP](https://img.shields.io/badge/Service-DHCP-00897B?style=flat-square)

> **Objectif :** configurer et diagnostiquer les services qui permettent aux postes de communiquer et d'accéder aux ressources.

## DHCP

Le DHCP fournit notamment l'adresse IP, le préfixe, la passerelle et les serveurs DNS.

Cycle simplifié : **Discover → Offer → Request → Acknowledge**.

Vérifications utiles :

- étendue active et adresses disponibles;
- options de passerelle et DNS;
- réservation liée à la bonne adresse MAC;
- absence de serveur DHCP non autorisé;
- heure du bail;
- connectivité entre le client et le serveur ou le relais.

~~~powershell
ipconfig /release
ipconfig /renew
Get-NetIPConfiguration
~~~

## DNS

| Type | Utilité |
| --- | --- |
| A / AAAA | nom vers adresse IPv4 / IPv6 |
| CNAME | alias vers un autre nom |
| MX | serveur de courrier |
| PTR | adresse vers nom |
| TXT | informations de validation ou de politique |
| SRV | localisation d'un service |

~~~powershell
Resolve-DnsName example.com
nslookup example.com
ipconfig /displaydns
ipconfig /flushdns
~~~

Vider le cache n'est pas une solution universelle : il faut d'abord comparer la réponse reçue avec la réponse attendue.

## Partages Windows

Deux niveaux d'autorisation peuvent s'appliquer :

1. permissions du partage;
2. permissions NTFS.

L'accès effectif correspond à la combinaison la plus restrictive. Attribuer les droits à des groupes, éviter **Tout le monde : contrôle total** et tester avec un compte représentatif.

## Bureau à distance

Avant d'activer RDP :

- confirmer que l'édition Windows le permet;
- limiter les utilisateurs autorisés;
- appliquer MFA ou une passerelle sécurisée lorsque disponible;
- éviter l'exposition directe à Internet;
- vérifier les règles du pare-feu;
- journaliser les connexions;
- maintenir le poste à jour.

## SMB et imprimantes

- confirmer le nom du serveur et du partage;
- tester la résolution DNS;
- vérifier le port 445;
- contrôler les identifiants enregistrés;
- vérifier les pilotes et la file d'impression;
- ne pas utiliser SMBv1 sauf contrainte exceptionnelle et documentée.

## Mise en situation

Un utilisateur reçoit une adresse valide, mais ne peut pas ouvrir un partage par nom. Tester d'abord la résolution du serveur, puis le port 445 et enfin les permissions. Éviter de réinitialiser toute la configuration réseau avant d'avoir localisé la couche en défaut.

---

## Notes personnelles, exercices et captures d’origine

> Cette section conserve **intégralement** le contenu personnel présent avant la refonte : formulations de cours, exercices, rappels et captures d’écran. Les sections précédentes servent de complément structuré; elles ne remplacent pas ces notes.

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
