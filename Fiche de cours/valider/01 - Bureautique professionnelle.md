# Bureautique professionnelle et validation de documents

![Word](https://img.shields.io/badge/Word-Documents-2B579A?style=flat-square&logo=microsoftword&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-Données-217346?style=flat-square&logo=microsoftexcel&logoColor=white)
![Visio](https://img.shields.io/badge/Visio-Schémas-3955A3?style=flat-square&logo=microsoftvisio&logoColor=white)

> **Objectif :** produire, vérifier et partager des documents professionnels sans altérer les données ni la mise en page.

## Repères rapides

| Besoin | Outil ou méthode |
| --- | --- |
| Coller sans importer une mise en forme indésirable | Collage spécial → texte uniquement |
| Vérifier les modifications | Suivi des modifications et commentaires |
| Structurer des données | Tableau Word ou tableau structuré Excel |
| Contrôler une feuille avant partage | Formules, filtres, validation et aperçu d'impression |
| Représenter un réseau ou un processus | Visio avec formes alignées et connecteurs |

## Word — produire un document propre

- utiliser les **styles** Titre 1, Titre 2 et Normal plutôt qu'une mise en forme manuelle;
- conserver une hiérarchie cohérente et générer la table des matières à partir des styles;
- utiliser **Ctrl + Alt + V** pour choisir le type de collage;
- activer le **suivi des modifications** lors d'une révision collaborative;
- ajouter des commentaires pour expliquer une correction sans modifier le texte;
- répéter la ligne d'en-tête des tableaux qui passent sur plusieurs pages;
- utiliser un espace insécable avec **Ctrl + Maj + Espace** pour éviter une coupure incorrecte.

## Excel — contrôler les données

Avant de partager un classeur :

1. vérifier les types de données et les formats;
2. rechercher les cellules vides ou incohérentes;
3. utiliser un tableau structuré pour faciliter les filtres;
4. protéger uniquement les cellules qui doivent l'être;
5. vérifier les formules et les références absolues;
6. supprimer les données personnelles inutiles;
7. contrôler l'aperçu avant impression.

### Fonctions utiles

| Fonction | Usage |
| --- | --- |
| **NBVAL** | compter les cellules non vides |
| **SI** | appliquer une condition |
| **SIERREUR** | afficher un résultat contrôlé en cas d'erreur |
| **RECHERCHEX** | retrouver une valeur dans un tableau moderne |
| **SOMME.SI.ENS** | additionner selon plusieurs critères |

> **Bon réflexe :** ne jamais écraser les données sources. Travailler sur une copie ou dans une colonne de résultat.

## Visio — produire un schéma lisible

- choisir un format de page avant de commencer;
- utiliser une seule convention pour les équipements;
- aligner et distribuer les formes;
- éviter les croisements de connecteurs;
- identifier clairement les réseaux, VLAN, adresses ou rôles;
- ajouter une légende lorsque les symboles ne sont pas évidents;
- vérifier le rendu PDF avant diffusion.

## Contrôle qualité

- [ ] le document porte un titre, une date et une version;
- [ ] les liens et références fonctionnent;
- [ ] l'orthographe et la terminologie sont vérifiées;
- [ ] aucune donnée confidentielle ne reste dans le fichier;
- [ ] le nom du fichier est explicite;
- [ ] le document reste lisible sur une autre machine.

## Mise en situation

Pour transmettre un inventaire informatique : créer un tableau Excel avec le numéro d'actif, l'utilisateur, le modèle, le numéro de série, l'état et la date de vérification. Protéger les colonnes calculées, filtrer les appareils à remplacer et exporter une version PDF destinée à la direction.

---

## Notes personnelles, exercices et captures d’origine

> Cette section conserve **intégralement** le contenu personnel présent avant la refonte : formulations de cours, exercices, rappels et captures d’écran. Les sections précédentes servent de complément structuré; elles ne remplacent pas ces notes.

# 🧠 Fiche mémo — Word / Excel / Visio (cours) : 

---

## 🟦 WORD — Collage (garder la mise en forme / texte uniquement)

<table>
  <tr>
    <td valign="top" width="40%">
      <ul>
        <li>📍 <b>Accueil</b> → <b>Coller</b> ▼</li>
        <li>✅ Choix : <b>Fusionner la mise en forme</b> / <b>Conserver le texte uniquement</b></li>
        <li>⌨️ <b>Ctrl + Alt + V</b> → Collage spécial → <b>Texte sans mise en forme</b></li>
      </ul>
    </td>
    <td valign="top" width="60%" align="right">
      <img src="https://github.com/user-attachments/assets/837b7a31-bde1-4512-a0a7-9cc1edbf92b1" alt="Coller - options" width="900"/>
    </td>
  </tr>
</table>

<hr/>

## 🟦 WORD — Espaces insécables / trait d’union insécable (éviter les coupures)

* ⌨️ **Espace insécable** : **Ctrl + Maj + Espace**
* ⌨️ **Trait d’union insécable** : **Ctrl + Maj + -**

📌 Si “Ctrl+Maj+-” ne marche pas :

* utilise le **tiret du clavier principal** (pas celui du pavé numérique),
* et assure-toi d’être dans du **texte** (pas dans un champ auto).

<hr/>

## 🟦 WORD — Révision (orthographe, dictionnaire, auto-correction)

* 📍 **Révision** → **Orthographe et grammaire**
* 📍 Ajouter mot : volet de correction → **Ajouter au dictionnaire**
* 📍 Auto-correction majuscules : **Fichier** → **Options** → **Vérification** → **Options de correction automatique…**
  → activer **Mettre une majuscule en début de phrase**

<hr/>

## 🟦 WORD — Commentaires + suivi des modifications

* 📍 **Révision** → **Nouveau commentaire**
* 📍 **Révision** → **Suivi** → **Suivi des modifications** (Activer)
* 📍 **Affichage pour révision** : Simple / Toutes les marques

<hr/>

## 🟦 WORD — Tableaux (styles, tri, colonnes égales, en-tête répété)

* 📍 **Insertion** → **Tableau**
* 📍 Style “1 ligne sur 2” : **Création de tableau** → **Styles** (lignes en bande)
* 📍 Trier : **Disposition (Outils de tableau)** → **Trier** <img width="1200" height="579" alt="image" src="https://github.com/user-attachments/assets/15ffd605-1e46-478f-9c67-471855479312" />
* 📍 Colonnes égales : **Disposition** → **Distribuer les colonnes**
* 📍 Répéter ligne de titres : sélectionner la 1re ligne → **Disposition** → **Répéter les lignes d’en-tête**<img width="1086" height="465" alt="image" src="https://github.com/user-attachments/assets/f9302d61-e6e1-46e6-9510-ccdf9cbd15e2" />
* 📍 Centrer le tableau : clic droit → **Propriétés du tableau** → Alignement **Centré**

<hr/>

## 🟦 WORD — Protection (formulaire)

* 📍 **Révision** → **Restreindre la modification**
* ✅ Autoriser : **Remplissage de formulaires**
* 🔐 **Oui, activer la protection** → mot de passe (ex. `Form123`)

<hr/>

## 🟨 EXCEL — Raccourcis & basiques utiles

* ⌨️ **Ctrl + 1** : **Format de cellule** (hyper pratique)
* 🧮 **NBVAL()** : compte les cellules **non vides**
  Exemple : `=NBVAL(A2:A100)`

<table>
  <tr>
    <td valign="top" width="40%">
      <ul>
        <li>📍 Format cellule : <b>Ctrl + 1</b></li>
        <li>📍 Nombre / Monétaire / Date / Alignement</li>
      </ul>
    </td>
    <td valign="top" width="60%" align="right">
      <img src="https://github.com/user-attachments/assets/d8b57bc3-7690-4dc2-8519-de38950ecd4b" alt="Format de cellule" width="900"/>
    </td>
  </tr>
</table>

<hr/>

## 🟨 EXCEL — Remplissage instantané (Flash Fill)

<table>
  <tr>
    <td valign="top" width="40%">
      <ul>
        <li>🎯 Objectif : fusionner Prénom + Nom, ou extraire des morceaux</li>
        <li>1) Tape un exemple</li>
        <li>2) <b>Ctrl + E</b> → Excel complète</li>
      </ul>
    </td>
    <td valign="top" width="60%" align="right">
      <img src="https://github.com/user-attachments/assets/ea1bcbeb-d853-4506-8b04-4bddcd6e19d2" alt="Remplissage instantané" width="900"/>
    </td>
  </tr>
</table>

<hr/>

## 🟨 EXCEL — Saut de ligne dans une cellule

* ⌨️ **Alt + Entrée**

<hr/>

## 🟨 EXCEL — Masquer lignes / colonnes

<table>
  <tr>
    <td valign="top" width="40%">
      <ul>
        <li>📍 Clic droit sur numéro de ligne / lettre de colonne</li>
        <li>→ <b>Masquer</b></li>
        <li>📍 Pour ré-afficher : sélectionner autour → clic droit → <b>Afficher</b></li>
      </ul>
    </td>
    <td valign="top" width="60%" align="right">
      <img src="https://github.com/user-attachments/assets/5a37100e-1edf-4295-8dd1-7bf376d7dcb6" alt="Masquer" width="700"/>
    </td>
  </tr>
</table>

<hr/>

## 🟨 EXCEL — Centrer horizontalement sur la page (impression)

<table>
  <tr>
    <td valign="top" width="40%">
      <ul>
        <li>📍 <b>Mise en page</b> → <b>Marges</b> → <b>Marges personnalisées</b></li>
        <li>✅ Cocher : <b>Centrer sur la page → Horizontalement</b></li>
      </ul>
    </td>
    <td valign="top" width="60%" align="right">
      <img src="https://github.com/user-attachments/assets/9db8382c-5325-4ea9-9541-8be81f1bd83d" alt="Centrer sur la page" width="900"/>
    </td>
  </tr>
</table>

<hr/>

## 🟨 EXCEL — Figer les 3 premières colonnes (A à C)

<table>
  <tr>
    <td valign="top" width="40%">
      <ul>
        <li>1) Clique en <b>D1</b> (juste à droite des 3 colonnes)</li>
        <li>2) <b>Affichage</b> → <b>Figer les volets</b> → <b>Figer les volets</b></li>
      </ul>
    </td>
    <td valign="top" width="60%" align="right">
      <img src="https://github.com/user-attachments/assets/a22d02ae-4abf-4dac-b54b-5f24df998c15" alt="Figer les volets" width="900"/>
    </td>
  </tr>
</table>

<hr/>

## 🟨 EXCEL — Fonctions financières (cours)

* 📌 **Investissement (valeur future)** : `VF(taux/12; nb_annees*12; montant)`
* 📌 **Emprunt (valeur actuelle)** : `VA(taux/12; nb_annees*12; montant)`

> Astuce : si tu veux un résultat “positif”, il faut souvent mettre le **montant en négatif** (logique flux de trésorerie).

<hr/>

## 🟦 VISIO — Mettre le format Lettre US + tout tenir sur 1 page

<table>
  <tr>
    <td valign="top" width="40%">
      <ul>
        <li>📍 <b>Conception</b> → <b>Taille</b> → <b>Lettre (US)</b></li>
        <li>📍 Puis : <b>Mise en page / Page Setup</b> → <b>Ajuster à</b> : <b>1 page × 1 page</b></li>
        <li>✅ Vérif : <b>Fichier</b> → <b>Imprimer</b> (aperçu = 1 page)</li>
      </ul>
    </td>
    <td valign="top" width="60%" align="right">
      <img src="https://github.com/user-attachments/assets/685621e3-1443-4ccb-8f14-3eefd4ee57ec" alt="Visio - format Lettre US" width="900"/>
    </td>
  </tr>
</table>

<hr/>

## 🟦 VISIO — Align / Distribute + Snap (rendu “propre”)

* 📍 **Affichage (View)** → **Snap & Glue** → activer **Snap**
* 📍 **Home** → **Arrange** → **Align / Position / Distribute**
* ⌨️ Astuce : maintenir **Shift** pour lignes parfaitement droites (selon connecteur)
