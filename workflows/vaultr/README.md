# Vaultr n8n Workflows

Automation workflows for the Vaultr wealth intelligence platform.

## Workflows

### 1. Market Alerts (`market-alerts.json`)
- **Frequency**: Every 5 minutes
- **Purpose**: Monitor watchlist symbols for price changes, volume spikes, and sentiment shifts
- **Actions**: In-app notification + email via Resend
- **Data Sources**: Binance API, Vaultr API

### 2. Portfolio Sync (`portfolio-sync.json`)
- **Frequency**: Every 15 minutes
- **Purpose**: Sync portfolio positions with real-time prices, calculate P&L
- **Actions**: Update database, trigger rebalance alerts when positions move 10%+
- **Data Sources**: Vaultr market data API

### 3. Council Analysis (`council-analysis.json`)
- **Frequency**: Daily (24h)
- **Purpose**: Run AI council analysis on all watchlist symbols
- **Actions**: Store results, notify users of strong signals (60%+ consensus)
- **Data Sources**: Vaultr AI council API

## Environment Variables
```
VAULTR_API_URL=https://vaultr.co.za
VAULTR_SERVICE_KEY=your_service_key
RESEND_API_KEY=your_resend_key
```

## Setup
1. Import workflows into n8n instance
2. Configure environment variables
3. Activate workflows
4. Monitor execution logs in n8n dashboard

## Architecture
```
n8n (scheduler) --> Vaultr API --> Supabase (database)
                --> Binance API   --> Email (Resend)
                --> AI Council    --> GStack (Pub/Sub)
```
