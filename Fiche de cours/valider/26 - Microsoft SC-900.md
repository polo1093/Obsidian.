# SC-900 — Défense en profondeur

## Idée principale

La défense en profondeur consiste à protéger un système avec plusieurs couches de sécurité.

Objectif : si une couche échoue, une autre couche bloque ou ralentit l’attaque.

## Couches principales

- Sécurité physique : accès aux bâtiments, serveurs, matériel.
- Identité et accès : MFA, RBAC, accès conditionnel.
- Périmètre : pare-feu, protection DDoS.
- Réseau : segmentation, règles de trafic, NSG.
- Calcul : VM, serveurs, correctifs, ports fermés.
- Applications : code sécurisé, validation des entrées, authentification.
- Données : chiffrement, classification, droits d’accès.
<img width="1100" height="580" alt="image" src="https://github.com/user-attachments/assets/055dbc42-9fca-4086-90ea-41bf99c7a1a4" />


# Triade CIA "donne  les mots en anglais et fr"

## Confidentiality 

Seules les personnes autorisées peuvent accéder aux données.

Exemples :
- chiffrement
- droits d’accès
- MFA

## Integrity 

Les données doivent rester exactes et non modifiées sans autorisation.

Exemples :
- hachage
- signature numérique
- journaux d’audit

## Availability = Disponibilité

Les systèmes doivent rester accessibles aux utilisateurs autorisés.

Exemples :
- sauvegardes
- redondance
- protection DDoS
- plan de reprise

## Phrase examen

La défense en profondeur protège par couches.
La triade CIA protège la confidentialité, l’intégrité et la disponibilité.

# SC-900 — Modèle Confiance nulle / Zero Trust

## Idée principale

Zero Trust = ne jamais faire confiance automatiquement.

Principe :
- vérifier chaque utilisateur
- vérifier chaque appareil
- vérifier chaque accès
- même si la demande vient du réseau interne

Phrase clé :
Trust no one, verify everything.

## 3 principes Zero Trust

### 1. Vérifier explicitement

Toujours authentifier et autoriser selon plusieurs signaux :

- identité de l’utilisateur
- emplacement de connexion
- état de l’appareil
- application demandée
- niveau de risque
- sensibilité des données

### 2. Accès avec privilège minimum

Donner uniquement les droits nécessaires.

Exemples :
- MFA
- RBAC
- accès juste-à-temps
- accès juste suffisant

### 3. Supposer la violation

Partir du principe qu’un attaquant peut déjà être dans le système.

Donc il faut :
- segmenter le réseau
- surveiller les connexions
- chiffrer les données
- limiter les dégâts

## 7 piliers Zero Trust

- Identités
- Appareils
- Applications
- Données
- Infrastructure
- Réseaux
- Visibilité, automatisation et orchestration

## À retenir examen

Zero Trust n’est pas un produit.
C’est une stratégie de sécurité.

On ne fait jamais confiance par défaut.
On vérifie chaque accès, on limite les droits, et on suppose qu’une attaque peut arriver.

# SC-900 — Chiffrement et hachage

## Chiffrement

Le chiffrement rend les données illisibles sans clé.

Objectif :
- protéger les données sensibles
- empêcher la lecture par une personne non autorisée

## Types de chiffrement

### Symétrique

Même clé pour chiffrer et déchiffrer.

À retenir :
- rapide
- utile pour gros volumes de données
- problème : partager la clé en sécurité

### Asymétrique

Deux clés :
- clé publique
- clé privée

À retenir :
- la clé publique chiffre
- la clé privée déchiffre
- utilisé pour HTTPS, e-mails sécurisés, signatures numériques

## États des données

- Données au repos : stockées sur disque, base de données, cloud.
- Données en transit : envoyées sur le réseau, Internet, VPN, HTTPS.
- Données en cours d’utilisation : traitées en mémoire ou par le processeur.

## Gestion des clés

Le chiffrement dépend de la sécurité des clés.

Bonnes pratiques :
- stocker les clés séparément des données
- limiter l’accès aux clés
- faire une rotation des clés
- utiliser un service comme Azure Key Vault

# Hachage

Le hachage transforme une donnée en empreinte numérique fixe.

Différence importante :
- chiffrement = réversible avec une clé
- hachage = non réversible

## Usage principal

Stockage des mots de passe.

Le système ne stocke pas le mot de passe, mais son hachage.

## Salage

Le salage ajoute une valeur aléatoire avant le hachage.

Objectif :
- éviter que deux mêmes mots de passe aient le même hachage
- protéger contre les attaques par dictionnaire et tables arc-en-ciel

## Phrase examen

Chiffrement = protéger la confidentialité.
Hachage = vérifier l’intégrité ou stocker un mot de passe sans le garder en clair.
Salage = renforcer le hachage des mots de passe.
# SC-900 — GRC

## GRC = Gouvernance, Risque, Conformité

### Gouvernance
Règles, processus et responsabilités de sécurité.

Exemples :
- qui a accès à quoi
- qui peut être admin
- comment les données sont classifiées
- quelles politiques appliquer

### Risque
Identifier, évaluer et traiter les menaces.

Cycle :
- identifier
- évaluer
- répondre
- surveiller

Réponses possibles :
- accepter le risque
- réduire le risque
- transférer le risque
- éviter le risque

### Conformité
Respect des lois, normes et règlements.

Exemples :
- ISO 27001
- SOC 2
- HIPAA

## À retenir

La conformité n’est pas la même chose que la sécurité.

Une entreprise peut être conforme au minimum légal, mais rester vulnérable.


# SC-900 — Authentification et autorisation

## Authentification

Vérifie l’identité.

Question :
Qui êtes-vous ?

Exemples :
- mot de passe
- code PIN
- téléphone
- empreinte digitale
- reconnaissance faciale
- clé de sécurité

## Facteurs d’authentification

- Quelque chose que je connais : mot de passe, PIN
- Quelque chose que je possède : téléphone, clé de sécurité
- Quelque chose que je suis : biométrie

## MFA

MFA = authentification multifacteur.

## Autorisation

Détermine les droits après authentification.

Question :
Que pouvez-vous faire ?

Exemples :
- lire un fichier
- modifier un document
- supprimer une ressource
- accéder à une application

## À retenir

L’authentification arrive d’abord.
L’autorisation arrive ensuite.

Phrase examen :
Authentification = vérifier qui tu es.
Autorisation = vérifier ce que tu as le droit de faire.

# SC-900 — Identité = nouveau périmètre

## Idée principale

Avant, la sécurité reposait surtout sur le réseau interne :
- pare-feu
- VPN
- réseau d’entreprise

Aujourd’hui, ce modèle suffit moins parce que les utilisateurs travaillent :
- à distance
- sur des appareils personnels
- avec des applications cloud
- avec des partenaires externes

## Nouveau périmètre

Le nouveau périmètre de sécurité, c’est l’identité.

Question principale :
Qui ou quoi demande l’accès ?

## Types d’identités

- Utilisateurs : employés, clients, partenaires
- Appareils : PC, téléphones, tablettes, IoT
- Charges de travail : applications, services, scripts, API
- Agents IA : agents autonomes ou assistants IA
<img width="1430" height="975" alt="image" src="https://github.com/user-attachments/assets/f45ec679-b27a-49af-a91d-fd575249c871" />

## 4 piliers de l’identité

### Administration
Créer, modifier et supprimer les identités.

### Authentification
Vérifier qui est l’identité.

### Autorisation
Définir ce que l’identité peut faire.

### Audit
Suivre les connexions et les actions.

## Phrase examen

Dans un environnement cloud et hybride, on ne protège plus seulement un réseau : on vérifie les identités, leurs droits, leurs appareils et leurs activités.

# SC-900 — Fournisseur d’identité

## Idée principale

Un fournisseur d’identité gère l’authentification et l’autorisation pour plusieurs applications.

Exemple :
- Microsoft Entra ID
- Google
- GitHub
- LinkedIn

## Rôle

Le fournisseur d’identité :
- vérifie l’identité de l’utilisateur
- applique les règles MFA
- émet des jetons de sécurité
- centralise les connexions
- facilite le retrait des accès

## Jetons

### Jeton d’ID
Prouve que l’utilisateur est connecté.

Question :
Qui est l’utilisateur ?

### Jeton d’accès
Autorise l’accès à une ressource.

Question :
Que peut faire l’application ?

## Protocoles importants

- OIDC : authentification moderne
- OAuth 2.0 : autorisation
- SAML : souvent utilisé en entreprise / anciennes applications

## SSO

SSO = authentification unique.

L’utilisateur se connecte une fois, puis accède à plusieurs applications sans se reconnecter.

## Phrase examen

Un fournisseur d’identité comme Microsoft Entra ID centralise l’authentification, émet des jetons et permet le SSO.

# SC-900 — Services d’annuaire, AD DS et Entra ID

## Service d’annuaire

Un service d’annuaire stocke les informations d’identité.

Exemples d’objets :
- utilisateurs
- groupes
- ordinateurs
- applications
- stratégies

Il répond à :
- Qui est cet utilisateur ?
- À quels groupes appartient-il ?
- À quoi a-t-il accès ?

## Active Directory Domain Services

AD DS = service d’annuaire local Microsoft.

Il sert à :
- gérer les utilisateurs et ordinateurs d’un domaine
- authentifier les connexions
- appliquer des GPO
- organiser les objets avec des OU
- utiliser Kerberos / NTLM

Le serveur AD DS s’appelle un contrôleur de domaine.

## Limites d’AD DS

AD DS est surtout conçu pour le réseau local.

Limites :
- pas natif pour les apps cloud
- moins adapté au télétravail
- nécessite souvent VPN ou synchronisation
- ne gère pas nativement iOS/Android
- pas conçu pour OAuth / OIDC

## Microsoft Entra ID

Entra ID = gestion des identités cloud Microsoft.

Il sert à :
- gérer les identités cloud
- utiliser MFA et SSO
- accéder aux applications SaaS
- gérer les accès depuis Internet
- supporter les identités hybrides

## Phrase examen

AD DS est centré sur le domaine local.
Microsoft Entra ID est centré sur le cloud, le SaaS et l’identité moderne.


# SC-900 — Fédération

## Idée principale

La fédération permet à un utilisateur d’accéder à une ressource externe avec son compte existant.

Exemple :
Un utilisateur d’une entreprise B accède à une application de l’entreprise A avec son propre compte B.

## Principe

Deux fournisseurs d’identité établissent une relation de confiance.

L’utilisateur n’a pas besoin de créer un nouveau compte dans l’autre organisation.

## Exemples

- Collaboration B2B entre entreprises
- Connexion avec Google, Microsoft ou GitHub
- Accès cloud avec une identité Active Directory locale
- AD FS pour fédérer une identité locale vers des services externes

## Point important

La confiance n’est pas forcément bidirectionnelle.

Si A fait confiance à B, cela ne veut pas dire que B fait confiance à A.

## Phrase examen

La fédération permet d’utiliser une identité existante pour accéder à des ressources d’une autre organisation grâce à une relation de confiance entre fournisseurs d’identité.
