# GitHub README

```markdown
# Token Snapshot System

A Clarity smart contract for creating and managing token snapshots on the Stacks blockchain. This system enables recording token balances at specific block heights for SIP-010 tokens.

## Overview

The Token Snapshot System allows users to:
- Create snapshots of token balances at specific block heights
- Store and retrieve snapshot metadata
- Track multiple users and their balances across different snapshots
- Manage up to 100 users per snapshot

## Features

- **Snapshot Creation**: Record token balances at the current block height
- **Balance Tracking**: Store balance data for each user in a snapshot
- **Read-Only Functions**: Query snapshot information without state changes
- **Admin Control**: Access control through admin principal management
- **Error Handling**: Comprehensive error codes for validation

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd token-snapshot
```

2. Deploy the contract to Stacks testnet or mainnet using Clarinet:
```bash
clarinet contract deploy
```

## Usage

### Create a Snapshot
```clarity
(contract-call? .token-snapshot take-snapshot)
```

### Get Total Snapshots
```clarity
(contract-call? .token-snapshot get-total-snapshots)
```

## Data Structures

- **snapshots**: Maps snapshot ID to block height
- **snapshot-balances**: Maps (snapshot-id, user) to balance amount

## Constants

- `MAX_USERS`: Maximum users per snapshot (100)

## Error Codes

| Code | Error |
|------|-------|
| 100 | ERR_ALREADY_SNAPSHOTTED |
| 101 | ERR_NOT_FOUND |
| 102 | ERR_UNAUTHORIZED |
| 103 | ERR_TOO_MANY_USERS |
