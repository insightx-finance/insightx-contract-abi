# insightx-contract-abi

ABI artifacts for all InsightX smart contracts deployed on Mantle Network.

## Overview

InsightX is a decentralized prediction market platform where users can create and participate in prediction markets. This repository contains the Contract Application Binary Interfaces (ABIs) for all smart contracts deployed on the Mantle Network.

## Purpose

This repository provides the ABIs needed for:
- **Backend Integration**: Backend services can use these ABIs to sign and verify contract interactions before broadcasting transactions on-chain
- **Frontend Integration**: Frontend applications can use these ABIs to encode/decode contract interactions
- **Contract Integration**: Other smart contracts can reference these ABIs for cross-contract interactions

## Project Structure

```
ABI/
├── insightx_trade.abi    # Trade contract ABI for market order execution
```

## Contracts

### InsightX Trade Contract
- **Purpose**: Handles market order execution and trade settlement
- **Network**: Mantle Network
- **File**: `ABI/insightx_trade.abi`

## Usage

### JavaScript/TypeScript Example
```javascript
import * as tradeABI from './ABI/insightx_trade.abi.json';
import web3 from 'web3';

const contract = new web3.eth.Contract(tradeABI, contractAddress);
```

### Backend Signature
```javascript
// Sign contract interaction before broadcasting
const encodedData = contract.methods.yourMethod(params).encodeABI();
const signedTx = await web3.eth.accounts.signTransaction(
  {
    to: contractAddress,
    data: encodedData,
    gas: gasLimit
  },
  privateKey
);
```

## Development

When updating contracts, ensure:
1. Update the ABI files in the `ABI/` directory
2. Create a pull request for review
3. Merge to main branch after approval

## License

MIT License - See [LICENSE](./LICENSE) file for details

## Support

For questions or issues, please open an issue in this repository.
