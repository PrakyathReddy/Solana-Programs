Solana CLI commands

1. solana-keygen new
   To generate a keypair
2. solana config get
   To see current CLI configuration
3. solana config set --url <RPC_URL>
   By default, Solana CLI is configured to interact with mainnet RPC, that definitely not what we want for development purposes.
   RPC URL for Devnet: https://api.devnet.solana.com
   RPC URL for Testnet: https://api.testnet.solana.com
   RPC URL for Mainnet Beta: https://api.mainnet-beta.solana.com
4. solana config set --keypair <PATH_TO_KEYPAIR>
   To change the location of the default keypair
5. solana address
   Get your public key used by default
6. solana airdrop <amount>
   Request SOL from a faucet
7. solana balance
8. solana transfer <reciepient> <amount>
   Transfer funds from your default account to another account
9. solana-test-validator
   Run localnet nodes
10. solana-keygen new --outfile <PATH_TO_KEYPAIR>
    Create additional keypairs
11. solana rent <amount_of_bytes>
    Calculate rent-exempt-minimum values for a given account data field length
12. solana logs
    To stream transaction logs from the test validator, you may use the following command
13. solana program deploy <PATH_TO_PROGRAM_BINARY>
    Deploy your program
