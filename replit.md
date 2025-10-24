# Agentic Payments - Project Documentation

## Overview
A cross-chain payment analytics system powered by Hedera Agent Kit and Base network integration. This project was imported from GitHub and required complete frontend implementation.

## Purpose
- Multi-wallet support for Web3 payments
- Real-time payment analytics across Base network
- Hedera Agent integration for automated payment processing
- Dynamic recipient payment system

## Tech Stack
- **Frontend**: Next.js 14, React 18, TypeScript
- **Styling**: Tailwind CSS 3
- **Wallet Integration**: RainbowKit, Wagmi, Viem
- **Blockchain**: Base Network (Ethereum L2), Hedera
- **Analytics**: Blockscout API

## Project Structure
```
/
├── apps/
│   └── web/               # Next.js frontend application
│       ├── app/           # App router pages and API routes
│       │   ├── api/       # API endpoints
│       │   │   ├── merchant/summary/  # Base network analytics
│       │   │   └── agent/receipt/     # Agent payment receipts
│       │   ├── dashboard/ # Analytics dashboard page
│       │   ├── pay/       # Payment interface page
│       │   ├── layout.tsx # Root layout with providers
│       │   ├── page.tsx   # Homepage
│       │   └── providers.tsx # RainbowKit/Wagmi setup
│       ├── .env.local     # Environment variables
│       └── package.json   # Frontend dependencies
├── agents/
│   ├── merchant-agent.js  # Hedera agent implementation (JS)
│   └── merchant-agent.ts  # Hedera agent implementation (TS)
└── package.json           # Root package.json

```

## Recent Changes (Oct 24, 2025)
- Created complete Next.js 14 frontend (original import was incomplete)
- Set up RainbowKit wallet connection with Base network support
- Implemented payment analytics dashboard with real Blockscout API integration
- Created payment interface page with USDC transfer functionality
- Configured for Replit environment (port 5000, 0.0.0.0 binding)
- Downgraded from Next.js 16/React 19 to Next.js 14/React 18 for memory constraints
- Downgraded from Tailwind 4 to Tailwind 3 for compatibility
- Set up deployment configuration for autoscale

### Hackathon-Worthy Redesign (Latest)
- **Visual Impact**: Striking animated gradient backgrounds, floating particle effects, glowing buttons
- **Data Visualization**: Integrated Recharts for real-time transaction analytics with smooth area charts
- **Animations**: Purposeful animations including gradient flows, fade-in-up transitions, count-up effects, live pulse indicators
- **Modern Effects**: Glass morphism cards, animated gradient borders, radial glows, floating particles layer
- **Color Palette**: Deep navy background with vibrant gradient accents (blue-purple-pink spectrum)
- **Typography**: Gradient text headings, system fonts for performance
- **Components**: Glass cards with backdrop blur, glowing hover states, animated borders
- **Hero Section**: Eye-catching gradient typography, particle effects, CTA buttons with glow effects
- **Dashboard**: Live KPI cards with pulse animations, real-time Recharts visualization, automated data updates
- **Payment Interface**: Interactive glass cards, network status indicators, feature showcase section
- **Layout**: Clean navigation, professional spacing, responsive grid systems
- **Dependencies**: Added react-is for Recharts compatibility

## Key Features
1. **Dashboard** (`/dashboard`):
   - Total revenue tracking with animated count-up effects
   - Live transaction chart using Recharts (AreaChart visualization)
   - Base network transaction analytics with pulse indicators
   - Agent payment receipts table
   - Real-time data updates every 10 seconds
   - Glass morphism KPI cards with glowing borders

2. **Payment Interface** (`/pay`):
   - Multi-wallet connection (20+ wallets via RainbowKit)
   - USDC payments on Base network
   - Dynamic recipient addresses
   - Transaction tracking

3. **API Routes**:
   - `GET /api/merchant/summary` - Fetches Base network analytics from Blockscout
   - `POST /api/agent/receipt` - Saves Hedera agent payment receipts
   - `GET /api/agent/receipt` - Retrieves agent payment history

## Environment Variables
Required in `apps/web/.env.local`:
- `NEXT_PUBLIC_BLOCKSCOUT_BASE` - Blockscout API endpoint
- `NEXT_PUBLIC_MERCHANT_ADDRESS` - Merchant wallet address
- `NEXT_PUBLIC_USDC_ADDRESS` - USDC token contract address on Base
- `NEXT_PUBLIC_WALLETCONNECT_PROJECT_ID` - WalletConnect project ID

## Running the Project
- **Development**: The workflow "Server" runs `npm run dev` in the apps/web directory
- **Port**: 5000 (required for Replit)
- **Host**: 0.0.0.0 (required for Replit proxy)

## Known Issues
- Console warnings about @react-native-async-storage/async-storage (non-blocking)
- WalletConnect API 403 errors (uses local config fallback, non-blocking)
- MetaMask SDK warnings (non-blocking)

## Deployment
- **Type**: Autoscale (stateless web app)
- **Build**: `cd apps/web && npm run build`
- **Run**: `cd apps/web && npm run start`

## Notes
- Original GitHub import had empty apps/web directory
- Built entire frontend from scratch based on README specifications
- Uses in-memory storage for agent receipts (not persistent)
- Real transaction data pulled from Base network via Blockscout
