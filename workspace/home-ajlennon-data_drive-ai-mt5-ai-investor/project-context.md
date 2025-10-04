# MetaTrader 5 AI Trading System - Live Forex Trading

## Status: PRODUCTION READY (Live Trading Active)

### Project Overview
Advanced MQL5-based AI trading system with genetic optimization and proven profitability in live forex markets.

### Key Features
- **Live Trading**: Successfully deployed in production forex markets
- **Genetic Optimization**: AI-driven parameter optimization for market adaptation
- **Risk Management**: Advanced position sizing and drawdown protection
- **GBP/USD Specialization**: Breakout strategy with multi-timeframe analysis

### Trading Performance
- **Strategy**: GBP/USD breakout with dynamic risk-reward optimization
- **Optimization**: Genetic algorithms for parameter evolution
- **Risk Controls**: Kelly Criterion position sizing, dynamic stop loss
- **Performance Metrics**: Profit factor, Sharpe ratio, maximum drawdown tracking

### Technical Implementation
```
mt5-ai-investor/
├── GBPBreakoutEA_v152.mq5     # Production version (current)
├── GBPBreakoutEA_v151_PreRelease.mq5  # Development version
├── testing/                   # Backtesting and optimization
└── PRODUCTION_DEPLOYMENT_GUIDE.md
```

### AI Optimization
- **Genetic Algorithm**: Population-based parameter evolution
- **Fitness Function**: Multi-objective optimization (profit, drawdown, Sharpe)
- **Market Adaptation**: Real-time parameter adjustment based on conditions
- **Performance Monitoring**: Continuous strategy effectiveness evaluation

### Production Infrastructure
- **Platform**: MetaTrader 5 with VPS deployment
- **Monitoring**: 24/7 operation with real-time performance tracking
- **Risk Controls**: Account protection, position limits, emergency stops
- **Redundancy**: Multiple server deployment for reliability

### Key Algorithms
```mql5
// Genetic optimization parameters
input int PopulationSize = 100;
input int GenerationCount = 50;
input double MutationRate = 0.1;
input double CrossoverRate = 0.8;
```

### Integration
- **AI Platform**: Data pipeline connection to AI Investment Analysis Platform
- **Performance Analytics**: Python-based analysis and strategy refinement
- **Risk Management**: Multi-level protection and correlation analysis

---
**Repository**: `/data_drive/ai/mt5-ai-investor/`  
**Status**: Live trading with genetic optimization (v152 Production)