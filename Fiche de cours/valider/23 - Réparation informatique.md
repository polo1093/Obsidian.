# Réparation informatique — matériel et Windows

![Matériel](https://img.shields.io/badge/Matériel-Diagnostic-616161?style=flat-square)
![ESD](https://img.shields.io/badge/Sécurité-ESD-C62828?style=flat-square)

> **Objectif :** diagnostiquer une panne matérielle sans mettre en danger les données, l'équipement ou le technicien.

## Sécurité avant intervention

- éteindre et débrancher l'appareil;
- retirer la batterie amovible lorsque possible;
- se protéger contre les décharges électrostatiques;
- photographier les branchements et noter les vis;
- vérifier la garantie avant d'ouvrir l'appareil;
- sauvegarder les données avant toute opération à risque;
- ne jamais travailler dans une alimentation électrique ouverte.

## Démarche de diagnostic

1. confirmer le symptôme avec l'utilisateur;
2. effectuer une inspection visuelle et olfactive;
3. vérifier alimentation, câbles et voyants;
4. retirer les périphériques non essentiels;
5. lire les codes sonores ou lumineux;
6. tester un composant ou une variable à la fois;
7. comparer avec une pièce connue fonctionnelle;
8. valider la réparation et documenter.

## Composants et symptômes

| Composant | Symptômes possibles | Vérifications |
| --- | --- | --- |
| Alimentation | aucun démarrage, arrêts | câble, prise, adaptateur, tensions par outil adapté |
| Mémoire vive | écrans bleus, redémarrages | réinstallation, test mémoire, module isolé |
| Stockage | lenteurs, erreurs, absence au démarrage | SMART, câbles, journaux, sauvegarde immédiate |
| Refroidissement | bruit, surchauffe, baisse de performance | ventilateurs, poussière, températures |
| Écran ou GPU | artefacts, écran noir | câble, autre écran, pilote, sortie vidéo |
| Carte réseau | pertes de connexion | câble, pilote, autre port, paramètres |

## Outils Windows

~~~powershell
Get-PhysicalDisk
Get-Disk
Get-Volume
Get-CimInstance Win32_BIOS
Get-CimInstance Win32_PhysicalMemory
Get-WinEvent -LogName System -MaxEvents 50
powercfg /batteryreport
~~~

## Réparation ou remplacement

Considérer :

- coût des pièces et de la main-d'œuvre;
- âge et état général;
- disponibilité des composants;
- garantie;
- risque de récidive;
- exigences de Windows et des logiciels;
- impact environnemental;
- valeur des données.

## Après l'intervention

- nettoyer sans endommager;
- remonter et contrôler tous les branchements;
- exécuter un test de stabilité;
- vérifier réseau, son, caméra, ports et alimentation;
- mettre à jour l'inventaire;
- expliquer clairement la réparation et les limites.

---

## Notes personnelles, exercices et captures d’origine

> Cette section conserve **intégralement** le contenu personnel présent avant la refonte : formulations de cours, exercices, rappels et captures d’écran. Les sections précédentes servent de complément structuré; elles ne remplacent pas ces notes.

# Réparation informatique — préparation de Windows 11

## Objectif

Vérifier la compatibilité d’un ordinateur, préparer l’installation de Windows 11 et utiliser les ressources officielles appropriées.

## Ressources Microsoft

- [Télécharger Windows 11](https://www.microsoft.com/fr-fr/software-download/windows11)
- [Utiliser l’application Contrôle d’intégrité du PC](https://support.microsoft.com/fr-fr/windows/comment-utiliser-l-application-contr%C3%B4le-d-int%C3%A9grit%C3%A9-du-pc-9c8abd9b-03ba-4e67-81ef-36f37caa7844)

## Vérifications avant intervention

- [ ] Sauvegarder les données importantes.
- [ ] Vérifier la compatibilité du processeur.
- [ ] Vérifier la mémoire vive et l’espace disque disponibles.
- [ ] Confirmer que TPM 2.0 est présent et activé.
- [ ] Confirmer que le démarrage sécurisé est disponible.
- [ ] Vérifier l’édition de Windows et l’état de la licence.
- [ ] Prévoir les pilotes réseau et les pilotes du fabricant.
- [ ] Documenter l’état initial de l’ordinateur.

## Après l’installation

- appliquer les mises à jour Windows;
- installer les pilotes manquants;
- vérifier le Gestionnaire de périphériques;
- tester le réseau, le son et les périphériques;
- réinstaller les applications nécessaires;
- restaurer les données de l’utilisateur;
- créer un point de restauration et consigner l’intervention.

## Document de travail

[Consulter les notes détaillées dans Google Docs](https://docs.google.com/document/d/15ocPGbVEtbwi7R6f1ZD7SCS98_HFMII0/edit)
