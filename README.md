# DrupalAI

Projet Drupal 11 sous environnement **DDEV** (WSL2 / Ubuntu).

## Stack technique

| Composant | Version | Détails |
|------------|----------|---------|
| **Drupal Core** | 11.2.5 | Distribution `drupal/recommended-project` |
| **PHP** | 8.3 | Nginx-FPM sous conteneur DDEV |
| **DDEV** | 1.24.10 | Plateforme Docker locale (wsl2-docker-ce) |
| **Base de données** | MariaDB 10.11 | fournie par DDEV |
| **Node.js** | 22 | intégré dans le conteneur web |
| **Composer** | 2.x | exécuté via `ddev composer` |

## Installation

Cloner le projet :
```bash
git clone git@github.com:Yorik56/ddev.git drupalai
cd drupalai
````

Démarrer l’environnement :

```bash
ddev start
```

Installer Drupal (si aucune base importée) :

```bash
ddev composer install
ddev drush site:install -y --account-name=admin --account-pass=admin
```

Le site sera accessible à :
👉 [https://drupalai.ddev.site](https://drupalai.ddev.site)

## Commandes utiles

| Action                 | Commande                                      |
| ---------------------- | --------------------------------------------- |
| Lancer le site         | `ddev launch`                                 |
| Stopper les conteneurs | `ddev stop`                                   |
| Exporter la base       | `ddev export-db --file=../drupalai-db.sql.gz` |
| Importer la base       | `ddev import-db --file=../drupalai-db.sql.gz` |
| Snapshot rapide        | `ddev snapshot --name="avant_migration"`      |
| Vérifier les services  | `ddev describe`                               |

## Bonnes pratiques

* Travailler dans `~/workspace/drupalai` (FS Linux, pas `/mnt/c`).
* Exclure `web/sites/default/files` et `vendor/` du versionnement.
* Désactiver Xdebug par défaut : `ddev xdebug off`.
* Exporter la base avant toute mise à jour majeure : `ddev export-db`.

---

**Environnement :** Windows 11 + WSL2 (Ubuntu)
