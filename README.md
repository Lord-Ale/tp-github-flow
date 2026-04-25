# cours-02-github-flow-api

API NestJS minimaliste — support du TP cours-02.

Ce dépôt est divisé en deux parties pédagogiques distinctes :

| Répertoire | Contenu |
|---|---|
| `docker-practice/` | **Partie 1 — Docker** : exercice indépendant sur les commandes de base |
| `src/`, `prisma/`, etc. | **Partie 2 — GitHub Flow** : API NestJS à faire évoluer |

---

## Partie 1 — Docker pratique

> Voir [`docker-practice/README.md`](docker-practice/README.md) pour les instructions complètes.

Tu vas écrire un Dockerfile minimaliste, construire une image, lancer un conteneur, puis faire le nettoyage.

---

## Partie 2 — GitHub Flow

### Objectif

Implémenter la fonctionnalité manquante `GET /tasks?done=true` en suivant le GitHub Flow :

1. Créer une branche `feature/add-task-filter` depuis `main`
2. Implémenter le filtrage par statut
3. Adapter les tests existants
4. Pousser la branche et ouvrir une Pull Request
5. Traiter les retours et fusionner dans `main`

### Démarrage recommandé — DevContainer (Windows / Linux / macOS)

**Prérequis** : [VS Code](https://code.visualstudio.com/) + [Docker Desktop](https://www.docker.com/products/docker-desktop/) + extension [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

1. Cloner le dépôt :
   ```bash
   git clone <url-du-repo>
   cd cours-02-github-flow-api
   ```

2. Ouvrir dans VS Code et accepter "Reopen in Container" — ou via la palette de commandes : `Dev Containers: Reopen in Container`

3. Attendre l'initialisation (première fois ~2 min). Les dépendances npm et les migrations Prisma s'exécutent automatiquement.

4. Lancer l'application :
   ```bash
   npm run start:dev
   ```

5. Swagger disponible sur [http://localhost:3000/api](http://localhost:3000/api)

### Démarrage manuel (sans DevContainer)

**Prérequis** : Node.js 24, PostgreSQL 18

1. Copier et renseigner les variables d'environnement :
   ```bash
   cp .env.example .env
   # Éditer .env : renseigner DATABASE_URL
   ```

2. Installer les dépendances :
   ```bash
   npm install
   ```

3. Appliquer les migrations :
   ```bash
   npx prisma migrate dev --name init
   ```

4. Lancer l'application :
   ```bash
   npm run start:dev
   ```

### Lancer les tests

```bash
npm test
```

### Routes disponibles

| Méthode | Route | Description |
|---|---|---|
| `POST` | `/tasks` | Créer une tâche |
| `GET` | `/tasks` | Lister toutes les tâches |
| `GET` | `/tasks/:id` | Récupérer une tâche |
| `PATCH` | `/tasks/:id` | Mettre à jour une tâche |
| `DELETE` | `/tasks/:id` | Supprimer une tâche |
| `GET` | `/tasks?done=true` | ⚠️ **À implémenter** — filtrer par statut |

---

## Pour les plus rapides

Une fois la Partie 2 terminée, tu peux implémenter la **pagination** sur `GET /tasks` via les query params `?page=` et `?limit=`.

Exemple : `GET /tasks?page=1&limit=10`

Même démarche : nouvelle branche `feature/add-pagination`, Pull Request, merge.

