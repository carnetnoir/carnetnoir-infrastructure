# carnetnoir-infrastructure
Infrastructure auto-hébergée sur Raspberry Pi 5 : XMPP, Prosody, WireGuard et services associés.

# Carnet Noir — Infrastructure auto-hébergée

**Serveur XMPP fédéré sur Raspberry Pi 5, propulsé par DietPi et Prosody.**

## Présentation

Carnet Noir est un projet personnel d'auto-hébergement visant à proposer des services de communication décentralisés, avec une attention particulière portée à la confidentialité, à l'interopérabilité et à la maîtrise de l'infrastructure.

Le cœur du projet repose sur un Raspberry Pi 5 exécutant DietPi, associé à un VPS OVHcloud assurant l'accès depuis Internet.

🌐 **Site officiel :** https://carnetnoir.fr

## Infrastructure

| Composant | Technologie |
|---|---|
| Serveur principal | Raspberry Pi 5 |
| Système d'exploitation | DietPi (Debian) |
| Messagerie instantanée | Prosody (XMPP) |
| Hébergement réseau public | VPS OVHcloud |
| Liaison sécurisée | WireGuard |
| Protection des accès | Fail2ban |
| Transferts de fichiers | HTTP File Upload / SOCKS5 |
| Appels audio et vidéo | TURN |
| Sauvegardes | Automatisées avec alertes |

## Fonctionnalités XMPP

- Communication fédérée avec les autres serveurs XMPP.
- Connexions sécurisées par TLS.
- Salons de discussion multi-utilisateurs (MUC).
- Synchronisation des messages entre appareils.
- Partage de fichiers.
- Prise en charge des appels audio et vidéo.
- Archivage des messages.
- Accès compatible avec différents clients XMPP.

## Salons communautaires

| Salon | Adresse |
|---|---|
| Général | general@groups.carnetnoir.fr |
| Support | support@groups.carnetnoir.fr |
| Musique électronique | musique@groups.carnetnoir.fr |
| Cinéma | cinema@groups.carnetnoir.fr |

## Objectifs du projet

- Favoriser les communications décentralisées.
- Expérimenter l'auto-hébergement sur matériel basse consommation.
- Maintenir une infrastructure documentée et sécurisée.
- Encourager l'utilisation de protocoles ouverts.
- Partager les expériences et les connaissances techniques.

## Documentation

Ce dépôt a vocation à documenter progressivement l'architecture, les services, les choix techniques et les procédures de maintenance de Carnet Noir.

Les identifiants, clés privées, secrets d'authentification et configurations sensibles ne sont pas publiés.

## Statut

Projet personnel en fonctionnement, maintenu et amélioré progressivement.
