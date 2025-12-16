# SuInsure

**SuInsure** is a decentralized parametric insurance platform built on the Sui blockchain. Our goal is simple: to replace slow, manual insurance claims with instant, automated payouts. By using smart contracts instead of bureaucratic processes, we offer financial protection that is transparent, fast, and accessible to everyone.

## How It Works
SuInsure operates on a "parametric" model, which means payouts are triggered by data, not opinions.
* **Automatic Triggers:** Our smart contracts monitor real-world data via oracles (like local weather reports for farmers or economic stats for businesses).
* **Instant Payouts:** As soon as a specific threshold is crossed—for example, if rainfall drops below a certain level—compensation is sent directly to the insured user's wallet.
* **No Paperwork:** Because the trigger is mathematical and automatic, there is no need to file a claim or wait months for approval. This is critical for businesses with low cash reserves or farmers facing immediate climate risks.

## Key Features

* **NFT Policy Certificates:** When you purchase coverage, you instantly receive an NFT. This serves as your digital policy—a traceable, tamper-proof proof of insurance that lives on-chain.
* **Working Capital (DeFi):** Unlike traditional insurance where premiums often sit idle, SuInsure actively manages pooled funds using DeFi protocols. This generates yield like a mutual fund, maximizing returns and ensuring the stability of the risk pool.
* **Built for Speed:** Leveraging the Sui blockchain’s parallel execution, our payouts happen in seconds with predictable fees, ensuring you get funds exactly when you need them.
* **Universal Access with Slush:** We built SuInsure to help the unbanked and those without traditional financial access. Through our integration with **Slush**, users can connect easily using standard crypto wallets or simple social logins (zkLogin), removing the barriers of traditional banking.




# Main functions 

## Modifying package live
```
sui client call --package <package_id> --module transfer_nft --function claim_publisher --args <upgrade_cap_object_id>

```


## Transferpolicy
```
sui client call --package 0x2 --module transfer_policy --function default --type-args 0xa38696917fd033a9fba4b7c0904e81e49bf1dbccab9f7a5e8b48e8141c15a3d1::transfer_nft::TransferRight --args <publisher_object_id>


```

## Burning the NFT for reimbursement 

```
- Simply call the function with the two IDs:
    - nft_id: ID of the TransferRight (will be consumed/burnt)
    - treasury_id: ID of the Treasury object (shared)
      
      
sui client call \
  --package <package_id> \
  --module transfer_nft \
  --function execute_and_burn_transfer \
  --args <transfer_right_id> <treasury_id> \
  --gas-budget 10000000
```

## Supplying the Treasury
```
--package  package \
  --module transfer_nft \
  --function fund_treasury \
  --args treasury_id \
         deposit_coin_id \
  --gas-budget 10000000
   
```


## Creating the NFT
```
sui client call \
  --package <package_id> \
  --module transfer_nft \
  --function mint_transfer_right \
  --args <ton_adresse> \
  --gas-budget 2000000
```


# Creating the NFT associated to the kiosk 
```
sui client call --package <new_package_id> --module transfer_nft --function mint_transfer_right_for_kiosk --args <kiosk_object_id> <kiosk_owner_cap_id> <recipient_address>

```







# Initialisation contract 
```
──────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ Transaction Data                                                                                             │
├──────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ Sender: 0x21a9877e440fca354aee0f8d1ad0f19bda846cedc66e420bcaaec47d2624bd85                                   │
│ Gas Owner: 0x21a9877e440fca354aee0f8d1ad0f19bda846cedc66e420bcaaec47d2624bd85                                │
│ Gas Budget: 25848800 MIST                                                                                    │
│ Gas Price: 1000 MIST                                                                                         │
│ Gas Payment:                                                                                                 │
│  ┌──                                                                                                         │
│  │ ID: 0x169fa038f40022143f16ac735e911111c250571465ea02ac4068a3587f283477                                    │
│  │ Version: 349180714                                                                                        │
│  │ Digest: BWDmihbyV78JWpUBkCyg8fYQFmjRycU4YtPP2K3gSAju                                                      │
│  └──                                                                                                         │
│                                                                                                              │
│ Transaction Kind: Programmable                                                                               │
│ ╭──────────────────────────────────────────────────────────────────────────────────────────────────────────╮ │
│ │ Input Objects                                                                                            │ │
│ ├──────────────────────────────────────────────────────────────────────────────────────────────────────────┤ │
│ │ 0   Pure Arg: Type: address, Value: "0x21a9877e440fca354aee0f8d1ad0f19bda846cedc66e420bcaaec47d2624bd85" │ │
│ ╰──────────────────────────────────────────────────────────────────────────────────────────────────────────╯ │
│ ╭─────────────────────────────────────────────────────────────────────────╮                                  │
│ │ Commands                                                                │                                  │
│ ├─────────────────────────────────────────────────────────────────────────┤                                  │
│ │ 0  Publish:                                                             │                                  │
│ │  ┌                                                                      │                                  │
│ │  │ Dependencies:                                                        │                                  │
│ │  │   0x0000000000000000000000000000000000000000000000000000000000000001 │                                  │
│ │  │   0x0000000000000000000000000000000000000000000000000000000000000002 │                                  │
│ │  └                                                                      │                                  │
│ │                                                                         │                                  │
│ │ 1  TransferObjects:                                                     │                                  │
│ │  ┌                                                                      │                                  │
│ │  │ Arguments:                                                           │                                  │
│ │  │   Result 0                                                           │                                  │
│ │  │ Address: Input  0                                                    │                                  │
│ │  └                                                                      │                                  │
│ ╰─────────────────────────────────────────────────────────────────────────╯                                  │
│                                                                                                              │
│ Signatures:                                                                                                  │
│    ZsLleD+VebW5aIn+oVJkwby3kgBvp+I57orOhcl6ppExy0ngmcCHYXN8Jt2QuUoc3+uZpL4nd7v7BkGxJl8yBA==                  │
│                                                                                                              │
╰──────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭───────────────────────────────────────────────────────────────────────────────────────────────────╮
│ Transaction Effects                                                                               │
├───────────────────────────────────────────────────────────────────────────────────────────────────┤
│ Digest: 8kbKAFFRGgDCDL74G57T5Q1RoZN3r96kUoXDEZmnEJPT                                              │
│ Status: Success                                                                                   │
│ Executed Epoch: 871                                                                               │
│                                                                                                   │
│ Created Objects:                                                                                  │
│  ┌──                                                                                              │
│  │ ID: 0x13a222c355e6dd35e3257ab97c314ea5f5b3631e176d647da29a16c29d8e2246                         │
│  │ Owner: Shared( 349180715 )                                                                     │
│  │ Version: 349180715                                                                             │
│  │ Digest: Fzgg4G33HZNCo9tcLMEN4PdeQWyicAjE212iTtFx3i1E                                           │
│  └──                                                                                              │
│  ┌──                                                                                              │
│  │ ID: 0x1b9b3468bcbbc819807130a333c03fd19e2b7b062aa36ac90a8a2b255326bfab                         │
│  │ Owner: Immutable                                                                               │
│  │ Version: 1                                                                                     │
│  │ Digest: 6unPHy57oaqe5sU17tRm7zM6XNS8H845rF4YagqiZLyH                                           │
│  └──                                                                                              │
│  ┌──                                                                                              │
│  │ ID: 0xe6c53aaa27f1ca840810ace4cec5600910f6c64c61c24cd0e3ff6a4993be1767                         │
│  │ Owner: Account Address ( 0x21a9877e440fca354aee0f8d1ad0f19bda846cedc66e420bcaaec47d2624bd85 )  │
│  │ Version: 349180715                                                                             │
│  │ Digest: HQKs9AfmRnGKs6kDby2aLXbyKH1QnYhsjJb6bNtFoYtm                                           │
│  └──                                                                                              │
│ Mutated Objects:                                                                                  │
│  ┌──                                                                                              │
│  │ ID: 0x169fa038f40022143f16ac735e911111c250571465ea02ac4068a3587f283477                         │
│  │ Owner: Account Address ( 0x21a9877e440fca354aee0f8d1ad0f19bda846cedc66e420bcaaec47d2624bd85 )  │
│  │ Version: 349180715                                                                             │
│  │ Digest: GdUF8wwqM5Fh3sBJTLG8YjCHav8ZEyDNAacAqvmWMs4h                                           │
│  └──                                                                                              │
│ Gas Object:                                                                                       │
│  ┌──                                                                                              │
│  │ ID: 0x169fa038f40022143f16ac735e911111c250571465ea02ac4068a3587f283477                         │
│  │ Owner: Account Address ( 0x21a9877e440fca354aee0f8d1ad0f19bda846cedc66e420bcaaec47d2624bd85 )  │
│  │ Version: 349180715                                                                             │
│  │ Digest: GdUF8wwqM5Fh3sBJTLG8YjCHav8ZEyDNAacAqvmWMs4h                                           │
│  └──                                                                                              │
│ Gas Cost Summary:                                                                                 │
│    Storage Cost: 23848800 MIST                                                                    │
│    Computation Cost: 1000000 MIST                                                                 │
│    Storage Rebate: 978120 MIST                                                                    │
│    Non-refundable Storage Fee: 9880 MIST                                                          │
│                                                                                                   │
│ Transaction Dependencies:                                                                         │
│    2dkJtqsoQcyCZJvjZnskNVPQeynwVtwCcA9goAru6tTi                                                   │
│    6VDnL9zUz7zjeeFkTCfcY7MKvabiHUG3agxpaexp1tnk                                                   │
│    Dd9pn1zFcSJjinxQewFd2gQdR4XKsHxFioD5MYnwLZQz                                                   │
╰───────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ Transaction Block Events                                                                                        │
├─────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│  ┌──                                                                                                            │
│  │ EventID: 8kbKAFFRGgDCDL74G57T5Q1RoZN3r96kUoXDEZmnEJPT:0                                                      │
│  │ PackageID: 0x1b9b3468bcbbc819807130a333c03fd19e2b7b062aa36ac90a8a2b255326bfab                                │
│  │ Transaction Module: transfer_nft                                                                             │
│  │ Sender: 0x21a9877e440fca354aee0f8d1ad0f19bda846cedc66e420bcaaec47d2624bd85                                   │
│  │ EventType: 0x1b9b3468bcbbc819807130a333c03fd19e2b7b062aa36ac90a8a2b255326bfab::transfer_nft::TreasuryCreated │
│  │ ParsedJSON:                                                                                                  │
│  │   ┌─────────────┬────────────────────────────────────────────────────────────────────┐                       │
│  │   │ treasury_id │ 0x13a222c355e6dd35e3257ab97c314ea5f5b3631e176d647da29a16c29d8e2246 │                       │
│  │   └─────────────┴────────────────────────────────────────────────────────────────────┘                       │
│  └──                                                                                                            │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ Object Changes                                                                                             │
├────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ Created Objects:                                                                                           │
│  ┌──                                                                                                       │
│  │ ObjectID: 0x13a222c355e6dd35e3257ab97c314ea5f5b3631e176d647da29a16c29d8e2246                            │
│  │ Sender: 0x21a9877e440fca354aee0f8d1ad0f19bda846cedc66e420bcaaec47d2624bd85                              │
│  │ Owner: Shared( 349180715 )                                                                              │
│  │ ObjectType: 0x1b9b3468bcbbc819807130a333c03fd19e2b7b062aa36ac90a8a2b255326bfab::transfer_nft::Treasury  │
│  │ Version: 349180715                                                                                      │
│  │ Digest: Fzgg4G33HZNCo9tcLMEN4PdeQWyicAjE212iTtFx3i1E                                                    │
│  └──                                                                                                       │
│  ┌──                                                                                                       │
│  │ ObjectID: 0xe6c53aaa27f1ca840810ace4cec5600910f6c64c61c24cd0e3ff6a4993be1767                            │
│  │ Sender: 0x21a9877e440fca354aee0f8d1ad0f19bda846cedc66e420bcaaec47d2624bd85                              │
│  │ Owner: Account Address ( 0x21a9877e440fca354aee0f8d1ad0f19bda846cedc66e420bcaaec47d2624bd85 )           │
│  │ ObjectType: 0x2::package::UpgradeCap                                                                    │
│  │ Version: 349180715                                                                                      │
│  │ Digest: HQKs9AfmRnGKs6kDby2aLXbyKH1QnYhsjJb6bNtFoYtm                                                    │
│  └──                                                                                                       │
│ Mutated Objects:                                                                                           │
│  ┌──                                                                                                       │
│  │ ObjectID: 0x169fa038f40022143f16ac735e911111c250571465ea02ac4068a3587f283477                            │
│  │ Sender: 0x21a9877e440fca354aee0f8d1ad0f19bda846cedc66e420bcaaec47d2624bd85                              │
│  │ Owner: Account Address ( 0x21a9877e440fca354aee0f8d1ad0f19bda846cedc66e420bcaaec47d2624bd85 )           │
│  │ ObjectType: 0x2::coin::Coin<0x2::sui::SUI>                                                              │
│  │ Version: 349180715                                                                                      │
│  │ Digest: GdUF8wwqM5Fh3sBJTLG8YjCHav8ZEyDNAacAqvmWMs4h                                                    │
│  └──                                                                                                       │
│ Published Objects:                                                                                         │
│  ┌──                                                                                                       │
│  │ PackageID: 0x1b9b3468bcbbc819807130a333c03fd19e2b7b062aa36ac90a8a2b255326bfab                           │
│  │ Version: 1                                                                                              │
│  │ Digest: 6unPHy57oaqe5sU17tRm7zM6XNS8H845rF4YagqiZLyH                                                    │
│  │ Modules: transfer_nft                                                                                   │
│  └──                                                                                                       │
╰────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭───────────────────────────────────────────────────────────────────────────────────────────────────╮
│ Balance Changes                                                                                   │
├───────────────────────────────────────────────────────────────────────────────────────────────────┤
│  ┌──                                                                                              │
│  │ Owner: Account Address ( 0x21a9877e440fca354aee0f8d1ad0f19bda846cedc66e420bcaaec47d2624bd85 )  │
│  │ CoinType: 0x2::sui::SUI                                                                        │
│  │ Amount: -23870680                                                                              │
│  └──                                                                                              │
╰───────────────────────────────────────────────────────────────────────────────────────────────────╯

```

# Functioning

## How execute_and_burn_transfer(TransferRight, &mut Treasury, ctx) -> Coin<SUI> works and executes.

### What the function does

- Verifies that the caller is the owner of the NFT and that it hasn't already been used.
- Verifies that the shared treasury has at least 0.1 SUI.
- Debits 0.1 SUI from the treasury and creates a Coin<SUI> “payment”.
- Burns the NFT (deletes the object).
- Emits the TransferExecuted event.
- Returns the Coin<SUI> “payment” to the caller.

### Prerequisites

- Have the ID of the TransferRight NFT you own: `sui client objects --owner <your_address>` then locate the type `<pkg>::transfer_nft::TransferRight`.
- Have the ID of the shared treasury (Treasury). If you just published, retrieve it via the event:
    - `sui client event --query 'MoveEventType = "<pkg>::transfer_nft::TreasuryCreated"' --limit 1`
    - Or list the shared object if you already know the ID.

### Execution via CLI

- Simply call the function with the two IDs:
    - nft_id: the ID of your TransferRight (will be consumed/burned)
    - treasury_id: the ID of the Treasury object (shared)
- Command:
    - `sui client call --package <pkg> --module transfer_nft --function execute_and_burn_transfer --args <nft_id> <treasury_id> --gas-budget 10000000`
- Result:
    - The transaction creates a Coin<SUI> of 0.1 SUI in your possession. You will see the ID in “Created Objects” with Owner = your address.
    - The NFT no longer exists (it has been destroyed).
    - A TransferExecuted event is emitted.

### After the call

- Retrieve the ID of the created coin in “Created Objects”.
- Optional: merge the payment with another coin or transfer it:
    - Merge: `sui client merge-coin --primary-coin <target_coin_id> --coin-to-merge <payment_coin_id> --gas-budget 10000000`
    - Transfer: `sui client transfer-coin --to <dest_addr> --coin-object-id <payment_coin_id> --gas-budget 10000000`

### Execution in a PTB (JS/TS)

- To chain the call and the transfer in a single transaction:
    - `const payment = tx.moveCall({ target: "<pkg>::transfer_nft::execute_and_burn_transfer", arguments: [tx.object(nftId), tx.object(treasuryId)] });`
    - `tx.transferObjects([payment], tx.pure.address(recipient));`

### Possible Errors

- ENOT_NFT_OWNER: if you are not the owner of the NFT.
- EALREADY_USED: if the NFT has already been used.
- EINSUFFICIENT_FUNDS: if the treasury has a balance < 0.1 SUI.

