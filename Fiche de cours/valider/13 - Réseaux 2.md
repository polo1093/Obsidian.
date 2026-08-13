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

[← Sommaire](./README.md) · [Bases de données →](./18%20-%20Bases%20de%20données.md)
