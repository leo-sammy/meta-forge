# MetaForge Protocol

**Next-generation Web3 gaming infrastructure that transforms digital ownership through interconnected virtual economies and player-centric asset management.**

## Overview

MetaForge Protocol represents a paradigm shift in blockchain gaming, creating a unified ecosystem where players truly own their digital assets across multiple game universes. Built with mathematical precision on Stacks blockchain, it leverages Bitcoin's unparalleled security to create persistent gaming identities, tradeable assets, and merit-driven economic incentives.

The protocol introduces revolutionary concepts including cross-dimensional asset portability, algorithmic rarity distribution, and dynamic player progression systems that adapt to individual playstyles. Advanced anti-cheat mechanisms and transparent governance ensure fair play while sophisticated reward algorithms create sustainable tokenomics for long-term ecosystem growth.

## 🚀 Features

### Core Gaming Infrastructure

- **Cross-Dimensional Asset Portability**: Assets can be used across multiple game worlds
- **Dynamic Player Progression**: Adaptive leveling system with experience-based advancement
- **Merit-Driven Economics**: Reward distribution based on player performance and engagement
- **Persistent Gaming Identities**: Avatar system with permanent achievements and progression

### Asset Management

- **NFT Game Assets**: Unique items with rarity, power levels, and world-specific attributes
- **Avatar NFTs**: Player identities with customizable attributes and progression tracking
- **Algorithmic Rarity Distribution**: Fair and transparent asset rarity mechanics
- **Experience-Based Leveling**: Assets and avatars gain experience and level up over time

### Economic Systems

- **Leaderboard Competition**: Skill-based ranking with transparent scoring
- **Reward Distribution**: Automated prize pools based on performance metrics
- **Protocol Fee Management**: Configurable fees for sustainable ecosystem growth
- **Multi-World Economy**: Separate economic zones with unique entry requirements

## 📋 Technical Specifications

### Smart Contract Architecture

The MetaForge Protocol is implemented as a comprehensive Clarity smart contract with the following components:

#### NFT Tokens

- `metaforge-asset`: Game items and equipment
- `metaforge-avatar`: Player identities and progression

#### Core Data Structures

- **Asset Metadata**: Name, description, rarity, power level, world association, attributes, experience, and level
- **Avatar Metadata**: Player name, level, experience, achievements, equipped assets, and world access permissions
- **Game Worlds**: Virtual environments with unique characteristics and entry requirements
- **Leaderboard**: Player rankings, statistics, and reward tracking

#### Constants and Configuration

- Maximum level: 100
- Maximum experience per level: 1,000
- Base experience requirement: 100
- Protocol fee: Configurable (default: 10)
- Maximum leaderboard entries: Configurable (default: 50)

## 🛠 Installation & Setup

### Prerequisites

- [Clarinet](https://github.com/hirosystems/clarinet) for local development
- Node.js (v14+) for testing framework
- Git for version control

### Local Development

```bash
# Clone the repository
git clone https://github.com/leo-sammy/meta-forge.git
cd meta-forge

# Install dependencies
npm install

# Run contract checks
clarinet check

# Run tests
npm test
```

## 📖 API Reference

### Core Functions

#### Protocol Management

**`initialize-protocol`**

```clarity
(initialize-protocol (entry-fee uint) (max-entries uint))
```

Initializes protocol configuration. Only callable by protocol admins.

#### Asset Management

**`mint-metaforge-asset`**

```clarity
(mint-metaforge-asset 
  (name (string-ascii 50))
  (description (string-ascii 200))
  (rarity (string-ascii 20))
  (power-level uint)
  (world-id uint)
  (attributes (list 10 (string-ascii 20))))
```

Mints a new game asset NFT with specified properties.

**`transfer-game-asset`**

```clarity
(transfer-game-asset (token-id uint) (recipient principal))
```

Transfers ownership of a game asset to another player.

#### Avatar System

**`create-avatar`**

```clarity
(create-avatar 
  (name (string-ascii 50))
  (world-access (list 10 uint)))
```

Creates a new player avatar with world access permissions.

**`update-avatar-experience`**

```clarity
(update-avatar-experience (avatar-id uint) (experience-gained uint))
```

Updates avatar experience and handles automatic level progression.

#### World Management

**`create-game-world`**

```clarity
(create-game-world 
  (name (string-ascii 50))
  (description (string-ascii 200))
  (entry-requirement uint))
```

Creates a new game world with specified entry requirements.

#### Leaderboard & Rewards

**`update-player-score`**

```clarity
(update-player-score (player principal) (new-score uint))
```

Updates a player's leaderboard score and game statistics.

**`distribute-rewards`**

```clarity
(distribute-rewards)
```

Distributes rewards to eligible players based on performance metrics.

### Read-Only Functions

**`get-world-details`**

```clarity
(get-world-details (world-id uint))
```

Returns detailed information about a specific game world.

**`get-avatar-details`**

```clarity
(get-avatar-details (avatar-id uint))
```

Returns comprehensive avatar metadata including progression and achievements.

**`get-next-level-requirement`**

```clarity
(get-next-level-requirement (avatar-id uint))
```

Calculates experience required for next level advancement.

**`can-receive-experience`**

```clarity
(can-receive-experience (avatar-id uint) (experience-amount uint))
```

Validates if an avatar can receive specified experience amount.

## 🎮 Game Mechanics

### Experience & Leveling System

- **Base Experience**: 100 XP required for first level
- **Progressive Requirements**: Each level requires `current_level * 100` XP
- **Maximum Level**: 100 (configurable)
- **Experience Validation**: Prevents exploitation with mathematical limits

### Rarity System

Assets support five rarity tiers:

- `common`: Standard items with basic attributes
- `uncommon`: Enhanced items with improved stats
- `rare`: Valuable items with special properties
- `epic`: Powerful items with unique abilities
- `legendary`: Ultra-rare items with maximum potential

### World Access Control

- Players gain access to worlds through avatar configuration
- Entry requirements can be set per world (level, assets, etc.)
- Cross-world asset compatibility enables true interoperability

## 🔐 Security & Access Control

### Authorization Levels

- **Protocol Admins**: Full system control and configuration access
- **Players**: Standard gameplay functions and asset management
- **Read-Only**: Public access to game state and statistics

### Validation & Safety

- Comprehensive input validation for all user-provided data
- Overflow protection in mathematical operations
- Principal validation to prevent unauthorized transfers
- Experience gain limits to prevent exploitation

## 🧪 Testing

The protocol includes comprehensive test coverage:

```bash
# Run all tests
npm test

# Run specific test file
npm run test -- meta-forge.test.ts

# Check contract syntax
clarinet check
```

### Test Coverage

- Asset minting and transfer functionality
- Avatar creation and progression
- World management and access control
- Leaderboard updates and reward distribution
- Edge cases and error conditions

## 🚀 Deployment

### Testnet Deployment

```bash
# Deploy to testnet
clarinet publish --testnet

# Verify deployment
clarinet console --testnet
```

### Mainnet Deployment

```bash
# Deploy to mainnet
clarinet publish --mainnet

# Initialize protocol
clarinet console --mainnet
```

## 📊 Architecture Diagrams

### System Overview

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Game Assets   │    │     Avatars     │    │   Game Worlds   │
│      NFTs       │    │      NFTs       │    │   Environments  │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 │
                    ┌─────────────────┐
                    │   MetaForge     │
                    │   Protocol      │
                    │   Core Logic    │
                    └─────────────────┘
                                 │
         ┌───────────────────────┼───────────────────────┐
         │                       │                       │
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  Leaderboards   │    │     Rewards     │    │  Experience     │
│   & Rankings    │    │  Distribution   │    │    System       │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## 🤝 Contributing

We welcome contributions to the MetaForge Protocol! Please follow these guidelines:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### Development Guidelines

- Follow Clarity best practices and conventions
- Include comprehensive tests for new features
- Update documentation for API changes
- Ensure all checks pass before submitting PR

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
