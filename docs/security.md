# Sécurité de l'infrastructure — Carnet Noir

## Présentation

La sécurité de Carnet Noir repose sur plusieurs mécanismes complémentaires destinés à protéger les services, les communications et les accès administratifs.

L'infrastructure comprend un Raspberry Pi 5 sous DietPi, un VPS OVHcloud et une liaison réseau WireGuard.

## Protection des accès

### SSH et Dropbear

L'administration du serveur s'effectue à distance au moyen d'une connexion SSH.

Le service Dropbear assure l'accès SSH sur le Raspberry Pi.

### Fail2ban

Fail2ban analyse les journaux de certains services afin de détecter des tentatives d'authentification abusives et d'appliquer des bannissements temporaires selon les règles configurées.

Deux protections sont notamment configurées :

| Jail | Service protégé |
|---|---|
| `dropbear` | Accès SSH |
| `prosody-auth` | Authentification XMPP |

La protection `prosody-auth` surveille les événements d'authentification de Prosody.

## Sécurisation des communications

### TLS

Les connexions XMPP utilisent TLS afin de protéger les communications entre les clients et le serveur, ainsi qu'entre les serveurs lorsque la négociation sécurisée est établie.

### WireGuard

Un tunnel WireGuard relie le VPS OVHcloud au Raspberry Pi.

Il fournit un canal réseau chiffré pour les échanges entre ces deux machines.

Les clés privées et paramètres sensibles du tunnel restent confidentiels.

## Sécurité de Prosody

Le serveur XMPP repose sur Prosody.

Plusieurs mécanismes contribuent à sa protection :

- Authentification des utilisateurs.
- Gestion des permissions administratives.
- Contrôle des affiliations et des rôles dans les salons MUC.
- Protection des tentatives d'authentification par Fail2ban.
- Chiffrement des connexions par TLS.

La fédération XMPP permet la communication avec d'autres serveurs, sans leur accorder de privilèges administratifs locaux.

## Sauvegardes et alertes

Des procédures automatisées assurent la sauvegarde des éléments nécessaires à l'exploitation du serveur.

Un mécanisme de notification permet de signaler les échecs des tâches de sauvegarde.

La documentation détaillée de ce dispositif figure dans `backup.md`.

## Vérifications administratives

### État de Fail2ban

```bash
sudo fail2ban-client status
```

### Protection de Prosody

```bash
sudo fail2ban-client status prosody-auth
```

### Protection de Dropbear

```bash
sudo fail2ban-client status dropbear
```

### État du tunnel WireGuard

```bash
sudo wg show
```

### Vérification de Prosody

```bash
sudo prosodyctl check config
```

Ces commandes sont destinées à l'administration locale et ne nécessitent aucune publication de leurs résultats.

## Confidentialité des configurations

Ce dépôt GitHub est destiné à la documentation technique.

Il ne contient pas :

- De clés privées SSH ou WireGuard.
- De mots de passe ou de jetons d'authentification.
- De secrets TURN.
- De sauvegardes contenant des données personnelles.
- De configurations complètes contenant des informations sensibles.

## Maintenance

La sécurité d'une infrastructure auto-hébergée nécessite une maintenance régulière, notamment la mise à jour des logiciels, la consultation des journaux et la vérification des mécanismes de protection.

---

**Projet :** Carnet Noir

**Site officiel :** https://carnetnoir.fr
