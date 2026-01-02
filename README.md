# CallAlly Signup Landing Page

Minimal, fast signup page with Stripe integration for CallAlly founding members.

## Features

- ✨ Beautiful dark theme with animated particles
- 💳 Stripe Checkout integration (one-time setup + monthly subscription)
- 📱 Fully responsive design
- ⚡ Fast, lightweight (no React/Vue/build tools)
- 🔒 Secure webhook handling for Stripe events

## Quick Start

```bash
npm install
npm start
```

Visit `http://localhost:3000`

## Configuration

1. Copy `.env.example` to `.env`
2. Add your Stripe keys:
   - `STRIPE_SECRET_KEY` - Get from Stripe Dashboard
   - `STRIPE_WEBHOOK_SECRET` - Create webhook endpoint in Stripe Dashboard
3. Set `DOMAIN` to your production URL

## Deployment

### Railway
```bash
railway link
railway up
```

### Heroku
```bash
heroku create callally-signup
git push heroku main
heroku config:set STRIPE_SECRET_KEY=sk_live_...
```

### Vercel
```bash
vercel
```

## Stripe Setup

1. Create a Stripe account at stripe.com
2. Get your Secret Key from Dashboard → API Keys
3. Create a webhook endpoint:
   - Go to Developers → Webhooks
   - Add endpoint: `https://yourdomain.com/api/webhook`
   - Select events: `checkout.session.completed`
   - Copy signing secret to `.env` as `STRIPE_WEBHOOK_SECRET`

## Testing

Use Stripe test cards:
- Success: `4242 4242 4242 4242`
- Decline: `4000 0000 0000 0002`
- Expiry: Any future date
- CVC: Any 3 digits

## API Endpoints

- `GET /` - Signup page
- `POST /api/checkout` - Create Stripe checkout session
- `POST /api/webhook` - Stripe webhook handler
- `GET /health` - Health check

## Environment Variables

| Variable | Description |
|----------|-------------|
| `PORT` | Server port (default: 3000) |
| `DOMAIN` | Production domain for redirects |
| `STRIPE_SECRET_KEY` | Stripe secret key |
| `STRIPE_WEBHOOK_SECRET` | Stripe webhook signing secret |
