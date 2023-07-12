--- Solana CLI commands

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

--- Setting up a project
cargo init
The minimum necessary set of files to write a quality on-chain program in Solana is to have the following files:

src/entrypoint.rs - responsible for the entry point into the program;
src/error.rs - defines error types;
src/instructions.rs - defines instructions for the program work and their serialization and deserialization;
src/lib.rs - defines all modules in the project;
src/processor.rs - responsible for the logic executed by the program;
src/state.rs - handles the objects' state and their serialization and deserialization.

--- If this module hierarchy is in place, the workflow will look as follows:

1. somebody calls the entrypoint with specific arguments;
2. the entrypoint passes arguments to the processor;
3. the processor decodes the instructions received as an argument from the entrypoint;
4. some action takes place according to the decoded data received;
5. if necessary, uses state.rs to manipulate the account state passed through the entrypoint;
6. in case of an error during an action, it uses custom errors from error.rs.

For further projects, you may use a template repo and modify it for your needs.

https://github.com/siexp/solana-program-library/tree/master

--- To Deploy Programs

To run a localnet for testing
solana-test-validator

Open a new terminal, and configure the CLI toolkit to work with the local cluster by default:
solana config set --url http://127.0.0.1:8899

program logs are output in a separate termimal using the following command:
solana logs

To Build the program
cargo build-bpf

After the build, we can deploy the .so program to the network with the command
solana program deploy
Returns the Program ID of the deployed program

To deploy to a specific program id, add a flag:
solana program deploy --program-id
