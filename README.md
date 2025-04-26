
# Auto Daily Plaza Finance Bot

Register : https://testnet.plaza.finance/rewards/RdPDMkEuBR84

This script automates interactions with Plaza Finance's faucet, ensuring unlimited spending for the wstETH token, swapping 80% of wstETH to bondETH, 10% to leverage tokens, creating Bond and Leverage tokens, and redeeming a portion of those tokens. It processes multiple wallets in a cycle, with a delay of 6 hours after all wallets are processed.

## Features
- Claims faucet tokens.
- Swaps 80% of wstETH to bondETH and 10% to Leverage tokens.
- Creates Bond and Leverage tokens.
- Redeems 50% of Bond and Leverage tokens' balance.
- Claims USDC coupon.
- Supports proxy usage for wallet interaction.
- Repeats the entire cycle every 6 hours.

## Requirements
- Node.js
- `web3`, `axios`, `chalk`, `fs`, `https-proxy-agent`

Install the required Node.js modules:

```bash
npm install web3@1.8.0 axios chalk@2 fs https-proxy-agent
```

## Setup

1. Add your private keys to the `private_keys.txt` file, with one private key per line. Ensure each key is exactly 64 characters (without 0x).
2. If you want to use proxies, add your proxy IPs to the `proxies.txt` file. The number of proxies should match the number of private keys.

### Proxy Format
Each line in the `proxies.txt` file should contain a proxy in the following format:

```
<IP_ADDRESS>:<PORT>
```

For example:

```
192.168.1.100:8080
123.456.789.101:3128
```

### Files:
- `private_keys.txt`: Contains the private keys of your wallets.
- `proxies.txt` (Optional): Contains the proxies for wallet interaction (one per line).

### Script Structure:

1. **Claim Faucet**: Claims tokens from Plaza Finance for each wallet.
2. **Swap wstETH**: Swaps 80% of wstETH to bondETH and 10% to leverage tokens.
3. **Unlimited Spending for wstETH**: Ensures unlimited allowance for the wstETH token.
4. **Create Bond and Leverage Tokens**: Creates Bond and Leverage tokens with random deposit amounts.
5. **Redeem Tokens**: Redeems 50% of the balance of Bond and Leverage tokens.
6. **Claim Coupon**: Claims a USDC coupon after completing the cycle.
7. **Delay and Retry**: Retries failed transactions with a 30-second delay and moves to the next wallet.
8. **Repeat**: The entire cycle repeats every 6 hours after processing all wallets.

## Usage

Create a screen:

```bash
screen -S plaza
```

Run the script with Node.js:

```bash
node index.js
```

Or if you prefer using proxies, run:

```bash
node index-proxy.js
```

The script will run once immediately and will repeat every 6 hours.

- To minmize the screen, press `Ctrl+A+D`
- To return the screen, enter command: `screen -r plaza`
- To stop and kill the bot, press `CTRL+C` inside the screen & run this command: `screen -XS plaza quit`


## Logs

The script logs detailed information using `chalk` for colorful output, including:
- Faucet claim status
- Token allowance status
- Token swap status (wstETH to bondETH and lev)
- Bond and Leverage token creation
- Token redemption
- Coupon claim

All successful transactions and errors are printed in the console with the appropriate formatting.

## Notes

- Ensure your private keys are correct, as invalid keys will result in errors.
- If using proxies, make sure the number of proxies in `proxies.txt` matches the number of private keys in `private_keys.txt`.

[source: forked from main Repo](https://github.com/ganjsmoke/plaza-finance-bot)
