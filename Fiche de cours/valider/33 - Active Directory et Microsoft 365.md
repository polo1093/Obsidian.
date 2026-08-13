# Active Directory et Microsoft 365

![AD](https://img.shields.io/badge/Windows-Active%20Directory-0078D4?style=flat-square&logo=windows11&logoColor=white)
![M365](https://img.shields.io/badge/Microsoft-365-D83B01?style=flat-square&logo=microsoftoffice&logoColor=white)

> **Objectif :** administrer les identités et accès en respectant le moindre privilège et les procédures d'approbation.

## Active Directory

| Élément | Rôle |
| --- | --- |
| Domaine | limite logique d'administration |
| Unité d'organisation | organise les objets et facilite les politiques |
| Groupe | attribue des accès à plusieurs identités |
| GPO | applique une configuration centralisée |
| Contrôleur de domaine | fournit notamment authentification et annuaire |
| DNS | permet de localiser les services du domaine |

## Gestion d'un utilisateur

Avant toute création ou modification :

- confirmer l'identité du demandeur;
- obtenir l'approbation requise;
- utiliser la convention de nommage;
- attribuer les groupes selon le rôle;
- éviter les droits individuels;
- imposer MFA lorsque applicable;
- documenter l'expiration ou la date de révision;
- transmettre les secrets par un canal approuvé.

## Modèle d'attribution

Une approche courante consiste à placer les **comptes** dans des groupes représentant leur **rôle**, puis à attribuer les **permissions** à des groupes de ressources. Cela facilite les audits et les départs.

## Départ d'un employé

- désactiver les accès au moment autorisé;
- révoquer les sessions et jetons;
- retirer ou transférer les privilèges;
- préserver les données selon la politique;
- transférer la messagerie ou les fichiers uniquement avec approbation;
- récupérer les appareils;
- documenter chaque action.

## Microsoft 365

Points de soutien fréquents :

- licences et disponibilité des services;
- réinitialisation d'accès;
- MFA et méthodes d'authentification;
- groupes et boîtes partagées;
- Teams et SharePoint;
- synchronisation OneDrive;
- état du service;
- appareils enregistrés ou gérés.

## GPO et synchronisation

Avant de forcer ou modifier une politique :

1. confirmer la portée;
2. vérifier l'appartenance et l'unité d'organisation;
3. identifier les politiques appliquées;
4. consulter les journaux;
5. tester sur un groupe limité;
6. prévoir le retour arrière.

~~~powershell
whoami /groups
gpresult /r
gpresult /h "$env:TEMP\gpresult.html"
~~~

## Sécurité

Ne jamais ajouter un utilisateur au groupe Administrateurs simplement pour résoudre une installation. Identifier l'autorisation exacte, appliquer une solution temporaire approuvée si nécessaire et retirer l'accès ensuite.

---

[← Sommaire](./README.md) · [Sécurité opérationnelle →](./34%20-%20Sécurité%20opérationnelle%20et%20sauvegardes.md)
