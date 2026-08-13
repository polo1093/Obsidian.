# Scripts et automatisation pour le soutien informatique

![PowerShell](https://img.shields.io/badge/PowerShell-Windows-5391FE?style=flat-square&logo=powershell&logoColor=white)
![Python](https://img.shields.io/badge/Python-Multiplateforme-3776AB?style=flat-square&logo=python&logoColor=white)
![Sécurité](https://img.shields.io/badge/Principe-Vérifier%20avant%20de%20modifier-C62828?style=flat-square)

> **Objectif :** automatiser des tâches répétitives avec des scripts lisibles, prévisibles, journalisés et sécuritaires.

## Choisir le bon outil

| Outil | Usage pertinent |
| --- | --- |
| **PowerShell** | administration Windows, services, comptes, fichiers, réseau et Microsoft 365 |
| **Batch** | lancement simple de commandes Windows ou compatibilité avec un ancien processus |
| **Python** | traitement de données, API, logique multiplateforme et outils personnalisés |

## Principes d'un script professionnel

- définir clairement les entrées, les sorties et les effets;
- commencer par une version en lecture seule;
- valider les chemins, les paramètres et les droits;
- gérer les erreurs explicitement;
- produire un journal utile;
- permettre une simulation lorsque l'action est sensible;
- ne jamais stocker de mot de passe ou de jeton dans le code;
- tester avec des données non critiques;
- documenter les prérequis et la procédure de retour arrière.

## PowerShell — structure recommandée

~~~powershell
[CmdletBinding(SupportsShouldProcess)]
param(
    [Parameter(Mandatory)]
    [ValidateNotNullOrEmpty()]
    [string]$Source,

    [Parameter(Mandatory)]
    [ValidateNotNullOrEmpty()]
    [string]$Destination
)

$ErrorActionPreference = 'Stop'

try {
    if (-not (Test-Path -LiteralPath $Source -PathType Container)) {
        throw "Le dossier source est introuvable : $Source"
    }

    if (-not (Test-Path -LiteralPath $Destination)) {
        New-Item -Path $Destination -ItemType Directory | Out-Null
    }

    if ($PSCmdlet.ShouldProcess($Destination, "Copier les fichiers texte")) {
        Copy-Item -Path (Join-Path $Source '*.txt') -Destination $Destination -Force
    }

    Write-Information "Opération terminée." -InformationAction Continue
}
catch {
    Write-Error "Échec de l'opération : $($_.Exception.Message)"
    exit 1
}
~~~

Exécuter d'abord avec **-WhatIf** lorsqu'une commande prend en charge cette option.

## Commandes PowerShell essentielles

| Besoin | Commande |
| --- | --- |
| vérifier un chemin | **Test-Path** |
| lire un élément | **Get-Item**, **Get-ChildItem** |
| créer | **New-Item** |
| copier ou déplacer | **Copy-Item**, **Move-Item** |
| lire les services | **Get-Service** |
| tester un port | **Test-NetConnection** |
| exporter des données | **Export-Csv**, **ConvertTo-Json** |
| journaliser | **Start-Transcript**, **Write-Information** |
| obtenir de l'aide | **Get-Help commande -Full** |

## Python — exemple de journal

~~~python
from datetime import datetime
from pathlib import Path

log_file = Path.home() / "Desktop" / "support_log.txt"
message = f"{datetime.now():%Y-%m-%d %H:%M:%S} - Vérification terminée"

try:
    log_file.write_text(message + "\n", encoding="utf-8")
    print(message)
except OSError as error:
    print(f"Impossible d'écrire le journal : {error}")
    raise
~~~

## Batch — bonnes pratiques minimales

~~~bat
@echo off
setlocal
set "DEST=%USERPROFILE%\Desktop\Sauvegarde"

if not exist "%DEST%" mkdir "%DEST%"
if errorlevel 1 (
  echo Impossible de creer le dossier.
  exit /b 1
)

echo Dossier pret : %DEST%
endlocal
~~~

Toujours mettre les chemins entre guillemets et utiliser **setlocal** pour éviter de modifier l'environnement parent.

## Sécurité et secrets

- utiliser un coffre de secrets ou le mécanisme d'identité de la plateforme;
- limiter les permissions du compte d'exécution;
- ne pas afficher de secrets dans les journaux;
- supprimer ou masquer les données personnelles;
- signer les scripts lorsque la politique l'exige;
- revoir tout script téléchargé avant de l'exécuter.

## Checklist avant production

- [ ] le script fonctionne sans privilège excessif;
- [ ] les paramètres sont validés;
- [ ] le mode simulation a été essayé;
- [ ] les erreurs retournent un code utile;
- [ ] les journaux ne contiennent aucun secret;
- [ ] un retour arrière existe;
- [ ] un second technicien peut comprendre le script.

## Idées d'automatisation en soutien

- inventaire de postes et versions;
- vérification d'espace disque;
- collecte de journaux;
- création contrôlée de dossiers et permissions;
- test de connectivité;
- préparation de rapports CSV;
- détection de services arrêtés;
- sauvegarde de fichiers de configuration.

---

## Notes personnelles, exercices et captures d’origine

> Cette section conserve **intégralement** le contenu personnel présent avant la refonte : formulations de cours, exercices, rappels et captures d’écran. Les sections précédentes servent de complément structuré; elles ne remplacent pas ces notes.

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
