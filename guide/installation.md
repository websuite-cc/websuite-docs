# 📦 Installation

Guide détaillé pour installer et configurer WebSuite CMS.

## Installation Locale (CLI)

### Prérequis

Choisissez l'une des options suivantes :

- **[Bun](https://bun.sh/)** (recommandé) - Runtime JavaScript ultra-rapide
- **[Node.js](https://nodejs.org/)** (v18 ou supérieur) avec NPM

### IDEs Recommandés

- **Visual Studio Code** - Éditeur open-source populaire
- **Cursor** - IDE basé sur VS Code avec IA intégrée
- **WebStorm** - IDE professionnel de JetBrains
- **Antigravity** - IDE moderne pour le développement web

### Étapes d'Installation

#### 1. Installer le Package

**Option A : Installation via NPM/Bun (Recommandé)**

```bash
# Avec Bun
bun install @websuite-cc/platform

# Ou avec NPM
npm install @websuite-cc/platform

# Aller dans le dossier du package
cd node_modules/@websuite-cc/platform
```

**Option B : Cloner le Repository (pour développement)**

```bash
git clone https://github.com/websuite-cc/CMS.git
cd CMS/ProdBeta
```

> 💡 **Note** : Le projet utilise uniquement les modules natifs de Bun/Node.js. Aucune dépendance externe n'est requise.

#### 2. Installer Bun (Recommandé)

Si vous n'avez pas encore Bun installé :

```bash
# macOS/Linux
curl -fsSL https://bun.sh/install | bash

# Windows
powershell -c "irm bun.sh/install.ps1 | iex"
```

> 💡 **Note** : Le projet utilise uniquement les modules natifs, aucune dépendance externe n'est requise.

#### 3. Configurer les Variables d'Environnement

Créez un fichier `.dev.vars` à la racine du projet :

```bash
cp .dev.vars.example .dev.vars
```

Éditez `.dev.vars` avec vos valeurs :

```env
ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=votre_password_securise
BLOG_FEED_URL=https://votrecompte.substack.com/feed
YOUTUBE_FEED_URL=https://www.youtube.com/feeds/videos.xml?channel_id=VOTRE_ID
PODCAST_FEED_URL=https://anchor.fm/s/VOTRE_ID/podcast/rss
EVENTS_FEED_URL=https://www.meetup.com/fr-fr/votre-groupe/events/rss
```

> ⚠️ **Sécurité** : Le fichier `.dev.vars` est déjà dans `.gitignore` et ne sera jamais commité.

#### 4. (Optionnel) Télécharger les Assets Offline

Pour fonctionner en mode offline, téléchargez les assets statiques :

```bash
chmod +x download-assets.sh
./download-assets.sh
```

#### 5. Ouvrir dans votre IDE

**Visual Studio Code :**
```bash
code .
```

**Cursor :**
```bash
cursor .
```

**WebStorm / Antigravity :**
- Ouvrir le dossier `ProdBeta` depuis l'IDE

#### 6. Lancer le Serveur de Développement

**Avec Bun :**
```bash
bun server.js
```

**Avec Node.js :**
```bash
node server.js
```

Le serveur démarre sur `http://localhost:8000`

> 💡 **Note** : Le serveur utilise le runtime Bun localement pour simuler l'environnement Cloudflare Workers. Si vous utilisez Node.js, certaines fonctionnalités peuvent nécessiter des adaptations.

> 💡 **Astuce** : Le serveur utilise Bun runtime localement pour simuler l'environnement Cloudflare Workers.

### Structure des Fichiers

```
ProdBeta/
├── index.html              # Page d'accueil frontend
├── admin/                  # Interface admin
│   ├── index.html          # Page de login
│   └── dashboard.html      # Dashboard principal
├── core/                   # Scripts JavaScript
│   ├── admin.js            # Logique dashboard
│   └── frontend.js         # Utilitaires frontend
├── functions/              # Cloudflare Pages Functions
│   ├── _middleware.js      # Routeur principal
│   ├── api/                # Endpoints API
│   └── shared/             # Utilitaires partagés
├── frontend/               # Templates frontend
├── config.json             # Configuration globale
└── .dev.vars               # Variables d'environnement (local)
```

## Installation en Production

### Déploiement avec Docker (Recommandé)

#### Option 1 : Docker Compose (Recommandé)

1. **Créer un fichier .env pour la production**

```bash
cp .dev.vars.example .env
# Éditez .env avec vos valeurs de production
```

2. **Lancer avec Docker Compose**

```bash
docker-compose up -d
```

3. **Vérifier le déploiement**

```bash
# Voir les logs
docker-compose logs -f

# Vérifier le statut
docker-compose ps
```

#### Option 2 : Docker Commands

1. **Construire l'Image Docker**

```bash
# Depuis le répertoire ProdBeta
docker build -t websuite-platform .
```

2. **Créer un fichier .env pour la production**

```bash
cp .dev.vars.example .env
# Éditez .env avec vos valeurs de production
```

3. **Lancer le Conteneur**

```bash
docker run -d \
  -p 8000:8000 \
  --env-file .env \
  --name websuite \
  --restart unless-stopped \
  websuite-platform
```

4. **Vérifier le Déploiement**

```bash
# Voir les logs
docker logs websuite

# Vérifier que le conteneur tourne
docker ps
```

Votre application sera accessible sur `http://localhost:8000` (ou le port que vous avez mappé)

> 💡 **Astuce** : Pour changer le port, utilisez `-p 3000:8000` pour mapper le port 8000 du conteneur vers le port 3000 de l'hôte.

### Déploiement sur Cloudflare Pages

Voir le guide [Déploiement sur Cloudflare Pages](../deployment/cloudflare-pages.md) pour les instructions complètes.

### Variables d'Environnement en Production

**Pour Docker :**
- Utilisez un fichier `.env` ou passez les variables avec `-e VARIABLE=valeur`

**Pour Cloudflare Pages :**
1. **Settings** → **Environment variables**
2. Ajoutez toutes les variables nécessaires
3. Marquez les variables sensibles (comme `ADMIN_PASSWORD`) comme **Encrypted**

## Vérification de l'Installation

### Test Local

1. Lancez le serveur :
   - Avec Bun : `bun run server.js`
   - Avec NPM : `npm start`
2. Ouvrez `http://localhost:8000`
3. Vérifiez que la page d'accueil s'affiche
4. Testez l'admin : `http://localhost:8000/admin`

### Test des API

```bash
# Tester l'endpoint des articles
curl http://localhost:8000/api/posts

# Tester l'endpoint des vidéos
curl http://localhost:8000/api/videos

# Tester l'endpoint des podcasts
curl http://localhost:8000/api/podcasts

# Tester l'endpoint des événements
curl http://localhost:8000/api/events
```

## Dépannage

### Erreur : "Cannot find module"

Le projet utilise uniquement les modules natifs de Bun/Node.js. Si vous rencontrez cette erreur :

1. Vérifiez que vous utilisez Bun ou Node.js v18+
2. Assurez-vous que tous les fichiers sont présents dans le projet
3. Vérifiez que les assets statiques sont téléchargés (voir section 4)

### Erreur : "Invalid credentials"

Vérifiez que vos variables d'environnement sont correctement définies dans `.dev.vars`.

### Erreur : "Feed URL not found"

Assurez-vous que les URLs de flux RSS sont valides et accessibles.

## Prochaines Étapes

- [Développement Local](development.md)
- [Configuration](../configuration/overview.md)
- [API Documentation](../api/overview.md)

