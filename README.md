# VoidChain API Documentation

## Table of Contents

### 1. [Overview](docs/01_Overview.md)
Introduction to VoidChain technology and architecture.

### 2. [Setup Instructions](docs/02_Setup_Instructions.md)
Installation and configuration guide for the Edge Trust Machine.

### 3. [Public Queries](docs/03_Public_Queries.md)
Public information query endpoints:
- Get Edge Trust Machine ID
- Entry Information Query
- Node Query
- Query Block List
- Block Information Query
- Block Transaction Query
- Address Query
- Rewards Query
- Account Check
- Token List Interface
- Transaction Result Query

### 4. [Login and Registration](docs/04_Login_Registration.md)
User authentication and account management:
- Session ID
- Register
- Login
- Import/Export Mnemonic
- Import/Export Account Password
- Import/Export Keystore
- Change Password
- Logout

### 5. [Mainnet Node Management](docs/05_Mainnet_Node_Management.md)
Node administration interfaces:
- Configure Management Password
- Exit Vacuum Network

### 6. [Content Information Management](docs/06_Content_Information_Management.md)
Content and address management:
- Create Address
- Update Address Content

### 7. [Query and Test Interface](docs/07_Query_Test_Interface.md)
Transaction testing and query operations.

### 8. [Transaction Interface](docs/08_Transaction_Interface.md)
Transaction execution endpoints:
- Transfer
- Distribute Transactions (Batch Transfer)
- Deploy Contract
- Execute Contract
- Contract Function Code Query

### 9. [Wallet Lock Interface](docs/09_Wallet_Lock_Interface.md)
Wallet locking mechanisms:
- Lock Wallet
- Query Lock Information
- Unlock

### 10. [Proposal Management](docs/10_Proposal_Management.md)
Governance and proposal system:
- TRC100 Address Query
- Query Proposal Permission
- Submit Proposal
- Vote
- Execute Proposal
- Query Proposal
- Delete Proposal
- Query Vote Information

### 11. [Static Metaspace](docs/11_Static_Metaspace.md)
Metaspace management interfaces:
- Apply for Static Metaspace
- Get Metaspace Genesis Block
- Confirm Metaspace Validity
- Dynamic Metaspace Query
- Deploy TRC100 Base Contract
- Configure Incentive Token
- Incentive Contract Query
- Node Management (Add, Batch Add, Delete, Batch Delete, Query)

### 12. [Cross-chain Circulation](docs/12_Cross_Chain_Circulation.md)
Asset transfer between metaspaces:
- Cross-chain Transfer Out
- Cross-chain Transfer In

### 13. [Cross-chain Metaspace Interface](docs/13_Cross_Chain_Metaspace.md)
- Login VoidChain to Get Transaction Voucher
- Login Third-party Exchange
- Create Public Chain Private Address
- Query Public Chain Private Address
- Import/Export Public Chain Mnemonic
- Deploy Public Chain Contract
- Deploy Public Chain Token
- Public Chain Information Query
- Public Chain Token Details Query
- Launch and Activate Public Chain
- Query All Chain Information
- Robot Address Query
- Import/Export Public Chain Assets
- Import/Export Asset Status Query
- Broker Transaction
- Query Cross-chain Metaspace Assets
- Query Other Chain Assets

### 14. [Transaction Monitoring](docs/14_Transaction_Monitoring.md)
Blockchain event monitoring:
- Set Monitoring
- Query Transaction Actions
- Blockchain Traversal Interface

### 15. [Other Utilities](docs/15_Other_Utilities.md)
Utility functions:
- Get Content MD5
- Query Machine Code

### 16. [Keywords](docs/16_Keywords.md)
Complete keyword reference table.

### 17. [Error Codes](docs/17_Error_Codes.md)
Error code reference and notes.

---

## API Communication

All API endpoints use JSON-RPC 3.0 protocol.

**Base URL:** `http://127.0.0.1:8080` (local machine)

**Request Format:**
```json
{
  "jsonrpc": "3.0",
  "method": "method_name",
  "params": ["param1", "param2"],
  "id": "session_id"
}
```

**Response Format:**
```json
{
  "jsonrpc": "3.0",
  "id": "session_id",
  "result": {
    "ret": "0",
    "err": "",
    "content": {}
  }
}
```

## Important Notes

1. **Token Decimals:** VoidChain platform tokens use 9 decimal places. Add 9 zeros when transferring tokens.

2. **Daily Free Gas:** Each account receives approximately 10 free gas operations daily, but must actively claim them.

3. **Gas Fee Priority:** Gas fees are deducted from the free pool first. When exhausted, 1 platform coin is automatically purchased for approximately 10 operations worth of gas.

4. **Transaction Confirmation:** Any operation returning a `txhash` field requires periodic status queries until completion.

## Getting Started

1. Download and install the Edge Trust Machine (see [Setup Instructions](docs/02_Setup_Instructions.md))
2. Configure `chain.conf` with your connection parameters
3. Start the trust machine service
4. Obtain a session ID (see [Login and Registration](docs/04_Login_Registration.md))
5. Begin making API calls

## Support

For questions and support, please refer to the specific documentation sections above.
