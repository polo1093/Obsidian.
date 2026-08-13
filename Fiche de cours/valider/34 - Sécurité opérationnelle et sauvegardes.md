# Sécurité opérationnelle et sauvegardes

![Sécurité](https://img.shields.io/badge/Sécurité-Défense%20en%20profondeur-C62828?style=flat-square)
![Sauvegarde](https://img.shields.io/badge/Sauvegarde-3--2--1--1--0-2E7D32?style=flat-square)

> **Objectif :** réduire les risques quotidiens, reconnaître un incident et garantir la récupération des données.

## Hygiène de sécurité

- appliquer rapidement les mises à jour selon le processus;
- utiliser MFA;
- retirer les logiciels et comptes inutiles;
- appliquer le moindre privilège;
- chiffrer les appareils;
- protéger les comptes d'administration;
- centraliser les journaux utiles;
- sensibiliser sans blâmer les utilisateurs;
- tester les restaurations.

## Signes d'incident

- demandes MFA non initiées;
- connexion depuis un lieu inhabituel;
- fichiers renommés ou chiffrés;
- antivirus désactivé;
- création de compte inattendue;
- règle de transfert de courrier inconnue;
- trafic ou processus anormal;
- perte d'un appareil contenant des données.

## Première réaction

1. ne pas détruire les preuves;
2. isoler l'appareil si la procédure le prévoit;
3. prévenir immédiatement le responsable;
4. noter l'heure, l'utilisateur et les observations;
5. éviter les actions non autorisées;
6. préserver les journaux;
7. suivre le plan de réponse aux incidents.

## Sauvegarde 3-2-1-1-0

- **3** copies des données;
- **2** types de support;
- **1** copie hors site;
- **1** copie hors ligne ou immuable;
- **0** erreur lors des vérifications et restaurations testées.

La synchronisation n'est pas nécessairement une sauvegarde : une suppression ou un chiffrement peut être synchronisé.

## RPO et RTO

| Mesure | Question |
| --- | --- |
| RPO | quelle quantité de données peut-on perdre? |
| RTO | combien de temps le service peut-il rester indisponible? |

Ces objectifs déterminent la fréquence des copies et la stratégie de reprise.

## Test de restauration

Un test doit préciser :

- les données et systèmes ciblés;
- le point de restauration;
- le temps nécessaire;
- l'intégrité du résultat;
- les écarts observés;
- les mesures correctives;
- la date du prochain test.

## Hameçonnage

Ne pas cliquer ni répondre. Vérifier le domaine, signaler selon la procédure et confirmer toute demande urgente par un canal indépendant. Si l'utilisateur a fourni ses identifiants, traiter immédiatement comme une compromission potentielle.

---

[← Sommaire](./README.md) · [Documentation et inventaire →](./35%20-%20Documentation%20et%20gestion%20du%20parc.md)
