# Partie 1 — Pratique Docker

> **Durée estimée : 25 min**  
> Cette partie est indépendante du reste du projet. Elle se fait entièrement dans ce répertoire `docker-practice/`.

---

## Contexte

Le fichier `index.js` est un serveur HTTP minimaliste en Node.js pur (aucune dépendance). Il répond `Hello depuis Docker !` sur le port 3001.

Ton travail : écrire un `Dockerfile` pour le conteneuriser, puis manipuler les commandes fondamentales de Docker.

---

## Étapes

### 1 — Observer le code

Ouvre `index.js` et lis-le. Comprends ce qu'il fait avant de continuer.

---

### 2 — Écrire le Dockerfile

Ouvre `Dockerfile`. Il contient des commentaires qui guident chaque section.  
Complète-le en utilisant :

- `FROM` — image parente
- `WORKDIR` — répertoire de travail dans le conteneur
- `COPY` — copier les fichiers nécessaires
- `EXPOSE` — port à exposer
- `CMD` — commande de démarrage

---

### 3 — Construire l'image

```bash
docker build -t hello-docker .
```

---

### 4 — Vérifier que l'image existe localement

```bash
docker image ls
```

---

### 5 — Lancer un conteneur

```bash
docker run -p 3001:3001 hello-docker
```

---

### 6 — Vérifier que l'application répond

Dans un autre terminal (ou via le navigateur) :

```bash
curl http://localhost:3001
```

Tu dois obtenir : `Hello depuis Docker !`

---

### 7 — Arrêter le conteneur

Dans un autre terminal, trouve l'ID du conteneur en cours d'exécution :

```bash
docker ps
```

Puis arrête-le :

```bash
docker stop <id>
```

---

### 8 — Vérifier que le conteneur n'est plus actif

```bash
docker ps
```

---

### 9 — Supprimer le conteneur

```bash
docker rm <id>
```

---

### 10 — Supprimer l'image locale

```bash
docker rmi hello-docker
```

---

### 11 — Vérifier le nettoyage

```bash
docker image ls
```

L'image `hello-docker` ne doit plus apparaître.

---

## Ce que tu dois être capable d'expliquer à la fin

- Quelle est la différence entre une **image** et un **conteneur** ?
- Que fait la ligne `FROM` dans un Dockerfile ?
- Pourquoi utilise-t-on `-p 3001:3001` dans `docker run` ?
- Quel est l'ordre correct : `build` → `run` → `stop` → `rm` → `rmi` ?
