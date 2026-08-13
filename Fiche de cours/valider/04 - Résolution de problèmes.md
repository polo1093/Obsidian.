# Fiche de révision (anglais) — Résolution de problèmes (prétest → examen final)

> Objectif : une fiche **utile en examen** (sans corriger le prétest), calée sur le format des questions Q1→Q7 du cahier. 

---

## 0) Règles de copie “niveau examen” ✅

* Écrire **factuel**, **court**, **vérifiable** (pas d’opinion, pas de blabla).
* Toujours structurer en **puces** (gain de points + lisibilité).
* Ne pas “résoudre” quand on te demande seulement **constat / anomalies**. 

---

## Q1 — Relevé complet des anomalies (sans solution) 🔎

**But :** sortir *tout* ce qui est pertinent dans le récit (symptômes + contexte + tests déjà faits).

### Checklist à appliquer

* **Symptôme déclaré** par le client vs **symptôme constaté** (différence = info clé).
* **Ce qui fonctionne** (ex. voyant allumé, BIOS visible) et **ce qui ne fonctionne pas**.
* **Moment d’apparition** (au boot, au chargement Windows, après MAJ, après crash).
* **Mode normal vs mode sans échec**, périphériques impliqués, messages, artefacts, bruit, odeur, etc.
* **Tests déjà réalisés** (et leurs résultats).

👉 Format de sortie recommandé :

* Faits observés
* Tests/constats
* Conditions d’apparition (quand/comment)

---

## Q2 — Choisir le scénario “clair et concis” 🧠

**Règle :** choisir celui qui **décrit le problème**, pas celui qui vend déjà la solution.

### Grille de sélection

* **Factuel** : pas d’intentions (“il vous arnaque”), pas de jugement (“il sait pas s’en servir”).
* **Centré sur l’enjeu** : reprend le symptôme principal + contexte.
* **Neutre** : ne suppose pas une cause non prouvée (surchauffe, écran usé, etc.).

---

## Q3 — “Éliminer 2 causes” (diagnostic logique) 🚫

**But :** enlever les causes **hors-sujet** ou **incompatibles** avec l’énoncé.

### Causes typiquement éliminables

* **Contradiction directe** (ex. “le client n’a pas d’imprimante” alors qu’il parle de son imprimante).
* **Hors périmètre** (ex. écran mal branché pour un problème d’impression).
* **Pas une cause** mais une action (“apporter le PC complet”).
* **Non liée au symptôme** (ex. disque dur empêche lecture CD audio).

### Mini-checklist (ultra rapide)

1. Est-ce que ça peut **empêcher** le symptôme ?
2. Est-ce que c’est **lié** au composant concerné ?
3. Est-ce compatible avec les **faits donnés** ?

---

## Q4 — Conséquences court terme vs long terme 📉

**On te demande au moins 2 / 2.** 

### Court terme (immédiat / opérationnel)

* Perte de productivité, interruptions, gels/plantages, contournements, stress, service ralenti.

### Long terme (cumulatif / business risk)

* Perte de données, panne complète, coûts récurrents, réputation, sécurité (malware/ransomware), mesures disciplinaires.

👉 Astuce : **court terme = aujourd’hui / cette semaine** ; **long terme = dans 1–3 mois**.

---

## Q5 — Hypothèses + vérification + solution + justification 🧾

**Format attendu :**

1. Problème
2. Questions au client (≥2)
3. Solution proposée
4. Justification (coût / temps / durabilité)

### Méthode pro

* **Hypothèses** : 2–3 causes plausibles, **classées** (la plus probable / la plus rapide à vérifier).
* **Vérifications** : étapes logiques du **moins intrusif** → **plus intrusif**.
* **Solution** : celle qui optimise **ROI** (coût vs résultat) et réduit les retours SAV.
* **Justification** : “réparation non rentable car ancien / récidive probable / remplacement plus fiable”.

---

## Q6 — Choisir un système à partir d’une liste de pièces (meilleur prix) 💻💰

La question Q6 te demande une config + numéros + prix total + justification. 
Tolérance sur le total : **± 50 $**. 

### Règle d’or : “minimum viable” + options demandées

* Inclure **uniquement** :

  * Les **essentiels** (pour que ça fonctionne)
  * Les **options explicitement demandées** (Blu-ray, USB, numériseur, imprimante, Internet)

### Rappels techniques (Annexe 1)

* **Carte maîtresse “onboard” (#4)** : inclut **graphique + son + réseau** → donc **pas besoin** de carte graphique (#12/#13), ni carte de son (#14/#15), ni carte réseau (#27/#28) sauf exigence spéciale. 
* **Ventilateur (#7)** : requis pour refroidir le microprocesseur (donc à prévoir dans une config assemblée). 
* **Haut-parleurs** : **ne pas ajouter par défaut** si ce n’est pas demandé (tu limites le coût et restes conforme au besoin).

### “Système de base” (pattern)

* Boîtier + alimentation + carte mère + CPU + ventilateur + RAM + disque + clavier + souris + écran
* * options demandées (ex. Blu-ray, imprimante, numériseur, clé USB)
* * Internet téléphonique : modem (#26) si l’énoncé le précise. 

### Justification type (à copier)

> “Meilleur prix : carte mère onboard pour réduire le nombre de composants, configuration minimale suffisante pour l’usage demandé, ajout uniquement des périphériques exigés.”

---

## Q7 — Rapport de résolution de problèmes (démarche complète) 🧩

Le rapport te force à montrer une démarche **structurée** (et à cocher). 

### 1. Énoncé du problème

**1.1 Éléments à considérer** : matériel, symptômes, contexte d’achat, OS, compétence utilisateur, etc.
**1.2 Problématique** : 1 phrase “symptôme + impact + contexte”.
**1.3 Contraintes** : oui/non + préciser (communication, déplacement, délai, données non fiables). 

### 2. Sources d’info

Coche ce que tu utilises vraiment :

* Personne ressource (client), manuel, fabricant, etc.

### 3. Information recueillie

* **3.1 Pistes** : lister 3–5 options (même “apporter en boutique”, “déplacement”, etc.)
* **3.2 Solution retenue** : 1 ligne
* **3.3 Vérifiable / vérifiée** :

  * si rendez-vous à venir → “vérifiable oui / vérifiée non” (logique d’audit)
* **3.4 Résultat** : ce qui est fait maintenant (ex. RDV pris)
* **3.5 Satisfaction** : souvent “non” tant que non résolu
* **3.6 Pourquoi** : “pas encore appliqué / pas de validation” 

### 4. Références

* “Infos client” + “manuel/procédure interne” (si applicable).

---

## Templates “copier-coller” (examen) 🧾

### Template Q1 (anomalies)

* Symptôme rapporté :
* Symptôme constaté :
* Ce qui fonctionne :
* Ce qui échoue :
* Conditions d’apparition :
* Tests/observations déjà faits :

### Template Q4 (conséquences)

**Court terme :**

* …
* …

**Long terme :**

* …
* …

### Template Q7 (problématique)

> “Le poste présente [symptôme]. À distance, les informations sont [fiables/non fiables], ce qui bloque le diagnostic. Une intervention [sur place/en atelier] est nécessaire pour [objectif].”

---




 important
 une carte mere one board  = need ventilateur,  , pas de carte graphique  mais besoin d un proco intel pas besoin de haut parleur par defauts


