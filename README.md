# Decentralized Freelance Platform

A blockchain-based freelance marketplace built on Solana, enabling trustless job postings, escrow payments, and dispute resolution through smart contracts.

---

## 📸 Screenshots

<!-- Add screenshots here -->
### Homepage
<img width="1467" height="744" alt="2025-12-14_12-13-05" src="https://github.com/user-attachments/assets/ec13e5b8-9757-4521-a167-9e9f2549e15e" />

### Dashboard
<img width="1462" height="831" alt="2025-12-14_12-15-27" src="https://github.com/user-attachments/assets/f1dcdf00-89b9-411f-a53e-d172f47d23bd" />
<img width="1469" height="830" alt="2025-12-14_12-15-56" src="https://github.com/user-attachments/assets/a20ff4a2-c298-4191-ad29-5a63c7d71814" />
<img width="1160" height="818" alt="2025-12-14_12-18-00" src="https://github.com/user-attachments/assets/c248fe15-6285-407e-93a2-9216a800f115" />


### Job Listing
<img width="1386" height="828" alt="2025-12-14_12-16-30" src="https://github.com/user-attachments/assets/2136b250-bb68-48ca-9372-32b504acf456" />

<img width="1139" height="767" alt="2025-12-14_12-16-51" src="https://github.com/user-attachments/assets/73ebb074-8fd6-4b7c-9013-df6461118768" />




### Job Creation
<img width="1145" height="810" alt="2025-12-14_12-18-56" src="https://github.com/user-attachments/assets/6e3c684e-d803-4bed-a1eb-e63da9204dd8" />


### Proposal Management
<img width="1195" height="817" alt="2025-12-14_12-18-32" src="https://github.com/user-attachments/assets/ba9151ae-06de-46e2-a05e-97d76c4dca30" />

### Dispute Resolution
<img width="1186" height="794" alt="2025-12-14_12-19-18" src="https://github.com/user-attachments/assets/4addea2a-c4de-41e5-ac44-66b8ce0a8f48" />
<img width="1218" height="823" alt="2025-12-14_12-19-53" src="https://github.com/user-attachments/assets/07132d95-2b55-4ea4-8820-97203e1d5e2b" />



---

## 🌟 Features

### Core Functionality
- **Decentralized Job Marketplace**: Post and browse freelance jobs on the blockchain
- **Smart Contract Escrow**: Secure payments held in escrow until work completion
- **Proposal System**: Freelancers can submit proposals with custom rates and timelines
- **Dispute Resolution**: Built-in dispute system for job conflicts
- **Wallet Integration**: Seamless connection with Solana wallets (Phantom, Solflare, etc.)
- **User Profiles**: On-chain user registration and profile management

### Security Features
- **Trustless Payments**: Funds locked in smart contract escrow
- **Program-Derived Addresses (PDAs)**: Secure account management
- **Job Counter System**: Unique job IDs generated on-chain
- **Multi-stage Job Lifecycle**: Open → Assigned → Submitted → Completed → Disputed

### User Roles
1. **Clients**: Create jobs, review proposals, accept work, and release payments
2. **Freelancers**: Browse jobs, submit proposals, deliver work, and receive payments

---

## 🏗️ Architecture

### Frontend (Next.js)
- **Framework**: Next.js 16 with React 19
- **Styling**: TailwindCSS with custom components
- **Wallet Integration**: Solana Wallet Adapter
- **UI Components**: Radix UI primitives
- **Charts & Visualizations**: Recharts
- **Animations**: Framer Motion
- **State Management**: React Context (UserProvider)

### Backend (Solana Program)
- **Framework**: Anchor 0.32.1
- **Language**: Rust
- **Network**: Solana Devnet/Localnet
- **Program ID**: `TCmSPaJcRMbtzJbkGcGrJtcsjzNRpAwFRNxhqTC9BZZ`

---

## 📁 Project Structure

```
freelanceNew/
├── my-app/                    # Next.js frontend application
│   ├── src/
│   │   ├── (anchor)/         # Solana program integration
│   │   │   ├── setup.ts      # Program initialization & PDAs
│   │   │   ├── actions/      # Blockchain actions
│   │   │   └── idl.json      # Program interface definition
│   │   ├── (providers)/      # React context providers
│   │   ├── (types)/          # TypeScript type definitions
│   │   ├── app/              # Next.js app router pages
│   │   │   ├── dashboard/    # User dashboard
│   │   │   ├── jobs/         # Job browsing & details
│   │   │   ├── manage-jobs/  # Job creation & management
│   │   │   ├── proposals/    # Proposal management
│   │   │   ├── submit-work/  # Work submission
│   │   │   └── disputes/     # Dispute handling
│   │   └── lib/              # Utility functions
│   └── package.json
│
└── backend/                   # Solana smart contract
    ├── programs/
    │   └── backend/          # Anchor program source
    ├── tests/                # Program tests
    ├── Anchor.toml           # Anchor configuration
    └── Cargo.toml            # Rust dependencies
```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js**: v20 or higher
- **Rust**: Latest stable version
- **Solana CLI**: v1.18 or higher
- **Anchor CLI**: v0.32.1
- **Yarn**: Package manager

### Installation

#### 1. Clone the Repository
```bash
git clone <repository-url>
cd freelanceNew
```

#### 2. Install Dependencies

**Frontend:**
```bash
cd my-app
npm install
```

**Backend:**
```bash
cd backend
yarn install
```

#### 3. Configure Solana Wallet
```bash
# Create a new wallet (or use existing)
solana-keygen new --outfile ~/.config/solana/id.json

# Set cluster to devnet
solana config set --url devnet

# Airdrop SOL for testing
solana airdrop 2
```

#### 4. Build and Deploy Smart Contract

```bash
cd backend

# Build the program
anchor build

# Deploy to localnet (optional)
anchor localnet
# In another terminal:
anchor deploy

# Or deploy to devnet
anchor deploy --provider.cluster devnet
```

#### 5. Update Program ID

After deployment, update the program ID in:
- `backend/Anchor.toml`
- `my-app/src/(anchor)/idl.json`
- `my-app/src/(anchor)/setup.ts`

#### 6. Set Environment Variables

Create `.env.local` in the `my-app` directory:

```env
NEXT_PUBLIC_SOLANA_RPC_URL=https://api.devnet.solana.com
# Or for localnet:
# NEXT_PUBLIC_SOLANA_RPC_URL=http://127.0.0.1:8899
```

#### 7. Run the Frontend

```bash
cd my-app
npm run dev
```

Visit `http://localhost:3000` in your browser.

---

## 🎯 Usage Guide

### For Clients

1. **Connect Wallet**: Click "Connect Wallet" and select your Solana wallet
2. **Register**: Complete user registration (one-time, on-chain)
3. **Create Job**: Navigate to "Manage Jobs" → "New Job"
   - Fill in job details (title, description, budget, deadline)
   - Lock funds in escrow
4. **Review Proposals**: View freelancer proposals on your job
5. **Accept Proposal**: Select the best proposal to assign the job
6. **Review Work**: Check submitted work
7. **Release Payment**: Approve work and release escrowed funds

### For Freelancers

1. **Connect Wallet**: Connect your Solana wallet
2. **Register**: Complete user registration
3. **Browse Jobs**: Explore available jobs on the dashboard
4. **Submit Proposal**: Apply to jobs with your rate and timeline
5. **Deliver Work**: Submit completed work with proof/links
6. **Receive Payment**: Get paid when client approves your work

### Dispute Handling

If there's a disagreement:
1. Client or freelancer can raise a dispute
2. Provide evidence and description
3. Funds remain locked until resolution
4. (Future: Implement DAO-based dispute resolution)

---

## 🔑 Key Components

### Smart Contract Accounts

1. **User Account**
   - Stores user registration data
   - PDA: `["user", authority]`

2. **Job Account**
   - Contains job details and status
   - PDA: `["job", job_id]`

3. **Job Counter**
   - Generates unique job IDs
   - PDA: `["job_counter"]`

4. **Escrow Account**
   - Holds locked SOL for job payment
   - PDA: `["escrow", job_account]`

### Job Lifecycle
<img width="608" height="292" alt="image" src="https://github.com/user-attachments/assets/2f6d51f2-a58b-4d55-88e9-71453146ef15" />

```
┌─────────┐     ┌──────────┐     ┌───────────┐     ┌───────────┐
│  Open   │────▶│ Assigned │────▶│ Submitted │────▶│ Completed │
└─────────┘     └──────────┘     └───────────┘     └───────────┘
                      │                                   │
                      │                                   │
                      ▼                                   ▼
                 ┌──────────┐                      ┌──────────┐
                 │ Disputed │                      │ Disputed │
                 └──────────┘                      └──────────┘
```

### Frontend Pages

- **Dashboard**: Overview of jobs, proposals, and user stats
- **Jobs**: Browse and search available jobs
- **Job Details**: View full job information and submit proposals
- **Manage Jobs**: Create, edit, and manage your posted jobs
- **Proposals**: Track your submitted proposals
- **Submit Work**: Deliver completed work
- **Disputes**: Handle job conflicts

---

## 🛠️ Technology Stack

### Frontend
| Technology | Purpose |
|-----------|---------|
| Next.js 16 | React framework with app router |
| React 19 | UI library |
| TypeScript 5 | Type safety |
| TailwindCSS | Styling |
| Radix UI | Accessible components |
| Solana Wallet Adapter | Wallet integration |
| Framer Motion | Animations |
| Recharts | Data visualization |
| Lucide React | Icons |

### Backend
| Technology | Purpose |
|-----------|---------|
| Anchor 0.32.1 | Solana development framework |
| Rust | Smart contract language |
| Solana Web3.js | Client library |
| BN.js | Big number handling |

---

## 📊 Database Schema (On-Chain)

### User Account
```rust
pub struct User {
    pub authority: Pubkey,
    pub name: String,
    pub created_at: i64,
    // Additional user fields
}
```

### Job Account
```rust
pub struct Job {
    pub job_id: u64,
    pub client: Pubkey,
    pub title: String,
    pub description: String,
    pub budget: u64,
    pub deadline: i64,
    pub status: JobStatus,
    pub assigned_freelancer: Option<Pubkey>,
    pub created_at: i64,
    // Additional job fields
}

pub enum JobStatus {
    Open,
    Assigned,
    Submitted,
    Completed,
    Disputed,
}
```

---

## 🧪 Testing

### Run Smart Contract Tests
```bash
cd backend
anchor test
```

### Test Locally
```bash
# Start local validator
solana-test-validator

# In another terminal, deploy
cd backend
anchor deploy

# Run tests
anchor test --skip-local-validator
```

---

## 🚢 Deployment

### Deploy to Devnet
```bash
cd backend
anchor build
anchor deploy --provider.cluster devnet
```

### Deploy Frontend
```bash
cd my-app
npm run build
npm start
```

Or deploy to Vercel/Netlify:
```bash
vercel deploy
# or
netlify deploy
```

---

## 🔐 Security Considerations

### Smart Contract Security
- ✅ **PDAs (Program-Derived Addresses)**: Ensure secure, predictable account ownership without private key management
- ✅ **Escrow System**: Funds are cryptographically locked in the program until explicit conditions are met, preventing unauthorized transfers
- ✅ **On-Chain Authorization Checks**: All transactions verify user permissions before execution
- ✅ **Wallet Signature Verification**: Every action requires cryptographic proof of authorization from the wallet owner

### Best Practices
- ⚠️ **Always verify transaction details** before signing - review the amount, recipient, and operation type
- ⚠️ **Never share your private key** or seed phrase with anyone, including support staff
- ⚠️ **Use devnet for testing**: Test all workflows thoroughly on devnet before using mainnet with real funds
- ⚠️ **Enable 2FA on wallet extensions**: Use additional security features provided by your wallet
- ⚠️ **Verify program deployment**: Confirm the deployed program matches the expected program ID before transacting

### Environment-Specific Recommendations
| Environment | Recommendation | Use Case |
|-----------|-----------------|----------|
| **Devnet** | Use for testing and development | Free testing, no real value |
| **Mainnet** | Use only with verified programs | Production with real SOL |
| **Localnet** | Use for local development | Isolated testing environment |

### Security Audit
- This platform has not undergone a formal security audit. Use at your own risk
- Review the smart contract code before deploying to mainnet
- Test extensively on devnet with small amounts first

---

## 🐛 Troubleshooting

### Common Issues

**1. Wallet Connection Fails**
- **Solution**: 
  - Ensure your wallet extension is installed and enabled (Phantom, Solflare, etc.)
  - Verify the network in your wallet matches the application network (devnet/mainnet)
  - Try clearing browser cache: `Ctrl+Shift+Delete` and refresh the page
  - Temporarily disable browser extensions that may interfere (ad blockers, privacy tools)
  - Try a different browser to isolate the issue

**2. Transaction Fails with "Insufficient Funds"**
- **Cause**: Not enough SOL for transaction fees or the operation
- **Solution**:
  - Check your SOL balance in the wallet (aim for at least 0.1 SOL)
  - Request an airdrop: `solana airdrop 2 --url devnet`
  - Ensure you have funds in the correct network (devnet/mainnet)
  - Note that escrow operations require additional SOL for account creation

**3. User Account Not Found**
- **Cause**: User hasn't registered on-chain yet
- **Solution**:
  - Navigate to Dashboard and complete the registration process
  - Wait for the registration transaction to confirm (usually 10-30 seconds)
  - Refresh the page after successful registration
  - Check the transaction hash on Solana Explorer for confirmation

**4. Build Errors**
- **Solutions**:
  - Clear and reinstall dependencies: `rm -rf node_modules && npm install`
  - Clear Next.js cache: `rm -rf .next && npm run dev`
  - Verify Node.js version: `node --version` (v20+ required)
  - Check for TypeScript errors: `npm run type-check`
  - Try updating packages: `npm update`

**5. Program Deployment Issues**
- **Solutions**:
  - Verify Solana CLI is installed: `solana --version`
  - Check CLI configuration: `solana config get`
  - Ensure wallet has sufficient SOL: `solana balance`
  - Try increasing compute budget if program is too large
  - For Anchor: verify `Anchor.toml` and `Cargo.toml` configurations
  - Clear Anchor cache: `anchor clean` then `anchor build`

**6. RPC Connection Errors**
- **Cause**: Issues connecting to Solana network
- **Solution**:
  - Verify RPC endpoint is correct in environment variables
  - Try alternative RPC endpoints if main one is down
  - Check internet connection stability
  - For devnet issues, try: `https://api.devnet.solana.com`
  - Rate limiting: If making many requests, implement exponential backoff

**7. Job Creation Transaction Timeout**
- **Cause**: Network congestion or slow RPC node
- **Solution**:
  - Wait a moment and retry the transaction
  - Check Solana network status: `solana validators --url devnet`
  - Try during off-peak hours
  - Verify escrow amount is reasonable (not exceptionally high)

**8. Frontend Won't Load or Shows Blank Page**
- **Solutions**:
  - Check browser console for errors: `F12` → Console tab
  - Verify environment variables in `.env.local` are set correctly
  - Ensure the backend/program is deployed and accessible
  - Clear browser cache and cookies
  - Try incognito/private browsing mode
  - Verify Next.js server is running: check terminal for `Ready in X.XXs`

### Debug Mode

To enable verbose logging:
1. Set environment variable: `DEBUG=*`
2. Check browser console (F12) for detailed error messages
3. Monitor network requests in DevTools → Network tab
4. Check terminal logs for server-side errors

### Still Having Issues?

- Check the [GitHub Issues](https://github.com/your-repo/issues) for similar problems
- Review Solana Explorer for transaction details: `https://explorer.solana.com/?cluster=devnet`
- Consult the [Anchor documentation](https://docs.rs/anchor-lang)
- Contact the team via GitHub or LinkedIn (see Team section)

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---


## 👥 Team

- Nikhil Dhakad: https://github.com/nikhil-dtech , https://www.linkedin.com/in/nikhil-dhakad-46304b285/
- Nikhil Goyal: https://github.com/NikhilG-14 ,  https://www.linkedin.com/in/nikhil-goyal-baa177325/
- vansh Kabra: https://github.com/VANSH3104 , https://www.linkedin.com/in/vansh-kabra-0a110327b/

---

## 📞 Contact

For questions or support, please:
- Open an issue on GitHub
- Contact on linkedin or github

---

## 🙏 Acknowledgments

- Solana Foundation for the blockchain infrastructure
- Anchor Framework team for development tools
- Radix UI for accessible component primitives
- The open-source community

---

**Built with ❤️ on Solana**
