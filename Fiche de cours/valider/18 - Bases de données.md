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

## Notes personnelles, exercices et captures d’origine

> Cette section conserve **intégralement** le contenu personnel présent avant la refonte : formulations de cours, exercices, rappels et captures d’écran. Les sections précédentes servent de complément structuré; elles ne remplacent pas ces notes.

Je ne sais pas refaire les relation 1 a infini au lieu de 1a1

import de execl expoeter requetes et etats

regrouper et trier etat
<img width="1917" height="1027" alt="image" src="https://github.com/user-attachments/assets/924e7f15-54a5-43da-81ae-9b53bdf1bbe1" />

Formulaires ordre d organinisation ne pas forcement garder
<img width="386" height="441" alt="image" src="https://github.com/user-attachments/assets/56106048-574b-4a86-a2bf-a7df9fd35aa2" />
<img width="1721" height="1039" alt="image" src="https://github.com/user-attachments/assets/82081b0b-0ad8-46b0-8c97-31ee8e7043e6" />


operations somme min sur une requete
<img width="1869" height="998" alt="image" src="https://github.com/user-attachments/assets/afc6bad8-f2a6-4d17-9be6-e19dd1a84812" />



filtre rapide
<img width="1598" height="725" alt="image" src="https://github.com/user-attachments/assets/aae5bccc-2bfb-4ba5-9610-541510234925" />

modifie le farmaat paysage lors de l exportage
<img width="869" height="560" alt="image" src="https://github.com/user-attachments/assets/e4c93aef-fc7b-4e1b-9484-12b60d12ab53" />


rapport de relations 
<img width="1501" height="779" alt="image" src="https://github.com/user-attachments/assets/f93f1e2c-ce4c-4cd5-a0e6-ed5fa231340a" />

importer des donnes de Excel
<img width="1321" height="808" alt="image" src="https://github.com/user-attachments/assets/aabb4a94-e546-4849-90b9-ac6d0f455f93" />

et soigner la presentations vers execl
