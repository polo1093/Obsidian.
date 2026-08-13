# AZ-900 — Notes courtes

## 1.1 — Concepts du cloud

### Définir le cloud computing

- Le cloud computing permet d’utiliser des ressources informatiques via Internet.
- Exemples :
  - serveurs
  - stockage
  - bases de données
  - réseau
  - logiciels
- On évite d’acheter et maintenir toute l’infrastructure soi-même.
- On consomme des services à la demande.

---

### Décrire le modèle de responsabilité partagée

<img width="1920" height="1180" alt="image" src="https://github.com/user-attachments/assets/0bcba1cf-7b77-4e15-9b3f-bb3a0fde625b" />

- La sécurité est partagée entre le fournisseur cloud et le client.
- Microsoft gère :
  - les datacenters
  - le matériel physique
  - une partie de l’infrastructure cloud
- Le client gère :
  - ses données
  - ses comptes utilisateurs
  - ses droits d’accès
  - ses configurations
- Plus le service est managé, moins le client gère de choses.

---

### Définir les modèles de cloud

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3d7f68e2-7dfd-407a-9874-7228e2a78946" />

#### Cloud public

- Infrastructure fournie par un fournisseur externe.
- Exemple : Microsoft Azure.
- Les ressources sont accessibles via Internet.
- Les clients partagent l’infrastructure physique, mais les données restent isolées.

#### Cloud privé

- Infrastructure dédiée à une seule organisation.
- Peut être hébergée en interne ou chez un prestataire.
- Donne plus de contrôle.
- Demande plus de gestion.

#### Cloud hybride

- Mélange entre cloud public et infrastructure privée.
- Utile pour garder certaines données en interne.
- Pratique pour migrer progressivement vers le cloud.

#### Multicloud

- Utilisation de plusieurs fournisseurs cloud.
- Exemple : Azure + AWS + Google Cloud.
- Peut éviter la dépendance à un seul fournisseur.

---

### Cas d’usage des modèles cloud

#### Cloud public

- Applications web
- Tests rapides
- Besoin de scalabilité
- Réduction des coûts matériels

#### Cloud privé

- Données très sensibles
- Contraintes fortes de conformité
- Besoin de contrôle complet

#### Cloud hybride

- Migration progressive
- Applications locales connectées au cloud
- Données sensibles gardées en interne

#### Multicloud

- Répartition des services entre plusieurs clouds
- Réduction du risque de dépendance fournisseur

---

### Modèle basé sur la consommation

- On paie selon l’utilisation réelle.
- Exemples :
  - temps de calcul
  - stockage utilisé
  - trafic réseau
  - nombre de requêtes
- Avantage : pas besoin d’acheter trop de matériel à l’avance.
- Attention : il faut surveiller les coûts.

---

### Modèles tarifaires cloud

#### CapEx

- Dépense d’investissement.
- Achat de serveurs, matériel, licences.
- Coût important au départ.

#### OpEx

- Dépense opérationnelle.
- Paiement à l’usage ou par abonnement.
- Plus flexible.
- Modèle typique du cloud.

---

## 1.2 — Avantages du cloud

### Haute disponibilité

- Objectif : garder les services accessibles.
- Même en cas de panne, l’application peut continuer à fonctionner.
- Azure propose de la redondance et des zones de disponibilité.

---

### Scalabilité

- Permet d’adapter les ressources à la demande.

#### Scalabilité verticale

- Augmenter la puissance d’une machine.
- Exemple : plus de CPU ou de RAM.

#### Scalabilité horizontale

- Ajouter plusieurs machines ou instances.
- Plus adapté aux fortes charges.

---

### Fiabilité

- Capacité d’un système à résister aux pannes.
- Le cloud permet de répartir les ressources sur plusieurs zones ou régions.
- Utile pour les applications critiques.

---

### Prévisibilité

- Meilleure anticipation des performances et des coûts.
- Azure fournit des outils de supervision et d’estimation.
- Permet de mieux dimensionner les ressources.

---

### Sécurité

- Azure propose des outils intégrés :
  - gestion des identités
  - contrôle d’accès
  - chiffrement
  - pare-feu
  - surveillance
- Mais la configuration reste une responsabilité importante du client.

---

### Gouvernance

- Permet de définir des règles d’utilisation du cloud.
- Exemples :
  - qui peut créer des ressources
  - quelles régions sont autorisées
  - quelles limites de coût appliquer
  - quelles règles de sécurité respecter

---

### Facilité de gestion

- Les ressources peuvent être gérées depuis :
  - le portail Azure
  - la ligne de commande
  - des scripts
  - l’infrastructure as code
- Le cloud réduit la maintenance matérielle.
- Il facilite l’administration à grande échelle.

---

### Durabilité

- Le cloud optimise l’utilisation des ressources.
- Moins de serveurs inutilisés.
- Les grands datacenters peuvent être plus efficaces énergétiquement.
- Objectif : réduire le gaspillage informatique.

---

## 1.3 — Types de services cloud

### IaaS — Infrastructure as a Service

- Fournit l’infrastructure de base.
- Exemples :
  - machines virtuelles
  - stockage
  - réseau
  - pare-feu
- Le client gère :
  - le système d’exploitation
  - les applications
  - les données
- Exemple Azure : machine virtuelle.

#### Cas d’usage

- Migration d’un serveur existant.
- Besoin de contrôle technique.
- Applications anciennes ou spécifiques.

---

### PaaS — Platform as a Service

- Fournit une plateforme prête pour développer et déployer.
- Le client gère surtout :
  - le code
  - les données
- Microsoft gère :
  - les serveurs
  - le système d’exploitation
  - les mises à jour
- Exemple Azure : Azure App Service.

#### Cas d’usage

- Héberger une application web.
- Développer plus vite.
- Ne pas gérer les serveurs.

---

### SaaS — Software as a Service

- Application complète prête à l’emploi.
- L’utilisateur utilise le logiciel directement.
- Pas besoin de gérer :
  - les serveurs
  - l’installation
  - les mises à jour
- Exemples :
  - Microsoft 365
  - Outlook
  - Teams
  - Dynamics 365

#### Cas d’usage

- Utiliser un logiciel directement.
- Réduire la gestion technique.
- Donner accès rapidement aux utilisateurs.

---

## À retenir pour l’examen

- IaaS = plus de contrôle, plus de responsabilités.
- PaaS = équilibre entre contrôle et simplicité.
- SaaS = le plus simple, le moins de gestion technique.
- Cloud public = fourni par un fournisseur cloud.
- Cloud privé = dédié à une organisation.
- Cloud hybride = mélange privé + public.
- Consommation = paiement selon l’usage réel.
- CapEx = achat initial.
- OpEx = paiement opérationnel flexible.

# 2 le principale
2.1
Décrire les régions Azure, les paires de régions et les régions souveraines.
Décrire les zones de disponibilité.
Décrire les centres de données Azure.
Décrire les ressources Azure et les groupes de ressources.
Décrire les abonnements.
Décrire les groupes d’administration.
Décrire la hiérarchie des groupes de ressources, des abonnements et des groupes d’administration.
Vérifier vos connaissances
1.

Combien de groupes de ressources une ressource peut-elle se trouver en même temps ?

Une

Deux

Trois
Incorrect
2.

Que se passe-t-il pour les ressources au sein d’un groupe de ressources lorsqu’une action ou un paramètre au niveau du groupe de ressources est appliqué ?

Les ressources actuelles héritent du paramètre, mais les ressources futures ne le font pas.

Les ressources futures héritent du paramètre, mais celles actuelles ne le sont pas.

Le paramètre est appliqué aux ressources actuelles et futures.
Correct
3.

Quelle fonctionnalité Azure réplique les ressources entre les régions qui se trouvent à au moins 300 kilomètres les unes des autres ?

Paires de régions

Zones de disponibilité

Régions souveraines
Incorrect



2.2

Comparer les types de calcul, notamment les instances de conteneur, les machines virtuelles et les fonctions.
Décrire les options des machines virtuelles, y compris les machines virtuelles, les ensembles d'échelles de machines virtuelles, et les groupes de disponibilité de machines virtuelles.
Décrire les ressources nécessaires aux machines virtuelles.
Décrire les options d’hébergement d’applications, notamment Azure Web Apps, les conteneurs et les machines virtuelles.
Décrire les catégories de service IA, Machine Learning et IoT/Edge dans Azure.

1.

Quelle fonctionnalité de la machine virtuelle Azure échelonne les mises à jour des machines virtuelles en fonction de leur domaine de mise à jour et de leur domaine de panne ?

Ensembles de disponibilité
Correct

Groupes identiques

Ensembles de mises à jour
2.

Quelle option de calcul Azure est pilotée par les événements et serverless. Vous pouvez donc exécuter du code sans gérer les machines virtuelles ?

Azure Functions
Correct

Machines virtuelles Azure

Azure Container Instances (Instances de Conteneur Azure)
3.

Quel service Azure permet aux organisations d’héberger des applications web et des API sans gérer l’infrastructure sous-jacente ?

Azure App Service
Correct

Machines virtuelles Azure

Azure ExpressRoute
4.

Quelle catégorie de service Azure fournit des API prédéfinies pour des fonctionnalités telles que la vision, la reconnaissance vocale et la langue sans entraîner votre propre modèle à partir de zéro ?

Services d'IA Azure
Correct

Machines virtuelles Azure

Réseaux virtuels Azure 



2.3
Décrire la mise en réseau virtuel Azure, y compris les sous-réseaux et les points de terminaison

Décrire les options de connectivité avec la passerelle VPN Azure

Décrire quand utiliser Azure ExpressRoute

Décrire les fonctionnalités Azure DNS

Décrire les contrôles d’accès réseau de base pour les ressources Azure

1.

Quelle fonctionnalité réseau Azure vous permet de diviser un réseau virtuel en segments logiques plus petits ?

Sous-réseaux
Correct

Ensembles de disponibilité

Verrous de ressources
2.

Si une entreprise a besoin d’une connectivité privée et prévisible entre un centre de données local et Azure, quel service convient le mieux ?

Azure ExpressRoute

Azure Front Door - Service de passerelle réseau de Microsoft
Incorrect

Azure Load Balancer (répartiteur de charge Azure)
3.

Quel type de passerelle VPN est recommandé dans Azure pour les connexions entre les réseaux virtuels et pour les scénarios multisite ?

Passerelle VPN basée sur le routage
Correct

Passerelle VPN basée sur des stratégies

Passerelle VPN point à point
4.

Quel est l’avantage principal d’Azure DNS ?

Vous pouvez gérer des enregistrements DNS à l’aide d’informations d’identification et d’outils Azure

Il fournit un bureau d’enregistrement de domaines intégré pour tous les domaines

Elle supprime la nécessité de tous les contrôles de sécurité réseau
Incorrect



2.4
Comparer les services de stockage Azure.
Décrire les niveaux de stockage.
Décrire les options de redondance.
Décrire les options de compte de stockage et les types de stockage.
Identifier les options de déplacement de fichiers, notamment AzCopy, Explorateur Stockage Azure et Azure File Sync.
Décrire les options de migration, notamment Azure Migrate et Azure Data Box.

1.

Quel outil permet de maintenir automatiquement à jour les fichiers entre un serveur Windows local et un environnement cloud Azure ?

Azure File Sync

Explorateur de stockage Azure

AzCopy
2.

Quelle option de redondance de stockage fournit le niveau de durabilité le plus élevé, avec une durabilité de 16 neuf ?

Stockage localement redondant

Stockage redondant interzone

Stockage géoredondant interzone
3.

Quel service Stockage Azure prend en charge l’analytique Big Data ainsi que la gestion des types de données texte et binaire ?

Objets blob Azure

Azure Files

Disques Azure 
2.5
Décrivez les services d’annuaire dans Azure, notamment Microsoft Entra ID et Microsoft Entra Domain Services.
Décrire les méthodes d’authentification dans Azure, notamment l’authentification unique (SSO), l’authentification multifacteur (MFA) et sans mot de passe.
Décrire les identités externes et l’accès invité dans Azure.
Décrivez l'accès conditionnel de Microsoft Entra.
Décrire le contrôle d’accès en fonction du rôle Azure (RBAC).
Décrivez le concept de confiance zéro.
Décrire l’objectif du modèle de défense en profondeur.
Décrire les concepts de chiffrement et les options de gestion des clés dans Azure.
Décrivez l’objectif de Microsoft Defender pour cloud.

1.

Quel outil Microsoft Entra peut faire varier les informations d’identification nécessaires pour se connecter en fonction de signaux, comme l’emplacement de l’utilisateur ?

Accès conditionnel

Accès invité

Sans mot de passe
2.

Quel modèle de sécurité envisage le pire scénario de sécurité et protège les ressources en conséquence ?

Confiance Zéro

Défense en profondeur

Contrôle d’accès en fonction du rôle
3.

Un utilisateur se voit attribuer simultanément plusieurs rôles qui utilisent le contrôle d'accès basé sur les rôles. Quels sont leurs droits réels ? Les autorisations de rôle sont les suivantes : Rôle 1 - lecture || Rôle 2 - écriture || Rôle 3 - lecture et écriture.

Lecture seule

Écriture uniquement

Lecture et écriture
4.

Quel service Azure est conçu pour stocker en toute sécurité des secrets, des certificats et des clés de chiffrement pour vos applications ?

Azure Key Vault

Azure Policy

Moniteur de Azure 
3.1
Décrire les facteurs qui peuvent affecter les coûts dans Azure.
Décrire la calculatrice de prix Azure.
Décrire l’outil Microsoft Cost Management.
Décrire l’objectif des balises.
Décrire les options d’optimisation des coûts, notamment les réservations, les plans d’épargne et les tarifs Spot.

1.

Quelle est la fonctionnalité Azure qui facilite l’organisation et le suivi de l’utilisation en fonction des métadonnées associées aux ressources ?

Étiquettes

Traceurs

Valeurs
2.

Quel outil permet d’estimer le coût du déploiement des services Azure avant l’implémentation ?

Analyse des coûts Azure

Calculatrice de prix Azure

Azure Advisor
3.

Vous disposez d’une charge de travail qui peut tolérer des interruptions et qui doit s’exécuter au coût de calcul le plus bas possible. Quelle option convient généralement le mieux ?

Machines virtuelles Spot

Réservations

Paiement à l’utilisation uniquement 
3.2
Décrire l’objectif de Microsoft Purview.
Décrire l’objectif d’Azure Policy.
Décrire l’objectif des verrous de ressources.
Décrivez l’objectif du portail Service Trust.

1.

Comment empêcher la création de ressources non conformes sans devoir évaluer manuellement chaque ressource ?

Azure Policy

Microsoft Purview

Azure Moniteur de ressources
2.

Quelle est la meilleure façon d’empêcher la suppression inopinée d’une ressource ?

Azure Policy

Microsoft Purview

Verrous de ressource Azure 
3.3
Décrivez le portail Azure.
Décrire Azure Cloud Shell, notamment Azure CLI et Azure PowerShell.
Décrire l’objectif d’Azure Arc.
Décrire Azure Resource Manager (ARM), les modèles ARM et Bicep.

1.

Quel est le service qui vous aide à gérer vos environnements Azure, locaux et multiclouds ?

Azure Arc

Azure Policy

Azure Cloud Manager
2.

Quels sont les deux composants que vous pouvez utiliser pour implémenter un déploiement « infrastructure en tant que code » ?

Modèles Bicep et ARM

Azure Policy et Azure Arc

Azure Monitor et Azure Arc 
3.4
Décrire l’objectif d’Azure Advisor.
Décrire Azure Service Health.
Décrire Azure Monitor, notamment Azure Log Analytics, les alertes Azure Monitor et Application Insights.

1.

Parmi les propositions suivantes, laquelle n’est pas l’une des catégories de recommandations pour Azure Advisor ?

Fiabilité

Capacité

Coût
2.

Vous recevez une notification par e-mail indiquant que des machines virtuelles (VM) dans une région Azure où vous avez des VM déployées connaissent une panne. Quel composant d'Azure Service Health vous permettra de savoir si votre application est impactée ?

État d’Azure

Santé du service

Intégrité des ressources 



