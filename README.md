
# Auto Daily Plaza Finance Bot

Register : https://testnet.plaza.finance/rewards/a0MndhdkWSCb

This script automates interactions with Plaza Finance's faucet, ensuring unlimited spending for the wstETH token, creating Bond and Leverage tokens, and redeeming a portion of those tokens. It processes multiple wallets in a cycle, with a delay of 6 hours after all wallets are processed.

## Features
- Claims faucet tokens.
- Sets unlimited allowance for wstETH token.
- Creates Bond and Leverage tokens.
- Redeems 50% of Bond and Leverage tokens' balance.
- Repeats the entire cycle every 6 hours.

## Requirements
- Node.js
- `web3`, `axios`, `chalk`, `fs`

Install the required Node.js modules:

```bash
npm install web3@1.8.0 axios chalk@2 fs
```

## Setup

1. Add your private keys to the `private_keys.txt` file, with one private key per line. Ensure each key is exactly 64 characters (without 0x).
   

### Files:
- `private_keys.txt`: Contains the private keys of your wallets.

### Script Structure:

1. **Claim Faucet**: Claims tokens from Plaza Finance for each wallet.
2. **Unlimited Spending for wstETH**: Ensures unlimited allowance for the wstETH token.
3. **Create Bond and Leverage Tokens**: Creates Bond and Leverage tokens with random deposit amounts.
4. **Redeem Tokens**: Redeems 50% of the balance of Bond and Leverage tokens.
5. **Delay and Retry**: Retries failed transactions with a 30-second delay and moves to the next wallet.
6. **Repeat**: The entire cycle repeats every 6 hours after processing all wallets.

## Usage

Run the script with Node.js:

```bash
node index.js
```

The script will run once immediately and will repeat every 6 hours.

## Logs

The script logs detailed information using `chalk` for colorful output, including:
- Faucet claim status
- Token allowance status
- Bond and Leverage token creation
- Token redemption

All successful transactions and errors are printed in the console with the appropriate formatting.

## Notes

- Ensure your private keys are correct, as invalid keys will result in errors.
