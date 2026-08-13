# Microsoft Azure AZ-900 — fondamentaux du cloud

![Azure](https://img.shields.io/badge/Microsoft%20Azure-AZ--900-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![Cloud](https://img.shields.io/badge/Cloud-IaaS%20%7C%20PaaS%20%7C%20SaaS-0A66C2?style=flat-square)

> **Objectif :** comprendre les modèles cloud, l'organisation d'Azure, les services principaux et les outils de gouvernance.

## Pourquoi utiliser le cloud?

- fournir des ressources rapidement;
- ajuster la capacité à la demande;
- améliorer la résilience;
- convertir une partie des investissements en dépenses d'exploitation;
- automatiser la gestion;
- déployer dans plusieurs emplacements.

La consommation doit être surveillée : l'élasticité ne garantit pas automatiquement une économie.

## Modèles de service

| Modèle | Le client gère principalement | Exemple |
| --- | --- | --- |
| **IaaS** | système, applications et données | machine virtuelle |
| **PaaS** | application et données | service d'applications |
| **SaaS** | configuration et utilisation | Microsoft 365 |

Plus le service est géré, moins le client administre l'infrastructure, mais ses responsabilités sur les identités et les données restent importantes.

## Organisation Azure

~~~text
Groupe d'administration
└── Abonnement
    └── Groupe de ressources
        └── Ressource
~~~

- un groupe de ressources regroupe des éléments ayant un cycle de vie commun;
- l'abonnement sert notamment de limite de facturation et de gestion;
- les régions contiennent des centres de données;
- les zones de disponibilité améliorent la résilience de certains services.

## Services à connaître

| Domaine | Exemples |
| --- | --- |
| Calcul | machines virtuelles, conteneurs, fonctions, App Service |
| Réseau | réseau virtuel, VPN, ExpressRoute, DNS, équilibrage |
| Stockage | objets blob, fichiers, disques, files et tables |
| Identité | Microsoft Entra ID, RBAC, accès conditionnel |
| Gestion | Azure Monitor, Advisor, Service Health, Arc |
| Sécurité | Defender for Cloud, Key Vault |
| Gouvernance | Azure Policy, verrous, balises, Cost Management |

## Disponibilité et résilience

Distinguer :

- **haute disponibilité** : réduire les interruptions;
- **reprise après sinistre** : restaurer après un événement majeur;
- **sauvegarde** : conserver des copies récupérables;
- **scalabilité** : modifier la capacité;
- **élasticité** : ajuster automatiquement cette capacité.

## Coûts et gouvernance

- estimer avec la calculatrice de prix;
- définir budgets et alertes;
- utiliser des balises cohérentes;
- choisir la bonne taille;
- arrêter les ressources inutiles;
- appliquer Azure Policy;
- protéger les ressources critiques avec des verrous;
- revoir régulièrement les recommandations.

## Infrastructure as Code

Les modèles ARM et Bicep permettent de décrire des ressources de manière versionnée et reproductible. Une modification doit être révisée, testée et associée à une stratégie de retour arrière.

> Les noms, fonctions et tarifs Azure évoluent. Pour une décision réelle, vérifier la documentation et la tarification officielles.

---

[← Sommaire](./README.md) · [Service desk →](./32%20-%20Service%20desk%20et%20gestion%20des%20billets.md)
