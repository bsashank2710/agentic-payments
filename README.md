# Agentic Payments

A cross-chain payment analytics system powered by Hedera Agent Kit and Base network integration.

## 🚀 Features

- **Multi-Wallet Support**: Connect with MetaMask, WalletConnect, Coinbase Wallet, and more
- **Cross-Chain Analytics**: Real-time payment tracking across Base network
- **Hedera Agent Integration**: Automated payment processing with Hedera Agent Kit
- **Dynamic Recipients**: Send payments to any Ethereum address
- **Real-time Dashboard**: Live analytics and transaction monitoring

## 🛠️ Tech Stack

- **Frontend**: Next.js 14, React 18, TypeScript
- **Styling**: Tailwind CSS 3
- **Wallet Integration**: RainbowKit, Wagmi, Viem
- **Blockchain**: Base Network, Hedera
- **Analytics**: Blockscout API

## ⚠️ Important Notes

- **Agent Receipts**: Currently stored in-memory (not persistent). For production use, implement a database backend.
- **Development**: Configured for Replit environment (port 5000, 0.0.0.0 binding)
- **Real Data**: Dashboard pulls actual transaction data from Base network via Blockscout API

## 📦 Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/agentic-payments.git
cd agentic-payments
```

2. Install dependencies:
```bash
npm install
```

3. Set up environment variables:
```bash
cp apps/web/.env.local.example apps/web/.env.local
```

4. Configure your environment variables in `apps/web/.env.local`:
```
NEXT_PUBLIC_BLOCKSCOUT_BASE=https://base.blockscout.com/api
NEXT_PUBLIC_MERCHANT_ADDRESS=your_merchant_address
NEXT_PUBLIC_USDC_ADDRESS=0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913
NEXT_PUBLIC_WALLETCONNECT_PROJECT_ID=your_project_id
```

5. Start the development server:
```bash
npm run dev
```

## 🌐 Usage

### Dashboard
Visit `http://localhost:5000/dashboard` (or port 3000 for non-Replit) to view:
- Real-time payment analytics
- Base network transaction data
- Agent payment receipts
- Total revenue calculations

### Payment Interface
Visit `http://localhost:5000/pay` (or port 3000 for non-Replit) to:
- Connect your wallet (supports 20+ wallets)
- Enter payment amount
- Specify recipient address
- Process cross-chain payments

## 🔧 API Endpoints

- `GET /api/merchant/summary` - Base network analytics
- `POST /api/agent/receipt` - Hedera agent payment receipts
- `GET /api/agent/receipt` - Retrieve payment history

## 🤖 Hedera Agent Integration

The system integrates with Hedera Agent Kit for automated payment processing:

```javascript
// Agent payment receipt
{
  "txHash": "0x...",
  "from": "sender_address",
  "to": "recipient_address", 
  "amount": "100.0",
  "token": "USDC",
  "timestamp": "2025-10-24T21:00:00Z"
}
```

## 🚀 Deployment

### Vercel (Recommended)
1. Connect your GitHub repository to Vercel
2. Set environment variables in Vercel dashboard
3. Deploy automatically on push to main branch

### Manual Deployment
```bash
npm run build
npm start
```

## 📊 Analytics Features

- **Real-time Updates**: Live transaction monitoring
- **Cross-chain Data**: Base network integration
- **Agent Payments**: Hedera agent transaction tracking
- **Revenue Analytics**: Total USDC calculations
- **Transaction History**: Complete payment logs

## 🔗 Supported Networks

- **Base Network**: Primary payment network
- **Ethereum**: Wallet connection support
- **Hedera**: Agent integration
- **Multi-chain**: Extensible architecture

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push to branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Hedera Agent Kit](https://github.com/hashgraph/hedera-agent-kit) for agent integration
- [RainbowKit](https://www.rainbowkit.com/) for wallet connection
- [Base Network](https://base.org/) for blockchain infrastructure
- [Blockscout](https://blockscout.com/) for blockchain analytics
