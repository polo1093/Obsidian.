# Réseaux avancés et administration à distance

![Réseau](https://img.shields.io/badge/Réseau-VLAN%20%7C%20VPN%20%7C%20Pare--feu-0A66C2?style=flat-square)
![Supervision](https://img.shields.io/badge/Exploitation-Supervision-2E7D32?style=flat-square)

> **Objectif :** comprendre la segmentation, l'accès distant et la supervision d'un environnement professionnel.

## Segmentation et VLAN

Un VLAN sépare logiquement les équipements. Son utilité dépend d'un plan d'adressage, d'un routage inter-VLAN et de règles de pare-feu cohérentes.

Exemples de segments :

- postes utilisateurs;
- serveurs;
- téléphonie;
- invités;
- équipements de gestion;
- objets connectés.

Le principe est de permettre uniquement les communications nécessaires.

## VPN

| Type | Usage |
| --- | --- |
| Site à site | relier durablement deux réseaux |
| Accès distant | connecter un utilisateur autorisé |
| Client à site | donner accès à des ressources internes précises |

Appliquer MFA, chiffrement moderne, journalisation et moindre privilège. Un VPN ne rend pas automatiquement un poste personnel digne de confiance.

## Pare-feu

Une règle doit préciser :

- source;
- destination;
- protocole et port;
- action;
- justification;
- propriétaire;
- durée ou date de révision.

Éviter les règles « any-any ». Tester le service attendu et contrôler les journaux de refus.

## Administration distante

- utiliser un canal chiffré et approuvé;
- confirmer l'identité de l'utilisateur;
- obtenir son accord avant de prendre le contrôle;
- expliquer les actions visibles;
- masquer ou fermer les données sensibles;
- déconnecter la session à la fin;
- documenter les opérations.

## Supervision

Mesures utiles :

- disponibilité;
- espace disque;
- CPU et mémoire;
- latence et perte de paquets;
- état des sauvegardes;
- certificats arrivant à expiration;
- erreurs applicatives;
- état des services critiques.

Une alerte doit être actionnable : seuil pertinent, contexte, responsable et procédure.

## Commandes de diagnostic

~~~powershell
Get-NetAdapter
Get-NetIPConfiguration
Get-NetRoute
Get-NetTCPConnection
Test-NetConnection server.example -Port 443
Get-Counter '\Processor(_Total)\% Processor Time'
Get-WinEvent -LogName System -MaxEvents 30
~~~

## Mise en situation

Un service fonctionne localement sur le serveur, mais pas depuis un autre VLAN. Vérifier l'écoute du service, la route, les règles inter-VLAN et le pare-feu du serveur avant de modifier DNS.

---

[← Sommaire](./README.md) · [Microsoft SC-900 →](./26%20-%20Microsoft%20SC-900.md)
