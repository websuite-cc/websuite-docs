# 🚀 Quick Start Guide

Get WebSuite Platform up and running in 5 minutes.

## Prerequisites

- **Bun** (recommended) or **Node.js** 18+
- Docker (for production deployment)
- API keys for the services you want to use

## Installation

### Step 1: Install the Package

```bash
# With Bun
bun install @websuite-cc/platform
cd node_modules/@websuite-cc/platform

# Or with NPM
npm install @websuite-cc/platform
cd node_modules/@websuite-cc/platform
```

### Step 2: Configure Environment Variables

```bash
# Copy the template
cp .dev.vars.example .dev.vars

# Edit with your values
nano .dev.vars
```

Minimum required variables:

```env
ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=your_secure_password_12_chars_min

# Content Sources (at least one)
BLOG_FEED_URL=https://yoursubstack.substack.com/feed
YOUTUBE_FEED_URL=https://www.youtube.com/feeds/videos.xml?channel_id=YOUR_ID
```

### Step 3: Run Locally

```bash
# With Bun
bun server.js

# Or with Node.js
node server.js
```

Your platform will be available at `http://localhost:8000`

- **Frontend**: http://localhost:8000
- **Admin Dashboard**: http://localhost:8000/admin
- **IDE**: http://localhost:8000/admin/ide.html

## Deployment Options

### Option 1: Docker (Recommended for Production)

```bash
# Build the image
docker build -t websuite-platform .

# Run with Docker Compose
docker-compose up -d
```

See [Installation Guide](installation.md#installation-en-production) for detailed instructions.

### Option 2: Cloudflare Pages (Managed Platform)

1. Connect your GitHub repository to Cloudflare Pages
2. Configure environment variables in the dashboard
3. Deploy automatically on every push

See [Cloudflare Pages Deployment](../deployment/cloudflare-pages.md) for details.

### Option 3: Self-Hosted

Deploy on your own infrastructure:
- VPS/Cloud Server
- Kubernetes
- Any platform supporting Docker or Bun/Node.js

## Next Steps

- 📖 [Complete Installation Guide](installation.md)
- 🤖 [AI Agents Guide](agents-architecture.md)
- 🔌 [Service Integrations](../configuration/overview.md)
- 📚 [API Documentation](../api/overview.md)

## Need Help?

- 📧 **Email**: community@websuite.cc
- 🐛 [GitHub Issues](https://github.com/websuite-cc/CMS/issues)
- 📖 [Full Documentation](../README.md)
