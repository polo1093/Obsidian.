# Fiche de cours – Réseau 3 / Prétest C19

## Objectif

Fiche courte pour retrouver rapidement les manipulations vues en cours :

- configurer les alertes courriel iDRAC ;
- activer et tester le Bureau à distance ;
- consulter les erreurs depuis le serveur ;
- repérer les échecs de connexion ;
- consulter le journal d’événements d’un client ;
- activer la gestion distante côté client ;
- configurer l’analyseur de performances.

---

## 1. Activer les alertes courriel iDRAC

### Paramètres importants

| Élément | Valeur |
|---|---|
| Serveur SMTP | `courrier.csduroy.qc.ca` |
| Port SMTP | `25` |
| Destination | courriel csduroy fourni dans la requête |
| Alertes à activer | Mémoire + Stockage |

> Dans la requête, bien vérifier le serveur exact demandé.  
> Note terrain : `bat**courrier.csduroy.qc.ca**`

### Capture

<img width="650" alt="activer mail" src="https://github.com/user-attachments/assets/99c5172d-3923-4b26-87b7-06d9b0f14ad7" />

---

## 2. Bureau à distance – procédure en 3 actions

### Lien vers le script tout-en-un

Script GitHub :

[script/bureau a distance.bat](https://github.com/polo1093/Cours_DEP_SI/blob/main/script/bureau%20a%20distance.bat)

---

### Action 1 — Activer le Bureau à distance dans Windows

Vérifier que le Bureau à distance est activé sur le serveur Windows.

<img width="650" alt="bureau a distance activation" src="https://github.com/user-attachments/assets/ad3f5e29-9a31-4928-bb35-e5115f214abe" />

---

### Action 2 — Autoriser le Bureau à distance dans le pare-feu

Vérifier que les règles du pare-feu liées au Bureau à distance sont activées.

<img width="650" alt="bureau a distance pare-feu" src="https://github.com/user-attachments/assets/5fdedd3b-bb8d-450e-91fa-55118f02081f" />

---

### Action 3 — Forcer le service RDP en automatique

À lancer sur le serveur en administrateur :

```bat
sc.exe config TermService start= auto >nul 2>&1
net start TermService >nul 2>&1
```

Depuis le client, tester le port RDP :

```powershell
Test-NetConnection 192.168.33.135 -Port 3389
```

Résultat attendu :

```text
TcpTestSucceeded : True
```

---

## 3. Filtrer les erreurs depuis le serveur

Objectif : retrouver rapidement les erreurs dans l’Observateur d’événements depuis le serveur.

À vérifier en priorité :

- journal **Application** ;
- journal **Système** ;
- erreurs critiques ;
- erreurs liées au service testé ;
- erreurs liées au réseau, DNS, RDP ou stockage.

<img width="650" alt="filtre erreur depuis serveur" src="https://github.com/user-attachments/assets/4ffce67e-8f35-4258-b00e-097690d0fab6" />

---

## 4. Verrouillage / connexion échouée

Objectif : repérer les traces de connexion refusée ou de compte verrouillé.

Événements utiles :

| ID événement | Utilité |
|---|---|
| `4625` | Échec de connexion |
| `4624` | Connexion réussie |
| `4740` | Compte verrouillé |
| `4771` | Échec Kerberos |
| `4776` | Échec NTLM |

<img width="650" alt="verrouillage connexion fail" src="https://github.com/user-attachments/assets/d452a321-19f3-4a81-948d-fc7853c23d15" />

---

## 5. Traces de logs des échecs de connexion

Objectif : identifier la source et la raison de l’échec.

À regarder :

- nom du compte ;
- poste source ;
- type d’ouverture de session ;
- code d’erreur ;
- heure de l’événement.

<img width="650" alt="trace de log des echecs de connexion" src="https://github.com/user-attachments/assets/2cfc3496-8406-423a-b254-b28c31f664b2" />

---

## 6. Journal d’événements client

Objectif : consulter les événements d’un poste client depuis le serveur.

Prérequis côté client :

- gestion distante activée ;
- règles pare-feu ouvertes ;
- WinRM activé ;
- droits administrateur suffisants.

<img width="650" alt="journal evenement client" src="https://github.com/user-attachments/assets/7bbf02ee-49ed-4ef2-905a-1b17a3ffe412" />

---

## 7. Commandes PowerShell sur l’ordinateur client

À lancer sur le poste client en PowerShell administrateur.

```powershell
Get-NetFirewallRule | Where-Object {
    $_.DisplayName -like "*journal*" -or
    $_.DisplayName -like "*événement*" -or
    $_.DisplayName -like "*Event Log*" -or
    $_.DisplayName -like "*RPC*" -or
    $_.DisplayName -like "*DCOM*"
} | Enable-NetFirewallRule

Enable-PSRemoting -Force

Set-NetFirewallRule -DisplayGroup "Gestion à distance de Windows" -Enabled True
```

### Variante si Windows est en anglais

```powershell
Set-NetFirewallRule -DisplayGroup "Remote Event Log Management" -Enabled True
Set-NetFirewallRule -DisplayGroup "Windows Remote Management" -Enabled True
Enable-PSRemoting -Force
```

---

## 8. Analyseur de performances

Objectif : créer un ensemble de collecteurs de données personnalisé.

Nom conseillé :

```text
PRETESTC19
```

Compteurs à ajouter :

| Compteur | Catégorie |
|---|---|
| `% temps processeur` | Processeur |
| `Écriture disque, octets/s` | Disque |
| `% octets dédiés utilisés` | Mémoire |

<img width="650" alt="performance" src="https://github.com/user-attachments/assets/01078e88-dbe8-4fa5-9c90-5b77e40a8ec2" />

---

## 9. Mini-check final

- [ ] Alertes courriel iDRAC configurées.
- [ ] Alertes mémoire activées.
- [ ] Alertes stockage activées.
- [ ] Bureau à distance activé.
- [ ] Service `TermService` démarré.
- [ ] Test `3389` réussi depuis le client.
- [ ] Journaux d’événements consultables.
- [ ] Gestion distante activée côté client.
- [ ] Collecteur de performance créé.
