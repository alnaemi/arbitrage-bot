# 🚀 Arbitrage Bot - DeFi Flash Loan Arbitrage

> **Professional-grade arbitrage bot for detecting and executing profitable trading opportunities between PancakeSwap and BakerySwap using flash loans**

## 📋 Overview

This arbitrage bot is designed to automatically detect and execute profitable trading opportunities between PancakeSwap and BakerySwap on the Binance Smart Chain (BSC). It leverages flash loans to execute risk-free arbitrage trades without requiring upfront capital, making it an ideal solution for DeFi traders and yield farmers.

### 🎯 Key Features

- **🔍 Real-time Price Monitoring**: Continuously monitors price differences between PancakeSwap and BakerySwap
- **⚡ Flash Loan Integration**: Uses flash loans to execute arbitrage without capital requirements
- **💰 Profit Optimization**: Calculates optimal trade sizes and gas costs for maximum profitability
- **🛡️ Risk Management**: Built-in safety checks and gas cost analysis
- **📊 Live Trading Analytics**: Real-time logging of prices, spreads, and trade execution
- **🔧 Configurable Parameters**: Easily adjustable trading thresholds and token pairs

### 🏗️ Architecture

The bot consists of two main components:

1. **TypeScript Bot** (`index.ts`): Monitors prices and triggers arbitrage opportunities
2. **Smart Contract** (`FlashLoaner.sol`): Executes flash loan arbitrage trades

## 🚀 Quick Start

### Prerequisites

- Node.js (v14 or higher)
- Yarn or npm
- BSC wallet with BNB for gas fees
- Environment variables configured

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/arbitrage-bot.git
cd arbitrage-bot

# Install dependencies
yarn install

# Configure environment variables
cp .env.example .env
# Edit .env with your configuration
```

### Configuration

Create a `.env` file with the following variables:

```env
PRIVATE_KEY=your_wallet_private_key
FLASH_LOANER=deployed_flash_loaner_contract_address
RPC_LINK=https://bsc-dataseed.binance.org/
```

### Running the Bot

```bash
# Start the arbitrage bot
yarn start
```

## 📊 How It Works

### 1. Price Monitoring
The bot continuously monitors ETH/DAI (or other token pair) prices on both PancakeSwap and BakerySwap by listening to new blocks on the BSC network.

### 2. Opportunity Detection
When a price discrepancy is detected, the bot calculates:
- Price spread between exchanges
- Potential profit after gas costs
- Optimal trade direction (ETH → DAI or DAI → ETH)

### 3. Flash Loan Execution
If profitable, the bot triggers a flash loan through the smart contract:
1. Borrows tokens from PancakeSwap
2. Swaps on BakerySwap at better price
3. Repays the flash loan
4. Keeps the profit

### 4. Profit Calculation
```typescript
const spread = Math.abs((priceBakerySwap / pricePancakeSwap - 1) * 100) - 0.6
const shouldTrade = spread > (tradeAmount / reserveAmount)
```

## 🔧 Technical Details

### Smart Contract Features
- **Flash Loan Integration**: Leverages PancakeSwap's flash loan functionality
- **Gas Optimization**: Minimizes transaction costs for maximum profitability
- **Safety Checks**: Ensures proper token approvals and transfers
- **Error Handling**: Graceful handling of failed transactions

### Bot Features
- **Real-time Block Monitoring**: Listens to new BSC blocks for price updates
- **Dynamic Gas Pricing**: Adjusts gas costs based on network conditions
- **Configurable Thresholds**: Adjustable profit margins and trade sizes
- **Comprehensive Logging**: Detailed transaction and profit tracking

## 📈 Performance Metrics

The bot is designed to capture arbitrage opportunities with:
- **Minimum Spread**: 0.6% + gas costs
- **Trade Sizes**: Configurable ETH/DAI amounts
- **Execution Speed**: Sub-second response to price changes
- **Success Rate**: High success rate with proper gas management

## 🛠️ Customization

### Adding New Token Pairs
1. Update token addresses in `index.ts`
2. Modify factory addresses for new DEXes
3. Adjust trade amounts and thresholds

### Adjusting Parameters
```typescript
const ETH_TRADE = 10;    // ETH trade amount
const DAI_TRADE = 3500;  // DAI trade amount
const spread = Math.abs((priceBakerySwap / pricePancakeSwap - 1) * 100) - 0.6;
```

## 🔒 Security Considerations

- **Private Key Security**: Never commit private keys to version control
- **Gas Limits**: Set appropriate gas limits to prevent failed transactions
- **Slippage Protection**: Built-in protection against price slippage
- **Contract Auditing**: Smart contract should be audited before mainnet deployment

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## ⚠️ Disclaimer

This software is for educational and research purposes. Trading cryptocurrencies involves significant risk. Use at your own risk and never invest more than you can afford to lose.

## 📞 Support

For support, You can find my contact in github profile.

---

**Built with ❤️ for the DeFi community**
