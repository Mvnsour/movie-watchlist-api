# Backend API — Node.js, Express, JWT, Prisma, PostgreSQL

**🇬🇧 [English](#english) | 🇫🇷 [Français](#français)**

---

## English

A complete REST API featuring user authentication, movie management, and a personal watchlist system.

### 🚀 Overview

This project implements:
1. **User Authentication** — registration, login, JWT-based sessions
2. **Movie Management** — full CRUD operations
3. **Watchlist** — status tracking and ratings for saved movies

### ⚙️ Tech Stack

- **Node.js** — JavaScript runtime
- **Express.js** — web framework
- **JWT** — authentication & authorization
- **Prisma** — ORM
- **PostgreSQL** — relational database
- **Zod** — schema validation
- **bcryptjs** — password hashing
- **dotenv** — environment variable management

### 📋 Features

**Authentication**
- User registration with validation
- Login with JWT token generation
- Logout / session invalidation
- Password hashing (bcryptjs)
- Protected routes via middleware

**Movies**
- Full CRUD (create, read, update, delete)
- Title, overview, release year, genres, runtime, poster
- Linked to the creating user

**Watchlist**
- Add / remove movies
- Status tracking: PLANNED, WATCHING, COMPLETED, DROPPED
- Ratings (1–10) and personal notes

**Other**
- Request validation with Zod
- Centralized error handling
- JWT middleware on protected routes
- Prisma migrations and seeding

### 👌 Getting Started

**Prerequisites**
- Node.js v18+ (v22.x recommended if using Prisma v7)
- PostgreSQL v14+
- Git

**Installation**

```bash
git clone <your-repo-url>
cd <project-name>
npm install
```

Create a `.env` file at the project root:

```
DATABASE_URL="postgresql://username:password@localhost:5432/database_name"
JWT_SECRET="your-super-secret-jwt-key"
PORT=5001
```

Set up the database:

```bash
npx prisma migrate dev
npm run seed:movies   # optional
```

Start the dev server:

```bash
npm run dev
```

The API will be available at `http://localhost:5001`.

> ⚠️ **Prisma v7 note**: this project can run on either Prisma v6 or v7. Prisma v7 is ESM-only and requires: `"type": "module"` in `package.json`, the `provider = "prisma-client"` generator, a `prisma.config.ts` file, the `@prisma/adapter-pg` driver adapter, and manually loading `.env` with `import "dotenv/config"`. Check the Prisma docs for full migration details.

### 🔌 API Endpoints

**Auth**
- `POST /auth/register`
- `POST /auth/login`
- `POST /auth/logout`

**Movies**
- `GET /movies`
- `POST /movies`
- `PUT /movies/:id`
- `DELETE /movies/:id`

**Watchlist (protected)**
- `POST /watchlist`
- `PUT /watchlist/:id`
- `DELETE /watchlist/:id`

### 🗄️ Data Models

**User**: id, name, email, password (hashed), createdAt

**Movie**: id, title, overview, releaseYear, genres[], runtime, posterUrl, createdBy, createdAt

**WatchlistItem**: id, userId, movieId, status, rating, notes, createdAt, updatedAt

### ☁️ Deployment

Can be deployed on Railway, Render, Heroku, DigitalOcean App Platform, or AWS.

### 📚 Resources

- [Node.js docs](https://nodejs.org/docs)
- [Express.js docs](https://expressjs.com/)
- [Prisma docs](https://www.prisma.io/docs)
- [PostgreSQL docs](https://www.postgresql.org/docs/)
- [Zod docs](https://zod.dev/)
- [JWT.io](https://jwt.io/)

---

## Français

Une API REST complète avec authentification utilisateur, gestion de films et système de watchlist personnelle.

### 🚀 Présentation

Ce projet implémente :
1. **Authentification utilisateur** — inscription, connexion, sessions basées sur JWT
2. **Gestion de films** — CRUD complet
3. **Watchlist** — suivi de statut et notation des films enregistrés

### ⚙️ Stack technique

- **Node.js** — runtime JavaScript
- **Express.js** — framework web
- **JWT** — authentification et autorisation
- **Prisma** — ORM
- **PostgreSQL** — base de données relationnelle
- **Zod** — validation de schémas
- **bcryptjs** — hachage des mots de passe
- **dotenv** — gestion des variables d'environnement

### 📋 Fonctionnalités

**Authentification**
- Inscription avec validation
- Connexion avec génération de token JWT
- Déconnexion / invalidation de session
- Hachage des mots de passe (bcryptjs)
- Routes protégées via middleware

**Films**
- CRUD complet (création, lecture, mise à jour, suppression)
- Titre, résumé, année de sortie, genres, durée, poster
- Association à l'utilisateur créateur

**Watchlist**
- Ajout / suppression de films
- Statuts : PLANNED, WATCHING, COMPLETED, DROPPED
- Notation (1–10) et notes personnelles

**Autres**
- Validation des requêtes avec Zod
- Gestion centralisée des erreurs
- Middleware JWT sur les routes protégées
- Migrations et seed Prisma

### 👌 Démarrage

**Prérequis**
- Node.js v18+ (v22.x recommandé avec Prisma v7)
- PostgreSQL v14+
- Git

**Installation**

```bash
git clone <url-de-ton-repo>
cd <nom-du-projet>
npm install
```

Créer un fichier `.env` à la racine :

```
DATABASE_URL="postgresql://username:password@localhost:5432/database_name"
JWT_SECRET="ton-secret-jwt"
PORT=5001
```

Initialiser la base de données :

```bash
npx prisma migrate dev
npm run seed:movies   # optionnel
```

Lancer le serveur de dev :

```bash
npm run dev
```

L'API est disponible sur `http://localhost:5001`.

> ⚠️ **Note Prisma v7** : ce projet fonctionne aussi bien avec Prisma v6 qu'avec Prisma v7. Prisma v7 est ESM-only et nécessite : `"type": "module"` dans `package.json`, le générateur `provider = "prisma-client"`, un fichier `prisma.config.ts`, l'adaptateur `@prisma/adapter-pg`, et le chargement manuel de `.env` via `import "dotenv/config"`. Voir la doc Prisma pour le détail complet.

### 🔌 Endpoints API

**Auth**
- `POST /auth/register`
- `POST /auth/login`
- `POST /auth/logout`

**Movies**
- `GET /movies`
- `POST /movies`
- `PUT /movies/:id`
- `DELETE /movies/:id`

**Watchlist (protégé)**
- `POST /watchlist`
- `PUT /watchlist/:id`
- `DELETE /watchlist/:id`

### 🗄️ Modèles de données

**User** : id, name, email, password (hashé), createdAt

**Movie** : id, title, overview, releaseYear, genres[], runtime, posterUrl, createdBy, createdAt

**WatchlistItem** : id, userId, movieId, status, rating, notes, createdAt, updatedAt

### ☁️ Déploiement

Déployable sur Railway, Render, Heroku, DigitalOcean App Platform ou AWS.

### 📚 Ressources

- [Documentation Node.js](https://nodejs.org/docs)
- [Documentation Express.js](https://expressjs.com/)
- [Documentation Prisma](https://www.prisma.io/docs)
- [Documentation PostgreSQL](https://www.postgresql.org/docs/)
- [Documentation Zod](https://zod.dev/)
- [JWT.io](https://jwt.io/)
