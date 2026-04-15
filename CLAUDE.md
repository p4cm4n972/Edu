# Contexte du projet Edu

## Infrastructure

- **VPS** : `51.210.107.204` — user `ubuntu`
- **Accès SSH** : `ssh ubuntu@51.210.107.204` (clé `~/.ssh/edu_deploy` pour GitHub Actions)
- **Répertoire web sur le VPS** : `/data/sites/html/`
- **Serveur web** : Nginx via Docker Compose, géré par Coolify
- **URL d'accès** : `http://51.210.107.204:8080`
- **Coolify** (panel d'administration) : `http://51.210.107.204:8000`

## Déploiement

- **Repo GitHub** : `git@github.com:p4cm4n972/Edu.git`
- **Branche** : `master`
- **Déploiement automatique** : GitHub Actions (`.github/workflows/deploy.yml`)
  - À chaque `git push` sur `master`, les fichiers HTML sont copiés vers `/data/sites/html/` sur le VPS
  - Durée : ~20 secondes

## Fichiers du projet

| Fichier | Description | URL |
|---|---|---|
| `index.html` | Page d'accueil avec cartes de navigation | `http://51.210.107.204:8080` |
| `english-dialogues.html` | Dialogues en anglais | `http://51.210.107.204:8080/english-dialogues.html` |
| `revision-maths-3eme.html` | Fiches de révision maths 3ème | `http://51.210.107.204:8080/revision-maths-3eme.html` |
| `quiz-maths-3eme.html` | Quiz interactif maths 3ème | `http://51.210.107.204:8080/quiz-maths-3eme.html` |
| `espanol-dialogues.html` | Dialogues espagnol (fichier de l'utilisateur) | `http://51.210.107.204:8080/espanol-dialogues.html` |

## Workflow pour mettre à jour un fichier

```bash
# Modifier le fichier souhaité, puis :
git add .
git commit -m "description de la mise à jour"
git push
# GitHub Actions déploie automatiquement en ~20 secondes
```

## Ajouter un nouveau fichier

1. Placer le fichier HTML dans `~/Documents/Edu/`
2. Ajouter une carte dans `index.html`
3. `git add . && git commit -m "ajout nouveau fichier" && git push`

## Secrets GitHub (repo Edu)

- `VPS_SSH_KEY` : clé privée `~/.ssh/edu_deploy`
- `VPS_HOST` : `51.210.107.204`
- `VPS_USER` : `ubuntu`
