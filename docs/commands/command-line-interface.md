
### --account_create --wallet=`<wallet>`
Insert next deterministic key in to `<wallet>`

### --account_get --key=`<key>`
Get account number for the `<key>`

### --account_key --account=`<account>`
Get the public key for `<account>`

### --clear_send_ids   
Remove all send IDs from the database (dangerous: not intended for production use)

### --confirmation_height_clear
_version 19.0+_ Sets the confirmation heights of all accounts to 0. Optional `--account` to only reset a single account.

### --daemon
Start node daemon. Since version 19.0, network and path will be output, similar to:
```
./nano_node --daemon --network test
Network: test, version: 19.0
Path: /home/USER/NanoTest
```

### --data_path=`<path>` 
Use the supplied `<path>` as the data directory

### --debug_account_count	
Display the number of accounts

### --debug_block_count
Display the number of blocks

### --debug_bootstrap_generate
Generate bootstrap sequence of blocks

### --debug_cemented_block_count
_version 19.0+_ Display the number of cemented blocks (blocks which are under the confirmation height of their accounts)

### --debug_dump_frontier_unchecked_dependents
_version 19.0+_ Dump frontiers which have matching unchecked keys

### --debug_dump_online_weight 
List online weights table and current online_weights value

### --debug_dump_representatives
List representatives and weights

### --debug_mass_activity
Generates fake debug activity

### --debug_output_last_backtrace_dump
Output the stacktrace stored after a node crash.

### --debug_profile_bootstrap
Profile simulated bootstrap process

### --debug_profile_generate
Profile work generation  
Optional `--pow_sleep_interval` in version 19.0+ which sets an amount to sleep (in nanoseconds) between batches of POW calculations when using the CPU.

### --debug_profile_kdf
Profile kdf function

### --debug_profile_sign
Profile signature generation

### --debug_profile_verify
Profile work verification

### --debug_profile_votes
Profile vote verification

### --debug_validate_blocks
_version 19.0+_ Validate blocks in the ledger, includes checks for confirmation height

### --debug_verify_profile
Profile signature verification

### --debug_xorshift_profile
[Disabled] Profile xorshift algorithms

### --debug_opencl --platform=`<platform>` --device=`<device>` --threads=`<threads>`
_[Draft]_ Profile OpenCL work generation for `<device>` on `<platform>` using `<threads>` count. To retrieve available platforms & devices run --diagnostics

### --diagnostics
Run internal diagnostics and validate existing config file (or create default config file if it doesn't exist)

### --help
Print out options

### --key_create
Generates a adhoc random keypair and prints it to stdout

### --key_expand --key=`<key>`
Derive public key and account number from `<key>`

### --network
Allows selection of a different network at runtime. Values `live`, `beta` and `test` supported.

### --online_weight_clear
Clear record history for long term online weight trending

### --peer_clear
Clear cached peers

### --snapshot
Compact database and create snapshot, functions similar to vacuum but does not replace the existing database. Optional `--unchecked_clear`, `--clear_send_ids`, `--online_weight_clear`, `--peer_clear`
Optional `--confirmation_height_clear` in version 19.0+

### --unchecked_clear
Clear unchecked blocks

### --vacuum
Compact database. If data_path is missing, the database in data directory is compacted. Optional `--unchecked_clear`, `--clear_send_ids`, `--online_weight_clear`, `--peer_clear`

### --version    
Prints out version

### --vote_dump
Dump most recent votes from representatives

### --wallet_add_adhoc --wallet=`<wallet>` --key=`<key>`
Insert `<key>` in to `<wallet>`

### --wallet_create --seed=`<seed>` --password=`<password>`
Creates a new wallet with optional `<seed>` and optional `<password>`, and prints the ID. Note the legacy `--key` option can still be used and will function the same as `--seed`.

### --wallet_change_seed --wallet=`<wallet>` --seed=`<seed>`
Changes seed for `<wallet>` to `<seed>`.  Note the legacy `--key` option can still be used and will function the same as `--seed`.

### --wallet_decrypt_unsafe --wallet=`<wallet>` --password=`<password>`
Decrypts `<wallet>` using `<password>`  
**!!THIS WILL PRINT YOUR PRIVATE KEY AND SEED TO STDOUT!!**  
If you didn't set password yet, use --wallet_decrypt_unsafe --wallet=`<wallet>`

### --wallet_destroy --wallet=`<wallet>`
Destroys `<wallet>` and all keys it contains

### --wallet_import  --file=`<filepath>` --wallet=`<wallet>` --password=`<password>`
Imports keys in `<filepath>` using `<password>` in to `<wallet>`. If the provided wallet id does not exist and `--force` is included, a new wallet will be created with the provided wallet id value, and the json file will be imported as is with existing seed and password (instead of a set of private keys without a change of seed).

### --wallet_list
Dumps wallet IDs and public keys

### --wallet_remove --wallet=`<wallet>` --account=`<account>`
Remove `<account>` from `<wallet>`

### --wallet_representative_get --wallet=`<wallet>`
Prints default representative for `<wallet>`

### --wallet_representative_set --wallet=`<wallet>` --account=`<account>`
Set `<account>` as default representative for `<wallet>`

## Launch options
When initially starting the nano_node or nano_wallet as a service the following launch options are available.

NOTE: These options are only for developer use so please understand the impacts before use.

### --block_processor_batch_size
Increase block processor transaction batch write size, default 0 (limited by config block_processor_batch_max_time), 256k for fast_bootstrap

### --block_processor_full_size
Increase block processor allowed blocks queue size before dropping live network packets and holding bootstrap download, default 65536, 1 million for fast_bootstrap

### --block_processor_verification_size
Increase batch signature verification size in block processor, default 0 (limited by config signature_checker_threads), unlimited for fast_bootstrap

### --disable_backup
Turn off automatic wallet backup process

### --disable_lazy_bootstrap
Turn off use of lazy bootstrap

### --disable_legacy_bootstrap
Turn off use of legacy bootstrap

### --disable_wallet_bootstrap
Turn off use of wallet-based bootstrap

### --disable_bootstrap_listener
Turn off listener on the bootstrap network so incoming TCP (bootstrap) connections are rejected. **Note:** this does not impact TCP traffic for the live network.

### --disable_tcp_realtime
_version 19.0+_
Turn off use of TCP live network (TCP for bootstrap will remain available)

### --disable_udp
_version 19.0+_
Turn off use of UDP live network

### --disable_unchecked_cleanup
Prevent periodic cleaning of unchecked table

### --disable_unchecked_drop
Prevent drop of all unchecked entries at node/wallet start

### --fast_bootstrap
Increase bootstrap processor limits to allow more blocks before hitting full state and verify/write more per database call. Also disable deletion of processed unchecked blocks
