# CINA Protocol: 技术白皮书

**版本**: 1.0  
**日期**: 2025年1月15日  
**运营方**: CINA Labs

## 1. 摘要

CINA Protocol 是基于 f(x) 协议构建的去中心化杠杆交易系统，通过闪电贷机制实现零资本杠杆交易。协议采用 Diamond 架构（ERC-2535）提供模块化功能扩展，支持用户使用 stETH 作为抵押物进行杠杆交易，通过聚合多个流动性源提供最优交易路径。

## 2. 项目概述

### 2.1 项目名称
**CINA Protocol** - 去中心化杠杆交易协议

### 2.2 核心价值主张
- **零资本杠杆**: 通过闪电贷机制实现无需初始资本的杠杆交易
- **流动性聚合**: 整合多个 DeFi 协议，提供最优交易路径
- **模块化架构**: 基于 Diamond 模式的可扩展智能合约系统

### 2.3 目标用户
- **DeFi 交易者**: 寻求高效杠杆交易的用户
- **流动性提供者**: 为协议提供流动性的用户
- **开发者**: 集成杠杆交易功能的 DApp 开发者

### 2.4 问题与解决方案

**挑战**:
- 传统杠杆交易需要大量初始资本
- 流动性分散，交易效率低
- 缺乏统一的杠杆交易接口

**解决方案**:
- 闪电贷机制实现零资本杠杆
- 流动性聚合提供最优路径
- 统一 Router 接口支持多种策略

## 3. 架构概览

### 3.1 系统架构

```
┌─────────────────────────────────────────────────────────────┐
│                    CINA Protocol 架构                        │
├─────────────────────────────────────────────────────────────┤
│  Frontend Layer                                             │
│  ├── Next.js (React Framework)                             │
│  ├── Wagmi (Ethereum Integration)                           │
│  └── RainbowKit (Wallet Connection)                         │
├─────────────────────────────────────────────────────────────┤
│  Router System (Diamond Pattern)                            │
│  ├── DiamondCutFacet (Contract Upgrade)                     │
│  ├── RouterManagementFacet (Route Management)               │
│  ├── PositionOperateFacet (Position Operations)              │
│  └── FlashLoanFacet (Flash Loan Integration)               │
├─────────────────────────────────────────────────────────────┤
│  Core Protocol (f(x) Protocol)                             │
│  ├── PoolManager (Pool Management)                         │
│  ├── FxUSD (Stablecoin)                                     │
│  ├── AaveFundingPool (Funding Pool)                        │
│  └── PriceOracle (Price Data Source)                        │
└─────────────────────────────────────────────────────────────┘
```

### 3.2 关键组件

#### 3.2.1 Router 系统 (Diamond 架构)
- **Diamond 合约**: 核心路由合约，支持模块化功能扩展
- **7 个 Facets**: 模块化功能实现，包含 23 个核心函数
- **功能模块**: 合约升级、路由管理、仓位操作、闪电贷集成

#### 3.2.2 核心协议组件
- **PoolManager**: 池子管理和配置系统
- **FxUSD**: 协议稳定币，基于 f(x) 协议
- **AaveFundingPool**: 资金池实现，支持杠杆交易
- **PriceOracle**: 价格数据源，提供实时价格信息

#### 3.2.3 前端应用
- **Next.js**: React 全栈框架
- **Wagmi**: 以太坊连接库
- **RainbowKit**: 钱包连接组件
- **TypeScript**: 类型安全的开发环境

### 3.3 技术栈

#### 智能合约技术栈
- **Solidity**: ^0.8.26 (最新安全版本)
- **OpenZeppelin**: ^5.0.2 (安全合约库)
- **Foundry**: 测试和部署框架
- **Hardhat**: 开发环境工具

#### 前端技术栈
- **Next.js**: 14.2.5 (React 框架)
- **React**: 18.2.0 (UI 库)
- **TypeScript**: 5.4.5 (类型系统)
- **Tailwind CSS**: 3.4.10 (样式框架)
- **Wagmi**: 2.12.7 (以太坊集成)
- **Viem**: 2.9.20 (以太坊客户端)

#### 开发工具
- **pnpm**: 包管理器
- **ESLint**: 代码检查工具
- **Prettier**: 代码格式化工具

## 4. 合约与部署信息

### 4.1 网络配置
- **测试网**: Sepolia
- **链 ID**: 11155111
- **RPC URL**: https://sepolia.infura.io/v3/YOUR_PROJECT_ID

### 4.2 核心合约地址

#### 4.2.1 Router 系统 (Diamond 架构)
| 合约名称 | 地址 | 验证状态 | 功能描述 |
|---------|------|---------|---------|
| **Router (Diamond)** | `0xB8B3e6C7D0f0A9754F383107A6CCEDD8F19343Ec` | ⏳ 待验证 | 核心路由合约 |
| **DiamondCutFacet** | `0x1adb1d517f0fAd6695Ac5907CB16276FaC1C3e8B` | ⏳ 待验证 | 合约升级管理 |
| **RouterManagementFacet** | `0xD3A63FfBE2EDa3D0E07426346189000f39fDa1C0` | ⏳ 待验证 | 路由管理 |
| **PositionOperateFacet** | `0x6403A2D1A99e15369A1f5C46fA2983C619D0B410` | ⏳ 待验证 | 仓位操作 |

#### 4.2.2 核心协议合约
| 合约名称 | 地址 | 验证状态 | 功能描述 |
|---------|------|---------|---------|
| **PoolManager** | `0xBb644076500Ea106d9029B382C4d49f56225cB82` | ✅ 已验证 | 池子管理系统 |
| **FxUSD** | `0x085a1b6da46aE375b35Dea9920a276Ef571E209c` | ✅ 已验证 | 协议稳定币 |
| **AaveFundingPool** | `0x3C67A6Fea47A00f2Ce6D3c1D1f170558d2b091AB` | ⏳ 待验证 | 资金池实现 |
| **MockPriceOracle** | `0x0347f7d0952b3c55E276D42b9e2950Cc0523d787` | ✅ 已验证 | 价格预言机 |

### 4.3 Etherscan 验证链接
- **Router**: https://sepolia.etherscan.io/address/0xB8B3e6C7D0f0A9754F383107A6CCEDD8F19343Ec
- **PoolManager**: https://sepolia.etherscan.io/address/0xBb644076500Ea106d9029B382C4d49f56225cB82
- **FxUSD**: https://sepolia.etherscan.io/address/0x085a1b6da46aE375b35Dea9920a276Ef571E209c
- **MockPriceOracle**: https://sepolia.etherscan.io/address/0x0347f7d0952b3c55E276D42b9e2950Cc0523d787

## 5. 运行与复现说明

### 5.1 环境要求

#### 5.1.1 系统要求
- **Node.js**: >= 18.0.0
- **pnpm**: >= 8.0.0
- **Git**: >= 2.30.0

#### 5.1.2 开发工具
- **MetaMask**: 钱包连接
- **VS Code**: 推荐编辑器
- **Hardhat**: 合约开发环境
- **Foundry**: 合约测试框架

### 5.2 快速启动

#### 5.2.1 项目初始化
```bash
# 克隆项目
git clone https://github.com/your-org/cina-protocol.git
cd cina-protocol/app/v1

# 安装合约依赖
cd contracts
pnpm install

# 安装前端依赖
cd ../frontend
pnpm install
```

#### 5.2.2 环境配置

**合约环境配置**:
```bash
cd contracts
cp env.example .env
# 编辑 .env 文件，添加私钥和 RPC URL
```

**前端环境配置**:
```bash
cd frontend
cp .env.local.example .env.local
# 编辑 .env.local 文件，配置合约地址
```

### 5.3 开发环境启动

#### 5.3.1 本地开发模式
```bash
# 启动本地 Hardhat 网络
cd contracts
npx hardhat node

# 部署合约到本地网络
npx hardhat run scripts/deploy.js --network localhost

# 启动前端应用
cd frontend
NEXT_PUBLIC_USE_LOCAL=true pnpm dev
```

#### 5.3.2 测试网模式
```bash
# 部署到 Sepolia 测试网
cd contracts
npx hardhat run scripts/deploy-sepolia.ts --network sepolia

# 启动前端应用
cd frontend
pnpm dev
```

### 5.4 合约部署指南

#### 5.4.1 Hardhat 部署
```bash
cd contracts

# 编译合约
npx hardhat compile

# 运行测试
npx hardhat test

# 部署到 Sepolia
npx hardhat run scripts/deploy-router-sepolia.ts --network sepolia

# 验证合约
npx hardhat verify --network sepolia CONTRACT_ADDRESS
```

#### 5.4.2 Foundry 部署
```bash
cd contracts

# 编译
forge build

# 测试
forge test

# 部署
forge script script/DeployMockOracle.s.sol --rpc-url sepolia --broadcast

# 验证
forge verify-contract ADDRESS CONTRACT_PATH:CONTRACT_NAME --chain sepolia
```

### 5.5 前端开发指南

#### 5.5.1 基础设置
```bash
cd frontend

# 安装依赖
pnpm install

# 启动开发服务器
pnpm dev
```

#### 5.5.2 钱包连接配置
```bash
# 设置 WalletConnect 项目 ID
pnpm run setup-walletconnect
```

### 5.6 测试指南

#### 5.6.1 合约测试
```bash
cd contracts

# Hardhat 测试
npx hardhat test

# Foundry 测试
forge test

# 覆盖率测试
npx hardhat coverage
```

#### 5.6.2 前端测试
```bash
cd frontend

# 运行测试
pnpm test

# 类型检查
pnpm run type-check

# 代码检查
pnpm run lint
```

### 5.7 故障排除

#### 5.7.1 常见问题解决

**合约部署失败**:
```bash
# 清理缓存
npx hardhat clean
npx hardhat compile --force
```

**前端连接失败**:
```bash
# 检查网络配置
echo $NEXT_PUBLIC_CHAIN_ID
echo $NEXT_PUBLIC_RPC_URL
```

**钱包连接问题**:
- 确保 MetaMask 连接到正确的网络
- 检查 RPC URL 和 Chain ID
- 重启浏览器和 MetaMask

## 6. 团队与联系信息

### 6.1 开发团队
- **智能合约开发**: 基于 f(x) 协议构建
- **前端开发**: Next.js + Wagmi 技术栈
- **测试**: Foundry + Hardhat 测试框架

### 6.2 技术支持
- **文档**: 查看 `contracts/` 和 `frontend/` 目录下的详细文档
- **问题反馈**: 通过 GitHub Issues 提交
- **社区**: 加入我们的 Discord 社区

### 6.3 重要链接
- **GitHub**: https://github.com/your-org/cina-protocol
- **文档**: https://docs.cina-protocol.com
- **测试网**: https://sepolia.etherscan.io/
- **水龙头**: https://sepoliafaucet.com/

## 7. 相关文档

### 7.1 技术文档
- [完整部署指南](contracts/COMPLETE_DEPLOYMENT_GUIDE.md)
- [前端集成指南](contracts/FRONTEND_INTEGRATION_GUIDE.md)
- [开发计划](contracts/FRONTEND_DEVELOPMENT_PLAN.md)
- [本地开发指南](frontend/LOCAL_DEVELOPMENT_GUIDE.md)

### 7.2 部署文档
- [Sepolia 部署报告](contracts/SEPOLIA_FINAL_DEPLOYMENT_REPORT.md)
- [合约地址列表](contracts/DEPLOYMENT_ADDRESSES.md)
- [测试总结](contracts/FOUNDRY_测试总结.md)

---

**项目状态**: 合约已部署，前端开发中  
**最后更新**: 2025-01-15  
**版本**: v1.0.0
