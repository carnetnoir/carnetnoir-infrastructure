# Serveur XMPP — Carnet Noir

## Présentation

Carnet Noir propose un service de messagerie instantanée décentralisée reposant sur le protocole ouvert **XMPP (Extensible Messaging and Presence Protocol)**.

Le serveur utilise **Prosody**, installé sur un Raspberry Pi 5 fonctionnant sous DietPi.

L'objectif est de proposer une infrastructure de communication indépendante, interopérable et compatible avec différents clients XMPP.

**Domaine principal :** `carnetnoir.fr`

**Serveur XMPP :** `xmpp.carnetnoir.fr`

**Service de salons :** `groups.carnetnoir.fr`

## Architecture XMPP

Le service est hébergé sur le Raspberry Pi 5. Les connexions publiques sont acheminées via un VPS OVHcloud, relié au Raspberry Pi par WireGuard.

Cette architecture permet de conserver le serveur de messagerie sur une infrastructure auto-hébergée.

## Fonctionnalités

Le serveur propose notamment :

- Messagerie instantanée XMPP.
- Fédération avec les autres serveurs XMPP.
- Connexions sécurisées par TLS.
- Synchronisation des messages entre plusieurs appareils.
- Archivage des messages (MAM).
- Salons de discussion multi-utilisateurs (MUC).
- Partage de fichiers.
- Prise en charge des appels audio et vidéo via les services associés.
- Notifications push pour les clients compatibles.
- Blocage de contacts et gestion des profils.

## Salons communautaires

Les salons sont hébergés sur le composant MUC `groups.carnetnoir.fr`.

| Salon | Adresse |
|---|---|
| Général | `general@groups.carnetnoir.fr` |
| Support | `support@groups.carnetnoir.fr` |
| Musique électronique | `musique@groups.carnetnoir.fr` |
| Cinéma | `cinema@groups.carnetnoir.fr` |

Ces salons sont destinés aux échanges communautaires et sont configurés pour être publics et permanents.

## Fédération

XMPP est un protocole fédéré : les utilisateurs de serveurs différents peuvent communiquer entre eux sans dépendre d'un fournisseur unique.

Carnet Noir utilise les mécanismes de communication serveur-à-serveur (S2S) de Prosody.

L'accessibilité des salons depuis des comptes externes fait partie des vérifications de fonctionnement de l'infrastructure.

## Sécurité

Plusieurs mesures contribuent à la sécurité du service :

- Chiffrement TLS des connexions.
- Désactivation de l'inscription publique directement depuis XMPP.
- Protection contre certaines tentatives d'authentification abusives avec Fail2ban.
- Contrôle des droits administratifs.
- Tunnel WireGuard entre le Raspberry Pi et le VPS.
- Sauvegardes automatisées et alertes en cas d'échec.

Le contenu sensible des fichiers de configuration, les secrets d'authentification et les clés privées ne sont pas publiés.

## Archivage

Prosody prend en charge l'archivage des messages via MAM, ainsi que l'archivage des conversations dans les salons compatibles.

Les politiques de conservation et de confidentialité sont décrites sur le site officiel.

## Clients compatibles

Le service peut être utilisé avec différents clients XMPP, notamment :

- Gajim
- Monal
- Conversations
- Dino

Le choix du client reste libre, conformément à l'approche ouverte du protocole XMPP.

## Maintenance

L'administration de Prosody s'effectue principalement depuis le terminal Linux et sa console d'administration.

Exemples de commandes de diagnostic :

### Vérifier la configuration

```bash
sudo prosodyctl check config
```

### Vérifier les fonctionnalités

```bash
sudo prosodyctl check features
```

### Afficher les salons existants

```bash
sudo prosodyctl shell muc list groups.carnetnoir.fr
```

### Vérifier le service

```bash
sudo systemctl status prosody
```

Ces commandes permettent de contrôler le fonctionnement du service sans modifier sa configuration.

---

**Site officiel :** https://carnetnoir.fr

**Projet :** Carnet Noir — Infrastructure auto-hébergée
