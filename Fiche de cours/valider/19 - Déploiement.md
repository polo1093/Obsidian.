# Préparation et déploiement de postes

![Windows](https://img.shields.io/badge/Windows-Déploiement-0078D4?style=flat-square&logo=windows11&logoColor=white)
![Qualité](https://img.shields.io/badge/Processus-Reproductible-2E7D32?style=flat-square)

> **Objectif :** livrer un poste sécurisé, conforme et prêt à l'emploi grâce à une procédure reproductible.

## Avant le déploiement

- confirmer le besoin, le rôle et les logiciels autorisés;
- enregistrer le numéro de série et le numéro d'actif;
- vérifier la compatibilité matérielle;
- utiliser une image et des sources approuvées;
- protéger les données de l'ancien poste;
- planifier le retour arrière;
- préparer les licences et accès nécessaires.

## Séquence recommandée

1. mettre à jour le micrologiciel lorsque cela est justifié;
2. installer ou réinitialiser Windows avec la bonne édition;
3. appliquer les mises à jour système et pilotes;
4. nommer l'appareil selon la convention;
5. joindre l'appareil au domaine ou au service de gestion;
6. appliquer les politiques de sécurité;
7. installer les applications approuvées;
8. configurer l'utilisateur sans lui donner de droits excessifs;
9. restaurer les données autorisées;
10. exécuter les tests de validation;
11. remettre le poste et obtenir une confirmation.

## Validation technique

- [ ] chiffrement actif et clé récupérable;
- [ ] antivirus ou EDR opérationnel;
- [ ] pare-feu actif;
- [ ] mises à jour terminées;
- [ ] réseau, DNS et impression testés;
- [ ] Microsoft 365 et applications accessibles;
- [ ] sauvegarde ou synchronisation confirmée;
- [ ] inventaire et garantie documentés;
- [ ] compte local temporaire supprimé ou désactivé.

## Migration des données

Classer les données avant le transfert :

- **à transférer** : documents de travail autorisés;
- **à recréer** : applications et paramètres gérés;
- **à exclure** : caches, exécutables inconnus et données personnelles non autorisées;
- **à conserver temporairement** : sauvegarde chiffrée avec date de suppression prévue.

## Automatisation

Une tâche de déploiement doit être **idempotente** : une seconde exécution ne doit pas endommager le poste. Les scripts doivent produire des journaux, vérifier leurs prérequis et signaler clairement les échecs.

## Mise en situation

Lors d'un remplacement de poste, conserver l'ancien appareil intact jusqu'à ce que l'utilisateur confirme l'accès à ses fichiers, ses applications et ses périphériques. Effacer l'ancien disque seulement après autorisation et selon la politique.

---

[← Sommaire](./README.md) · [Réparation informatique →](./23%20-%20Réparation%20informatique.md)
