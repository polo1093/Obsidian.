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
