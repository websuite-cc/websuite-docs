# ❓ Frequently Asked Questions

## General

### What is WebSuite Platform?

WebSuite is a **complete web development platform** that combines:
- Headless CMS with multi-source content aggregation
- AI Agents powered by multiple models (Gemini, ChatGPT, Mistral AI, DeepSeek)
- Built-in IDE (Monaco Editor) for code editing
- 30+ service integrations (GitHub, Gmail, Slack, Stripe, WhatsApp, etc.)
- MCP Workers for intelligent automation
- Modern admin dashboard

### Is it free?

The platform itself is open source (MIT License). You can:
- **Self-host** for free on your own infrastructure
- **Use Docker** on any cloud provider
- **Deploy on Cloudflare Pages** (free tier available)
- **Use managed platform** (paid option with premium features)

### What services are supported?

WebSuite integrates with **30+ services**:

**AI & ML:**
- Google Gemini, OpenAI ChatGPT, Mistral AI, DeepSeek, DeepL

**Communication:**
- Gmail, WhatsApp Business, Twilio SMS, Slack

**Development:**
- GitHub, GitLab, Supabase

**Productivity:**
- Google Workspace (Drive, Docs, Sheets, Calendar, Meet, Forms)
- Airtable, Trello

**E-commerce:**
- Stripe, PayPal, Shopify

**Media:**
- YouTube, Spotify, Pexels, WordPress

**Business:**
- Zoom, Google Ads, Google Analytics, Meta

See the [admin dashboard](/admin) for the complete list.

### Can I add custom integrations?

Yes! The platform is fully extensible. You can:
- Add new service integrations via environment variables
- Create custom AI agents
- Extend the API with new endpoints
- Customize the frontend templates

## Installation

### How do I install WebSuite?

```bash
# With Bun (recommended)
bun install @websuite-cc/platform
cd node_modules/@websuite-cc/platform

# Or with NPM
npm install @websuite-cc/platform
cd node_modules/@websuite-cc/platform
```

See the [Quick Start Guide](../guide/quick-start.md) for details.

### What are the system requirements?

- **Runtime**: Bun 1.0+ (recommended) or Node.js 18+
- **Memory**: 512MB minimum (1GB+ recommended)
- **Storage**: 100MB+ for the platform
- **Platform**: Linux, macOS, Windows (with WSL2)

### How long does installation take?

Less than 5 minutes! Most time is spent configuring environment variables.

### Can I deploy on my own infrastructure?

Yes! You can deploy:
- **Docker** on any cloud provider
- **Self-hosted** with Bun or Node.js
- **Kubernetes** using the Docker image
- **Cloudflare Pages** for managed deployment

## Configuration

### What environment variables do I need?

Minimum required:
```env
ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=your_secure_password
```

Optional (for content sources):
```env
BLOG_FEED_URL=https://yoursubstack.substack.com/feed
YOUTUBE_FEED_URL=https://www.youtube.com/feeds/videos.xml?channel_id=YOUR_ID
```

See [.dev.vars.example](../../.dev.vars.example) for the complete list of 50+ variables.

### Are environment variables secure?

Yes! Environment variables are:
- Never committed to Git (`.dev.vars` is in `.gitignore`)
- Encrypted in production (Cloudflare Pages)
- Stored securely in Docker secrets
- Accessible only to authenticated admin users

### How do I get API keys?

Each service has its own process:
- **Google AI**: https://aistudio.google.com/app/apikey
- **OpenAI**: https://platform.openai.com/api-keys
- **GitHub**: https://github.com/settings/tokens
- See the admin dashboard for links to all service configurations

## AI Agents

### What are AI Agents?

AI Agents are intelligent workers that:
- Understand context and make decisions
- Generate and deploy code automatically
- Execute complex workflows
- Support MCP (Model Context Protocol)

### Which AI models are supported?

- **Google Gemini** (recommended for code generation)
- **OpenAI ChatGPT**
- **Mistral AI**
- **DeepSeek**
- **DeepL** (for translation)

### How do I create an AI agent?

1. Go to Admin Dashboard → Agents
2. Click "Create New Agent"
3. Describe what you want the agent to do
4. The AI will generate the code
5. Deploy with one click

## API

### Is the API public?

Most endpoints are public:
- `/api/posts` - Blog posts
- `/api/videos` - YouTube videos
- `/api/podcasts` - Podcast episodes
- `/api/events` - Events

Admin endpoints require authentication:
- `/api/login` - Authentication
- `/api/admin/*` - Admin functions
- `/api/agents/*` - Agent management

### How do I authenticate?

Use the `X-Auth-Key` header with your admin password:

```http
X-Auth-Key: your_admin_password
```

### Are there rate limits?

- **Self-hosted**: No limits (your infrastructure)
- **Cloudflare Pages Free**: 100,000 requests/day
- **Managed Platform**: Unlimited (paid plans)

## Content

### What content sources are supported?

- **RSS Feeds** - Any RSS/Atom feed
- **Substack** - Blog articles
- **YouTube** - Video channels
- **Podcasts** - Anchor.fm, Spotify, Apple Podcasts
- **Events** - Meetup, Eventbrite

### How often is content updated?

Content is cached for 180 seconds (3 minutes). After publishing new content, it appears within 3 minutes.

### Can I force a refresh?

Yes! Use the `/api/clear-cache` endpoint (requires authentication).

### Are images included?

Yes! Images are automatically extracted from RSS feeds and served via CDN.

## Deployment

### Can I use my own domain?

Yes! Configure your domain in:
- **Docker**: Set up reverse proxy (Nginx, Caddy)
- **Cloudflare Pages**: Add custom domain in settings
- **Self-hosted**: Configure DNS and SSL

### Is deployment automatic?

- **Docker**: Manual or CI/CD pipeline
- **Cloudflare Pages**: Automatic on Git push
- **Self-hosted**: Manual or your own CI/CD

### Can I have multiple environments?

Yes! You can set up:
- **Development** - Local with `.dev.vars`
- **Staging** - Separate Docker container or Cloudflare preview
- **Production** - Production deployment

## Support

### Where can I get help?

- 📧 **Email**: community@websuite.cc
- 🐛 [GitHub Issues](https://github.com/websuite-cc/CMS/issues)
- 📖 [Documentation](https://docs.websuite.cc)
- 💬 **Discord**: Join our community

### Can I contribute?

Yes! Contributions are welcome:
1. Fork the repository
2. Create a feature branch
3. Submit a Pull Request

See [Contributing](../../README.md#-contributing) for details.

## Troubleshooting

### Content is not displaying

1. Check RSS feed URLs are correct and accessible
2. Clear cache: `/api/clear-cache`
3. Wait 3 minutes for cache refresh
4. Check browser console for errors

### Getting 500 errors

1. Check server logs
2. Verify environment variables are set
3. Check RSS feed URLs are valid
4. Ensure API keys are correct

### Admin dashboard not working

1. Verify `ADMIN_EMAIL` and `ADMIN_PASSWORD` are correct
2. Clear browser cache
3. Check authentication token in localStorage
4. Verify server is running

### AI agents not executing

1. Check AI API keys are configured
2. Verify GitHub token for code deployment
3. Check agent execution logs
4. Ensure CronJob API key is set (for scheduled agents)

For more help, see [Troubleshooting Guide](troubleshooting.md).
