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

[← Sommaire](./README.md) · [Outlook et Microsoft 365 →](./24%20-%20Outlook.md)
