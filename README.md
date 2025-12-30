# 🚀 WebSuite Platform

> **The Complete Web Development Platform** - CMS, AI Agents, MCP Workers, IDE, and 30+ Integrations  
> Built on Edge with Bun. Deploy anywhere in minutes.

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![npm version](https://img.shields.io/npm/v/@websuite-cc/platform)](https://www.npmjs.com/package/@websuite-cc/platform)
[![Bun](https://img.shields.io/badge/runtime-Bun-000000)](https://bun.sh)

---

## ✨ What is WebSuite?

WebSuite is a **complete web development platform** that combines:

- 🎯 **Headless CMS** - Multi-source content aggregation (RSS, YouTube, Podcasts, Events)
- 🤖 **AI Agents** - Intelligent MCP Workers powered by Gemini, ChatGPT, Mistral AI, DeepSeek
- 💻 **Built-in IDE** - Monaco Editor for code editing and deployment
- 🔌 **30+ Integrations** - GitHub, Gmail, Slack, Stripe, WhatsApp, Zoom, Supabase, and more
- ⚡ **Edge Runtime** - Built on Bun.js for maximum performance
- 🎨 **Modern UI** - Beautiful admin dashboard with dark mode
- 🔐 **Enterprise Security** - Authentication, environment variables, encrypted secrets

---

## 🚀 Quick Start

### Installation

```bash
# With Bun (recommended)
bun install @websuite-cc/platform
cd node_modules/@websuite-cc/platform

# Or with NPM
npm install @websuite-cc/platform
cd node_modules/@websuite-cc/platform
```

### Configuration

```bash
# Copy environment variables template
cp .dev.vars.example .dev.vars

# Edit .dev.vars with your API keys and configuration
nano .dev.vars
```

### Run Locally

```bash
# With Bun
bun server.js

# Or with Node.js
node server.js
```

Your platform will be available at `http://localhost:8000`

---

## 🎯 Core Features

### 📊 Content Management System

- **Multi-source aggregation** from RSS feeds
- **YouTube integration** for video content
- **Podcast support** (Anchor.fm, Spotify, Apple Podcasts)
- **Event management** (Meetup, Eventbrite)
- **Real-time content sync** with intelligent caching

### 🤖 AI Agents & MCP Workers

- **Intelligent agents** that understand context and make decisions
- **Multiple AI models**: Gemini, ChatGPT, Mistral AI, DeepSeek
- **Code generation** and deployment automation
- **MCP (Model Context Protocol)** support
- **Agent execution logs** and monitoring

### 💻 Built-in IDE

- **Monaco Editor** - VS Code-like experience in the browser
- **Live preview** of your code
- **One-click deployment** to GitHub
- **Template management** for frontend pages
- **Syntax highlighting** for multiple languages

### 🔌 30+ Service Integrations

Connect to all your favorite services:

**Communication:**
- Gmail, WhatsApp Business, Twilio SMS, Slack

**AI & Machine Learning:**
- Google Gemini, OpenAI ChatGPT, Mistral AI, DeepSeek, DeepL

**Development:**
- GitHub, GitLab, Supabase

**Productivity:**
- Google Workspace (Drive, Docs, Sheets, Calendar, Meet, Forms)
- Airtable, Trello, Notion

**E-commerce & Payments:**
- Stripe, PayPal, Shopify

**Media & Content:**
- YouTube, Spotify, Pexels, WordPress

**Business:**
- Zoom, Google Ads, Google Analytics, Meta (Facebook)

### 🎨 Admin Dashboard

- **Modern UI** with TailwindCSS
- **Dark mode** support
- **Real-time analytics** and monitoring
- **API Explorer** for testing endpoints
- **Service status** indicators
- **Content management** interface

---

## 📦 Deployment Options

### Option 1: Docker (Recommended for Production)

```bash
# Build the image
docker build -t websuite-platform .

# Run with Docker Compose
docker-compose up -d

# Or run directly
docker run -d \
  -p 8000:8000 \
  --env-file .env \
  --name websuite \
  --restart unless-stopped \
  websuite-platform
```

### Option 2: Cloudflare Pages (Managed Platform)

One-click deployment on Cloudflare's edge network:

1. Connect your GitHub repository
2. Configure environment variables
3. Deploy automatically on every push

See [Deployment Guide](docs/deployment/cloudflare-pages.md) for details.

### Option 3: Self-Hosted

Deploy on your own infrastructure:

- **VPS/Cloud Server** - Run with Docker or directly with Bun
- **Kubernetes** - Use the Docker image in your cluster
- **Any Node.js/Bun compatible platform**

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────┐
│           WebSuite Platform                      │
├─────────────────────────────────────────────────┤
│                                                 │
│  ┌──────────────┐  ┌──────────────┐           │
│  │   Frontend   │  │  Admin Panel │           │
│  │  (Static)    │  │  (Dashboard) │           │
│  └──────┬───────┘  └──────┬───────┘           │
│         │                 │                     │
│         └────────┬────────┘                     │
│                  │                               │
│         ┌────────▼────────┐                      │
│         │   Edge Runtime  │                      │
│         │   (Bun.js)      │                      │
│         └────────┬────────┘                      │
│                  │                               │
│  ┌───────────────┼───────────────┐              │
│  │               │               │              │
│  ┌───────┐  ┌────▼────┐  ┌───────┐             │
│  │  CMS  │  │  AI     │  │  API  │             │
│  │  RSS  │  │ Agents  │  │ REST  │             │
│  └───────┘  └─────────┘  └───────┘             │
│                                                 │
│  ┌──────────────────────────────────────────┐  │
│  │     30+ Service Integrations              │  │
│  │  GitHub, Gmail, Slack, Stripe, etc.       │  │
│  └──────────────────────────────────────────┘  │
└─────────────────────────────────────────────────┘
```

---

## 🛠️ Technology Stack

- **Runtime**: Bun.js (compatible with Node.js 18+)
- **Frontend**: HTML, CSS (TailwindCSS), JavaScript (Vanilla)
- **Backend**: Edge Functions with Bun runtime
- **Rendering**: HTMX for dynamic SSR
- **Editor**: Monaco Editor (VS Code engine)
- **AI**: Multiple models (Gemini, ChatGPT, Mistral AI, DeepSeek)
- **Cache**: Intelligent edge caching
- **Deployment**: Docker, Cloudflare Pages, or self-hosted

---

## 📚 Documentation

### Getting Started

- **[Installation Guide](docs/guide/installation.md)** - Complete setup instructions
- **[Quick Start](docs/guide/quick-start.md)** - Get up and running in 5 minutes
- **[Development Guide](docs/guide/development.md)** - Local development setup

### Core Features

- **[AI Agents](docs/guide/agents-architecture.md)** - Build and deploy intelligent agents
- **[Content Management](docs/content/articles.md)** - Manage your content sources
- **[Service Integrations](docs/configuration/overview.md)** - Connect external services
- **[API Documentation](docs/api/overview.md)** - Complete API reference

### Deployment

- **[Docker Deployment](docs/guide/installation.md#installation-en-production)** - Production deployment with Docker
- **[Cloudflare Pages](docs/deployment/cloudflare-pages.md)** - Managed platform deployment
- **[Environment Variables](docs/deployment/environment-variables.md)** - Configuration guide

### Advanced

- **[Server Architecture](docs/guide/server-architecture.md)** - How the platform works
- **[Security](docs/advanced/security.md)** - Best practices
- **[Customization](docs/advanced/customization.md)** - Extend the platform

---

## 🔑 Environment Variables

Key environment variables you'll need:

```env
# Admin
ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=your_secure_password

# Content Sources
BLOG_FEED_URL=https://yoursubstack.substack.com/feed
YOUTUBE_FEED_URL=https://www.youtube.com/feeds/videos.xml?channel_id=YOUR_ID
PODCAST_FEED_URL=https://anchor.fm/s/YOUR_ID/podcast/rss
EVENTS_FEED_URL=https://www.meetup.com/your-group/events/rss

# AI Services
GOOGLE_AI_KEY=your_gemini_api_key
OPENAI_API_KEY=your_chatgpt_api_key
MISTRAL_AI_API_KEY=your_mistral_api_key
DEEPSEEK_API_KEY=your_deepseek_api_key

# Integrations (optional)
GITHUB_TOKEN=your_github_token
SUPABASE_URL=your_supabase_url
SUPABASE_ANON_KEY=your_supabase_key
# ... and 25+ more services
```

See [.dev.vars.example](.dev.vars.example) for the complete list.

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📝 License

MIT License - See [LICENSE](LICENSE) for details.

---

## 📞 Support

- 📧 **Email**: community@websuite.cc
- 📖 **Documentation**: https://docs.websuite.cc
- 🐛 **Issues**: [GitHub Issues](https://github.com/websuite-cc/CMS/issues)
- 💬 **Community**: Join our Discord

---

## 🌟 Why WebSuite?

- ✅ **All-in-One Platform** - CMS, AI, IDE, and integrations in one place
- ✅ **Edge Performance** - Built on Bun.js for maximum speed
- ✅ **30+ Integrations** - Connect to all your favorite services
- ✅ **AI-Powered** - Intelligent agents that automate your workflows
- ✅ **Developer-Friendly** - Built-in IDE and comprehensive API
- ✅ **Production-Ready** - Docker support and managed deployment options
- ✅ **Open Source** - MIT License, fully customizable

---

<p align="center">
  Made with ❤️ for the developer community<br>
  <strong>WebSuite</strong> - Your complete web development platform<br>
  <small>Built on Edge with Bun</small>
</p>
