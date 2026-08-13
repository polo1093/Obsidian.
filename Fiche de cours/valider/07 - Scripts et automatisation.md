Oui ✅ Voici **toutes les commandes PowerShell** qui apparaissent dans ta conversation, **remises au propre**, dans l’ordre.

---

## 1) Création conditionnelle du dossier `C:\TestBackup` (version incomplète)

```powershell
if (!(Test-Path "______")) { New-Item -Path "C:\TestBackup"
```

## 2) Création conditionnelle du dossier `C:\TestBackup` (version complète)

```powershell
if (!(Test-Path "C:\TestBackup")) { New-Item -Path "C:\TestBackup" -ItemType Directory }
```

## 3) Variante avec Get-Item (et mkdir)

```powershell
if (Get-Item "C:\TestBackup") { mkdir "C:\TestBackup" }
```

## 4) Variante “corrigée” avec Get-Item (gestion erreur silencieuse)

```powershell
if (!(Get-Item "C:\TestBackup" -ErrorAction SilentlyContinue)) { mkdir "C:\TestBackup" }
```

## 5) Création d’un dossier `C:\Backup`

```powershell
New-Item "C:\Backup" -ItemType Directory
```

## 6) Création d’un fichier vide (exemple mentionné)

```powershell
New-Item "C:\Backup\test.txt" -ItemType File
```

## 7) Copie de tous les `.txt` vers `C:\Backup`

```powershell
Copy-Item "C:\Data\*.txt" -Destination "C:\Backup" -Force
```

## 8) Suppression de tous les `.txt` dans `C:\Data`

```powershell
Remove-Item "C:\Data\*.txt" -Force
```

## 9) Affichage console — copie

```powershell
Write-Host "Copie terminée avec succès"
```

## 10) Affichage console — sauvegarde

```powershell
Write-Host "Sauvegarde terminée avec succès"
```

## 11) Affichage console — début (proposition)

```powershell
Write-Host "Début de l'opération de sauvegarde"
```

---

Si tu veux, je peux aussi te fournir **la version “script final”** qui enchaîne proprement : *début → création dossier → copie → message → suppression → message fin* (mode prod avec `try/catch` + logs).






Pretest

Dans le cadre de la compétence 13 - Commandes systèmes et langage de script
Évaluation en aide à l'apprentissage synthèse

Instructions :

Lisez chaque consigne attentivement.

Écrivez vos scripts dans les logiciels prévu et remettez vos scripts à l’enseignant.

Objectif : Créer trois scripts (Batch, PowerShell et Python) pour automatiser des tâches simples sur Windows.
Matériel requis : Un ordinateur du magasin, accès à l’explorateur de fichiers, à l’invite de commandes, à PowerShell, à Python (installé), et à un éditeur de texte (ex. : Bloc-notes, VS Code, etc.).

Partie 1 – Script Batch (.bat)

Nom du fichier : sauvegarde.bat

Crée un script batch qui effectue les actions suivantes :

Crée un dossier nommé Sauvegarde sur ton bureau.

Copie tous les fichiers avec l’extension .txt (à créer) de ton dossier Documents vers ce nouveau dossier.

Crée un fichier journal.txt dans le dossier Sauvegarde, contenant la liste des fichiers copiés.

Affiche un message dans la console : Sauvegarde terminée.

Termine le script en attente d’une action de l’utilisateur (pause).

Assure-toi d’avoir quelques fichiers .txt dans ton dossier Documents pour tester ton script.

Section 1 /5

Partie 2 – Script PowerShell (.ps1)

Nom du fichier : rapport_systeme.ps1

Crée un script PowerShell qui fait ce qui suit :

Affiche le nom de l’utilisateur connecté.

Affiche la date et l’heure actuelles.

Liste les processus en cours dont le nom contient le mot Windows (ou un autre programme visible avec mention du programme choisi si tel est le cas).

Enregistre toutes ces informations dans un fichier nommé rapport_systeme.txt sur ton bureau.

Affiche à la fin : Rapport généré.

Section 2 /5

Partie 3 – Script Python (.py)

Nom du fichier : bonjour_log.py

Écris un script Python qui :

Demande à l’utilisateur de saisir son prénom.

Affiche un message de bienvenue : Bonjour [Prénom]!

Enregistre ce message ainsi que la date et l’heure dans un fichier bonjour_log.txt.

Lit ensuite le contenu de ce fichier et l’affiche à l’écran.

Tu peux utiliser le module datetime pour obtenir la date et l’heure.

Remise et évaluation

Remets les trois fichiers (.bat, .ps1, .py) avec les noms demandés.

Assure-toi que chaque script s’exécute sans erreur et produit un résultat visible.

Les scripts doivent être commentés lorsque nécessaire, et bien structurés.

Critère — Points

Fonctionnalité du script — /15

Lisibilité et organisation — /5

Utilisation correcte des commandes ou fonctions — /5

Fichier journal ou sortie bien générée — /5

Respect des consignes — /5

Total — /35
