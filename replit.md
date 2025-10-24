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
- **Authentication**: Privy (role-based auth with email/Google/wallet support)
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
│       │   │   ├── merchant/summary/  # Merchant inbound analytics
│       │   │   ├── user/spending/     # User outbound analytics
│       │   │   └── agent/receipt/     # Agent payment receipts
│       │   ├── components/  # Shared components
│       │   │   ├── LoginModal.tsx   # Role selection modal
│       │   │   └── NavBar.tsx       # Navigation with auth
│       │   ├── context/     # React context providers
│       │   │   └── UserContext.tsx  # User role management
│       │   ├── dashboard/   # Dashboard pages
│       │   │   ├── page.tsx           # Dashboard router
│       │   │   ├── MerchantDashboard.tsx  # Merchant view
│       │   │   └── UserDashboard.tsx      # User view
│       │   ├── pay/         # Payment interface page
│       │   ├── layout.tsx   # Root layout with providers
│       │   ├── page.tsx     # Homepage
│       │   └── providers.tsx # Privy/RainbowKit/Wagmi setup
│       ├── .env.local     # Environment variables
│       └── package.json   # Frontend dependencies
├── agents/
│   ├── merchant-agent.js  # Hedera agent implementation (JS)
│   └── merchant-agent.ts  # Hedera agent implementation (TS)
└── package.json           # Root package.json

```

## Recent Changes (Oct 24, 2025)

### Role-Based Authentication (Latest Update)
- **Integrated Privy Authentication**: Email, Google, and wallet login support
- **User Roles**: Merchant and User account types with localStorage persistence
- **Custom Login Modal**: Sleek role selection UI matching hackathon design
- **Shared NavBar**: Unified navigation with login/account management
- **Role-Based Dashboards**:
  - **Merchant Dashboard**: Inbound + outbound analytics, net income, transaction lists
  - **User Dashboard**: Personal spending history and analytics only
- **Updated APIs**: Address-aware endpoints for user-specific data queries
- **Authentication Flow**: Login → Role Selection → Personalized Dashboard
- **Design Consistency**: All new components maintain hackathon-winning aesthetic

### Initial Implementation
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

1. **Authentication System**:
   - Privy integration for email, Google, and wallet login
   - Role selection: Merchant or User account types
   - Role persistence via localStorage
   - Unified NavBar with login/account management
   - Logout functionality clearing role and auth state

2. **Dashboard** (`/dashboard`):
   - **For Merchants**:
     - Total inbound revenue with animated count-up
     - Total outbound spending tracking
     - Net income calculation
     - Inbound/outbound transaction lists with dual-panel layout
     - Live Recharts visualization (inbound revenue chart)
     - Real-time data updates every 10 seconds
   - **For Users**:
     - Total spending overview
     - Average transaction value
     - Transaction count tracking
     - Spending history chart (Recharts)
     - Detailed transaction table with BaseScan links
   - Glass morphism KPI cards with glowing borders
   - Live pulse indicators

3. **Payment Interface** (`/pay`):
   - Multi-wallet connection (20+ wallets via RainbowKit)
   - USDC payments on Base network
   - Dynamic recipient addresses
   - Transaction tracking
   - Success/error feedback with toast notifications

4. **API Routes**:
   - `GET /api/merchant/summary?address={address}` - Inbound transactions for specified address
   - `GET /api/user/spending?address={address}` - Outbound transactions for specified address
   - `POST /api/agent/receipt` - Saves Hedera agent payment receipts
   - `GET /api/agent/receipt` - Retrieves agent payment history

## Environment Variables
Required in `apps/web/.env.local`:
- `NEXT_PUBLIC_PRIVY_APP_ID` - Privy application ID for authentication
- `NEXT_PUBLIC_BLOCKSCOUT_BASE` - Blockscout API endpoint
- `NEXT_PUBLIC_MERCHANT_ADDRESS` - Default merchant wallet address
- `NEXT_PUBLIC_USDC_ADDRESS` - USDC token contract address on Base
- `NEXT_PUBLIC_WALLETCONNECT_PROJECT_ID` - WalletConnect project ID

## Running the Project
- **Development**: The workflow "Server" runs `npm run dev` in the apps/web directory
- **Port**: 5000 (required for Replit)
- **Host**: 0.0.0.0 (required for Replit proxy)

## Known Issues
- Console warnings about @react-native-async-storage/async-storage (non-blocking, MetaMask SDK)
- WalletConnect API 403 errors (uses local config fallback, non-blocking)
- Privy iframe load warnings (non-blocking, authentication still functional)
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
