# Microsoft SC-900 — sécurité, conformité et identité

![SC-900](https://img.shields.io/badge/Microsoft-SC--900-512BD4?style=flat-square&logo=microsoft&logoColor=white)
![Zero Trust](https://img.shields.io/badge/Modèle-Zero%20Trust-C62828?style=flat-square)

> **Objectif :** comprendre les principes fondamentaux de sécurité et les principales familles de solutions Microsoft.

## Responsabilité partagée

Le fournisseur protège l'infrastructure du service selon le modèle utilisé. L'organisation reste notamment responsable de ses identités, de ses données, de ses appareils, de ses configurations et de ses accès.

## Zero Trust

Trois principes :

1. **vérifier explicitement** avec plusieurs signaux;
2. appliquer le **moindre privilège**;
3. **supposer une compromission** et limiter son impact.

Zero Trust n'est pas un produit unique : c'est une manière de concevoir les contrôles.

## Identité et accès

| Concept | Utilité |
| --- | --- |
| Authentification | vérifier qui se connecte |
| Autorisation | déterminer ce que l'identité peut faire |
| MFA | ajouter un facteur indépendant |
| SSO | réduire les connexions répétées |
| Accès conditionnel | appliquer des règles selon les signaux |
| RBAC | attribuer des droits selon un rôle |
| PIM | limiter et surveiller les privilèges élevés |

## Défense en profondeur

Couches complémentaires :

- sécurité physique;
- identité;
- périphériques;
- réseau;
- applications;
- données;
- supervision et réponse.

Aucune couche ne doit être considérée comme infaillible.

## Familles de solutions Microsoft

- **Microsoft Entra** : identité et accès;
- **Microsoft Defender** : prévention, détection et réponse;
- **Microsoft Sentinel** : analyse centralisée et automatisation de la réponse;
- **Microsoft Purview** : gouvernance, protection et conformité des données;
- **Microsoft Priva** : gestion de certains enjeux de confidentialité.

Les capacités exactes dépendent des licences et évoluent : toujours confirmer dans la documentation officielle.

## Réflexes du technicien

- ne jamais approuver une demande MFA inattendue;
- confirmer l'identité avant de réinitialiser un accès;
- retirer les droits devenus inutiles;
- protéger les comptes d'administration;
- signaler rapidement une activité anormale;
- conserver les journaux nécessaires;
- ne pas désactiver une protection uniquement pour contourner un problème.

## Scénario

Un utilisateur reçoit plusieurs demandes MFA qu'il n'a pas initiées. Lui demander de les refuser, protéger le compte, vérifier les connexions et jetons, réinitialiser les secrets selon la procédure et escalader comme incident potentiel.

---

[← Sommaire](./README.md) · [Microsoft Azure AZ-900 →](./31%20-%20Microsoft%20Azure%20AZ-900.md)
