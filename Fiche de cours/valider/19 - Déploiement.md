
# Fiche courte — Déploiement logiciel par GPO
## 1. Préparation client / réseau

- Vérifier le pare-feu Windows.
- Vérifier la carte réseau VMware.
- IP client : 192.168.48.159
- Passerelle : 192.168.48.2
- DNS : 192.168.48.159
- DNS avancé : ajouter le suffixe DNS / nom de forêt.
- Vérifier que le poste est bien joint au domaine.

<img src="https://github.com/user-attachments/assets/7dfe109c-de63-4fda-8406-11f50ef0c8e8" width="50%">


## 2. Partage du dossier installateurs

- Dossier installateur partagé.
- Partage : Tout le monde.
- Sécurité : Tout le monde + ordinateurs clients / ordinateurs du domaine.



## 3. Installation MSI par GPO

- Créer une GPO.
- Ajouter le package MSI avec un chemin UNC.
- Lier la GPO à la bonne OU.
- Dans le filtrage de sécurité : mettre seulement le groupe ciblé.

<img src="https://github.com/user-attachments/assets/21e80965-783e-43a9-ab5b-81998f940d87" width="50%">



## 4. Sécurité de la GPO

- Garder uniquement le groupe concerné.
- Ajouter Utilisateurs authentifiés si nécessaire pour l’évaluation.
- Ajouter l’ordinateur client dans les droits si demandé.

<img src="https://github.com/user-attachments/assets/93e7a092-0453-4048-b100-1e1924e53e9f" width="50%">

<img src="https://github.com/user-attachments/assets/7da65e59-669a-49bd-86d1-5f6c40e263e9" width="50%">


## 5. Script PowerShell au démarrage

- Script dans Configuration ordinateur.
- Scripts Windows : Démarrage.
- Autoriser les scripts distants dans la stratégie Windows PowerShell.
- Redémarrer le poste pour tester.

<img src="https://github.com/user-attachments/assets/d0efd397-0466-4cad-a679-72dce388c7cb" width="50%">

<img src="https://github.com/user-attachments/assets/76c12552-f8c7-4d5d-abdc-69128612231b" width="50%">


## 6. OU / Active Directory

- Les utilisateurs sont déjà créés.
- Déplacer les postes depuis Computers vers la bonne OU.
- Vérifier les OU : utilisateurs, groupes, ordinateurs clients.



## 7. Côté client
Normalement pas necessaire
gpupdate /force



## Bonus : admin local

* Ajouter un compte dans les administrateurs locaux si demandé.

<img src="https://github.com/user-attachments/assets/7aee09ab-5d3d-497c-aa2f-6b4b1ab061d9" width="50%">


