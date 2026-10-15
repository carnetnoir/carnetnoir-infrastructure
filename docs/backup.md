# Sauvegardes et supervision — Carnet Noir

## Présentation

L'infrastructure Carnet Noir dispose d'un système de sauvegarde automatisé sur son Raspberry Pi 5 sous DietPi.

Ce dispositif vise à faciliter la récupération des services et à signaler les échecs de sauvegarde.

## Automatisation

Les sauvegardes sont intégrées à l'administration du serveur Linux et utilisent des unités systemd.

Un service dédié assure l'exécution de la procédure de sauvegarde.

En cas d'échec, une unité systemd distincte déclenche un mécanisme d'alerte.

## Notification des échecs

Le mécanisme de notification repose sur un script Bash chargé de transmettre une alerte par courrier électronique.

Le système utilise notamment les unités suivantes :

| Unité systemd | Fonction |
|---|---|
| `carnetnoir-backup.service` | Exécution de la sauvegarde |
| `carnetnoir-backup-alert.service` | Notification d'un échec |

La directive `OnFailure` permet d'associer le service principal au mécanisme d'alerte.

## Vérifications administratives

### État du service

```bash
sudo systemctl status carnetnoir-backup.service
```

### Configuration des alertes

```bash
sudo systemctl show carnetnoir-backup.service -p OnFailure -p OnFailureJobMode
```

### Consulter les journaux

```bash
sudo journalctl -u carnetnoir-backup.service --no-pager -n 50
```

### Vérifier le service d'alerte

```bash
sudo systemctl status carnetnoir-backup-alert.service
```

## Tests

Le mécanisme de notification a fait l'objet d'un test d'envoi de courrier électronique.

La réception du message de test a été confirmée.

Cela valide le fonctionnement de la notification testée, sans constituer à lui seul une validation complète de la restauration des sauvegardes.

## Confidentialité

Les archives de sauvegarde, les données des utilisateurs, les identifiants et les paramètres sensibles ne sont pas publiés dans ce dépôt.

Les procédures détaillées de restauration restent à documenter après validation.

## Objectifs de maintenance

- Surveiller les résultats des sauvegardes.
- Vérifier régulièrement les alertes.
- Contrôler l'intégrité des archives.
- Tester périodiquement les procédures de restauration.
- Maintenir une documentation à jour.

---

**Projet :** Carnet Noir

**Site officiel :** https://carnetnoir.fr
