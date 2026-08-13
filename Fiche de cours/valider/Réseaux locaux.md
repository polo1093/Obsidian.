# Réseaux locaux — fondamentaux

![TCP/IP](https://img.shields.io/badge/Réseau-TCP%2FIP-0A66C2?style=flat-square)
![Diagnostic](https://img.shields.io/badge/Approche-Couche%20par%20couche-2E7D32?style=flat-square)

> **Objectif :** comprendre la circulation des données dans un réseau local et diagnostiquer les problèmes de connectivité.

## Éléments d'un réseau

| Élément | Rôle |
| --- | --- |
| Carte réseau | connecte l'appareil au média |
| Commutateur | relie les appareils d'un même réseau local |
| Routeur | relie plusieurs réseaux et choisit une route |
| Point d'accès | offre une connexion sans fil au réseau |
| Pare-feu | autorise ou bloque des communications |
| Serveur DHCP | attribue automatiquement la configuration IP |
| Serveur DNS | traduit les noms en adresses IP |

## Configuration IPv4

Une configuration fonctionnelle comprend généralement :

- une adresse IP;
- un masque ou préfixe;
- une passerelle par défaut;
- un ou plusieurs serveurs DNS.

Une adresse **169.254.x.x** indique souvent que le poste n'a pas obtenu de bail DHCP.

## Ports courants

| Service | Port | Transport |
| --- | ---: | --- |
| DNS | 53 | UDP/TCP |
| DHCP | 67/68 | UDP |
| HTTP / HTTPS | 80 / 443 | TCP |
| SSH | 22 | TCP |
| RDP | 3389 | TCP/UDP |
| SMB | 445 | TCP |
| NTP | 123 | UDP |

Un port connu ne garantit pas qu'un service est actif ou autorisé par le pare-feu.

## Diagnostic par étapes

1. vérifier le câble, le Wi-Fi et les voyants;
2. lire la configuration avec **ipconfig /all**;
3. tester la pile locale avec l'adresse de bouclage;
4. tester l'adresse IP du poste;
5. tester la passerelle;
6. tester une adresse Internet;
7. tester la résolution DNS;
8. tester le port du service concerné.

~~~powershell
ipconfig /all
ping 127.0.0.1
ping 192.168.1.1
nslookup example.com
tracert example.com
Test-NetConnection example.com -Port 443
Get-NetAdapter
Get-NetIPConfiguration
~~~

## Wi-Fi

Facteurs à vérifier :

- puissance et stabilité du signal;
- fréquence 2,4 GHz ou 5/6 GHz;
- interférences et canaux;
- authentification et chiffrement;
- pilotes de la carte;
- itinérance entre points d'accès;
- saturation du réseau.

## Principes de sécurité

- remplacer les identifiants par défaut;
- utiliser WPA2 ou WPA3 selon la compatibilité;
- séparer les invités, objets connectés et postes administratifs;
- désactiver les services inutiles;
- documenter les changements;
- appliquer les mises à jour;
- sauvegarder la configuration des équipements.

## Mise en situation

Un poste atteint la passerelle et une adresse Internet, mais pas un site par son nom. La couche physique et le routage fonctionnent probablement; concentrer le diagnostic sur DNS avant de modifier le pilote ou le pare-feu.

---

## Notes personnelles, exercices et captures d’origine

> Cette section conserve **intégralement** le contenu personnel présent avant la refonte : formulations de cours, exercices, rappels et captures d’écran. Les sections précédentes servent de complément structuré; elles ne remplacent pas ces notes.

## 🧠 Fiche ultra-courte — Réseaux locaux (résumé)

### 🌍 Types de réseaux (portée)

* 📱 **PAN** : réseau personnel (Bluetooth, quelques mètres)
* 🏢 **LAN** : réseau local (maison/bureau/bâtiment)
* 🏙️ **MAN** : réseau d’une ville / agglomération
* 🌐 **WAN** : réseau étendu (pays/monde, Internet)

### 🧩 Organisation d’un réseau

* 🧑‍💼➡️🗄️ **Client-serveur** : serveur central = services (fichiers, comptes, imprimantes)
* 🤝 **Peer-to-peer (P2P)** : postes au même niveau, partage direct

### 🌐 IP publique vs IP privée

* 🏠 **IP privée** : interne au LAN, **non routable** sur Internet
* 🌍 **IP publique** : visible sur Internet (souvent via **NAT**)

### ⚙️ DHCP

* 🪄 Attribue automatiquement : **IP + masque + passerelle + DNS** (bail/lease)

### 🧮 Masque / sous-réseau (idée clé)

* ✅ **Même sous-réseau** → communication directe (ARP) → **ping OK**
* ❌ **Sous-réseaux différents** → besoin **routeur/passerelle** → sinon **ping KO**
* ➕ **Masque plus large** (ex: **/22**) peut regrouper plusieurs /24 → **ping redevient OK**

### 🛠️ Commandes Windows utiles

* 🧾 `ipconfig` / `ipconfig /all` : IP, masque, passerelle, DNS
* 📡 `ping` : test connexion + latence
* 🧭 `tracert` : chemin + nombre de sauts
* 🔎 `nslookup` : DNS (nom ↔ IP)
* ♻️ `ipconfig /release` + `ipconfig /renew` : renouveler DHCP
* 🧹 `ipconfig /flushdns` : vider le cache DNS
