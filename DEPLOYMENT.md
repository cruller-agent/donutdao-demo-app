# DonutDAO Dashboard - IPFS + ENS Deployment

**Deployment Date:** 2026-02-01  
**Version:** 2.0 - Real-Time Stats Dashboard  
**Status:** ✅ LIVE

## 🌐 Access Points

| Method | URL |
|--------|-----|
| **ENS Subdomain** | `demo.donut-agent.eth` |
| **eth.limo Gateway** | https://demo.donut-agent.eth.limo/ |
| **IPFS Direct** | ipfs://QmNW7suCmF95hRAjUGquEZVrd26u1Y7ocoRkiTQjvc7Bg9 |
| **Public IPFS Gateway** | https://ipfs.io/ipfs/QmNW7suCmF95hRAjUGquEZVrd26u1Y7ocoRkiTQjvc7Bg9/index.html |
| **Cloudflare IPFS** | https://cloudflare-ipfs.com/ipfs/QmNW7suCmF95hRAjUGquEZVrd26u1Y7ocoRkiTQjvc7Bg9/index.html |

## 📦 IPFS Details

| Property | Value |
|----------|-------|
| **CID (v0)** | `QmNW7suCmF95hRAjUGquEZVrd26u1Y7ocoRkiTQjvc7Bg9` |
| **Contenthash** | `0xe30101701220026cf27cc4f7e0a27fe1627aa8c0e079fa7e456287600be6cf8a644d699d3486` |
| **Content Type** | Static HTML page with live contract data |
| **File Size** | ~26.7 KB |

## 🔗 ENS Configuration

| Property | Value |
|----------|-------|
| **Parent Domain** | `donut-agent.eth` |
| **Subdomain** | `demo.donut-agent.eth` |
| **Resolver** | `0x231b0Ee14048e9dCcD1d247744d114a4EB5E8E63` (ENS Public Resolver v3) |
| **Owner** | `0x608044ffa0ecfdf91a4e235304685559158a3a72` |
| **Network** | Ethereum Mainnet |

### Namehashes
```
donut-agent.eth:      0x4db8f08227319829175132ee5559889c799be524971abe535dc2990364e7d311
demo.donut-agent.eth: 0x91be10d03e9fcd00711780a0c6efb4ff282cb80d5f59bb860997357f761835be
```

## 💰 Transaction History

### Transaction 1: Update Contenthash (v2.0)
- **Hash:** `0x92d4b2c981646176e87a246bc882b5ccb48b7fcba7b0320936ec7b3b15e3f196`
- **Etherscan:** https://etherscan.io/tx/0x92d4b2c981646176e87a246bc882b5ccb48b7fcba7b0320936ec7b3b15e3f196
- **Contract:** ENS Public Resolver (`0x231b0Ee14048e9dCcD1d247744d114a4EB5E8E63`)
- **Function:** `setContenthash(bytes32 node, bytes calldata hash)`
- **Date:** 2026-02-01

### Previous Transactions (v1.0)
- **Create Subdomain:** `0x6a9b6f9ad7f6cefe6d41023ec66b341952ad9cb8cb2d2ceef736046863b5859a`
- **Set Initial Contenthash:** `0x1a96956609548e82d108cf1d0b3ce21c4a2c01bb3cf7d6917ff515cb0a2c5618`
- **Old CID:** `QmUMpizYGE9GBdsLVz8WNpeHvkCi8KPrvibMPJjz8q5omk`

## 📊 Dashboard Features (v2.0)

The new dashboard displays **REAL** DonutDAO stats from Base mainnet:

### Live Contract Data
1. **DONUT Total Supply** - Fetched from ERC20 totalSupply()
2. **gDONUT Total Staked** - DONUT locked in governance token
3. **Total Voting Power** - gDONUT supply (governance weight)
4. **Staking Ratio** - % of DONUT supply that's staked
5. **Mining Rate** - Emissions per second (if available)
6. **ETH Price** - From Coingecko API

### Contract Addresses (Base Mainnet)
```
DONUT:         0xAE4a37d554C6D6F3E398546d8566B25052e0169C
gDONUT:        0xC78B6e362cB0f48b59E573dfe7C99d92153a16d3
Voter:         0x9C5Cf3246d7142cdAeBBD5f653d95ACB73DdabA6
RevenueRouter: 0x4799CBe9782265C0633d24c7311dD029090dED33
Miner:         0xF69614F4Ee8D4D3879dd53d5A039eB3114C794F6
DAO:           0x690C2e187c8254a887B35C0B4477ce6787F92855
```

### Design System
- **GlazeCorp Design** by @Heesho
- Dark theme with pink accents (donut-500: #ec4899)
- Inter font for UI, JetBrains Mono for numbers
- Responsive grid layout
- Hover effects and smooth animations

## 🛠️ Technical Implementation

### Stack
- Pure HTML/CSS/JS (no build step required)
- Ethers.js v6.9.0 (CDN)
- Base RPC: https://mainnet.base.org
- Google Fonts (Inter, JetBrains Mono)
- Coingecko API for ETH price

### Data Flow
1. Page loads → ethers.js initializes
2. Create JsonRpcProvider for Base
3. Parallel fetch: DONUT supply, gDONUT stats, mining rate
4. Format and display with commas
5. Refresh button for manual updates

## 🔄 Update Process

To update the app:
1. Modify `dist/index.html`
2. Add to IPFS: `ipfs add -r dist/`
3. Pin: `ipfs pin add <CID>`
4. Generate contenthash: `node update-contenthash.mjs prepare <CID>`
5. Submit via Bankr

## 📝 Notes

- **Gateway Propagation:** Changes may take a few minutes to propagate through IPFS gateways
- **ENS Resolution:** Updates are near-instant once the tx confirms
- **RPC Rate Limits:** Using public Base RPC, may need to add fallbacks for heavy usage
- **Client-Side:** All data fetching happens in the browser

## 📚 References

- [ENS Documentation](https://docs.ens.domains/)
- [IPFS Documentation](https://docs.ipfs.io/)
- [eth.limo Gateway](https://eth.limo/)
- [Ethers.js v6](https://docs.ethers.org/v6/)
- [Base Network](https://docs.base.org/)
