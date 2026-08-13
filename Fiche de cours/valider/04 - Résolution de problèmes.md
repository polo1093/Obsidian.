# Diagnostic et résolution de problèmes

![Méthode](https://img.shields.io/badge/Méthode-Structurée-0A66C2?style=flat-square)
![Priorité](https://img.shields.io/badge/Priorité-Données%20et%20sécurité-C62828?style=flat-square)

> **Objectif :** résoudre un incident de manière reproductible, sécuritaire et compréhensible pour l'utilisateur.

## La démarche en sept étapes

1. **Écouter et reformuler** le problème.
2. **Établir les faits** : symptômes, portée, changements récents et impact.
3. **Protéger les données** et évaluer les risques.
4. **Formuler des hypothèses** classées par probabilité et coût de vérification.
5. **Tester une variable à la fois**, du moins intrusif au plus intrusif.
6. **Appliquer et valider** la solution avec l'utilisateur.
7. **Documenter** la cause, les actions, le résultat et la prévention.

## Questions utiles à l'utilisateur

- Depuis quand le problème existe-t-il?
- Le problème touche-t-il une seule personne ou plusieurs?
- Que s'est-il passé juste avant?
- Quel est le message exact?
- Le problème est-il constant ou intermittent?
- Qu'avez-vous déjà essayé?
- Existe-t-il une échéance ou un impact opérationnel urgent?

> **Important :** distinguer ce que l'utilisateur rapporte de ce que le technicien observe.

## Priorisation

| Niveau | Exemple | Réaction |
| --- | --- | --- |
| Critique | service essentiel indisponible, risque de sécurité | isoler, escalader et communiquer immédiatement |
| Élevé | plusieurs utilisateurs bloqués | rétablir le service et rechercher la cause |
| Normal | incident individuel avec contournement | traiter selon l'ordre convenu |
| Faible | demande d'information ou amélioration | planifier et documenter |

## Outils Windows utiles

~~~powershell
Get-ComputerInfo
Get-Service
Get-Process
Get-WinEvent -LogName System -MaxEvents 20
Test-Connection 8.8.8.8 -Count 2
Test-NetConnection example.com -Port 443
ipconfig /all
nslookup example.com
~~~

## Validation de la solution

Une réparation n'est pas terminée lorsqu'une commande réussit. Il faut :

- reproduire le scénario initial;
- vérifier la fonction principale et les fonctions connexes;
- confirmer avec l'utilisateur;
- surveiller les erreurs récentes;
- supprimer les solutions temporaires devenues inutiles;
- préciser quoi faire si le problème revient.

## Escalade

Escalader lorsque :

- les droits requis dépassent le mandat;
- des données risquent d'être perdues;
- un incident de sécurité est possible;
- le service touche plusieurs clients;
- le temps investi dépasse le seuil prévu;
- une expertise ou une garantie fournisseur est nécessaire.

L'escalade doit comprendre le symptôme, l'impact, l'environnement, les tests effectués, leurs résultats et les journaux pertinents.

## Modèle de note de billet

~~~text
Utilisateur / appareil :
Impact et urgence :
Symptôme exact :
Contexte et changements récents :
Tests effectués et résultats :
Cause retenue :
Solution appliquée :
Validation avec l'utilisateur :
Prévention / suivi :
~~~

## Erreurs fréquentes

- appliquer plusieurs changements simultanément;
- supposer que la cause est connue;
- réinstaller trop tôt;
- oublier la sauvegarde;
- utiliser un compte administrateur sans justification;
- fermer le billet sans validation;
- documenter uniquement « problème réglé ».

## Mise en situation

Un utilisateur accède à Internet par adresse IP, mais pas par nom de domaine. Vérifier d'abord la configuration DNS, tester une résolution avec **nslookup**, comparer avec un poste fonctionnel, vider le cache seulement si cela est pertinent, puis documenter le serveur DNS en cause.

---

[← Sommaire](./README.md) · [Scripts et automatisation →](./07%20-%20Scripts%20et%20automatisation.md)
