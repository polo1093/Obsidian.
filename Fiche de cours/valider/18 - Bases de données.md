# Bases de données pour le soutien informatique

![SQL](https://img.shields.io/badge/SQL-Requêtes-336791?style=flat-square)
![Données](https://img.shields.io/badge/Principe-Intégrité-2E7D32?style=flat-square)

> **Objectif :** comprendre la structure d'une base relationnelle et effectuer des recherches simples sans compromettre les données.

## Concepts essentiels

| Concept | Définition |
| --- | --- |
| Table | ensemble d'enregistrements d'un même type |
| Ligne | un enregistrement |
| Colonne | une propriété ou un champ |
| Clé primaire | identifiant unique d'une ligne |
| Clé étrangère | référence vers une autre table |
| Index | structure qui accélère certaines recherches |
| Contrainte | règle garantissant l'intégrité des données |
| Transaction | groupe d'opérations traité comme une unité |

## Requêtes de lecture

~~~sql
SELECT id, nom, statut
FROM equipements
WHERE statut = 'À vérifier'
ORDER BY nom;
~~~

Limiter les colonnes et les lignes rend la requête plus claire et réduit les risques d'exposer des données inutiles.

### Agrégation

~~~sql
SELECT statut, COUNT(*) AS nombre
FROM equipements
GROUP BY statut
ORDER BY nombre DESC;
~~~

### Jointure

~~~sql
SELECT e.nom, u.nom AS utilisateur
FROM equipements AS e
LEFT JOIN utilisateurs AS u
  ON e.utilisateur_id = u.id;
~~~

## Modifications : précautions

Avant **UPDATE** ou **DELETE** :

1. sauvegarder ou confirmer la restauration possible;
2. exécuter d'abord le même filtre avec **SELECT**;
3. vérifier le nombre de lignes ciblées;
4. utiliser une transaction si le système le permet;
5. journaliser la demande et le résultat;
6. ne jamais travailler directement en production sans autorisation.

~~~sql
BEGIN TRANSACTION;

UPDATE equipements
SET statut = 'En service'
WHERE id = 42;

COMMIT;
-- ou annuler avec ROLLBACK;
~~~

## Sauvegarde et restauration

Une sauvegarde n'est utile que si la restauration a été testée. Documenter :

- la fréquence;
- la rétention;
- l'emplacement;
- le chiffrement;
- le responsable;
- le résultat des tests de restauration.

## Mise en situation

Pour rechercher un poste dans un inventaire, interroger uniquement les champs nécessaires avec son numéro d'actif. Ne pas exporter toute la table des utilisateurs dans un fichier local.

---

[← Sommaire](./README.md) · [Déploiement →](./19%20-%20Déploiement.md)
