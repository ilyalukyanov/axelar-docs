# Monitoring State of Cross-Chain Transactions
Axelar provides two options to check each GMP transfer status via: 
1. the Axelarscan UI, OR 
2. the AxelarJS SDK

## 1. Axelarscan UI
Anyone can view the General Message Passing transaction on the GMP page of Axelarscan
- mainnet: https://axelarscan.io/gmp
- testnet: https://testnet.axelarscan.io/gmp.

![gmp-tracker.png](/images/gmp-tracker-2.png)

To search for a particular transfer, you can enter either a transaction hash or a sender address in the search bar. 
![gmp-searchbar.png](/images/gmp-searchbar.png)

## 2. the AxelarJS SDK

See SDK docs for [[Query transaction status by txHash](axelarjs-sdk/tx-status-query-recovery#query-transaction-status-by-txhash)]