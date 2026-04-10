# n8n Workflow Integration with Vaultr

## Connection to MiroFish
Workflows are triggered via the n8n webhook module at `src/lib/n8n/webhooks.ts`.

## Webhook Endpoints
- `/webhook/vaultr-market-alerts` - Triggered by market scan cron
- `/webhook/vaultr-portfolio-sync` - Triggered on portfolio updates
- `/webhook/vaultr-council-analysis` - Triggered on council analysis requests

## Environment Variables (in MiroFish .env)
- `N8N_WEBHOOK_URL` - Base URL of n8n instance
- `N8N_API_KEY` - API key for authentication

## Workflow Files
- `market-alerts.json` - 5-min interval price/volume/sentiment monitoring
- `portfolio-sync.json` - Real-time portfolio data synchronization
- `council-analysis.json` - Multi-model AI council analysis pipeline
