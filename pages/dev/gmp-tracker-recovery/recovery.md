# Transaction Recovery
Occasionally, transactions can get "stuck" in the pipeline from a source to destination chain (e.g. due to one-off issues that arise with relayers that operate on top of the network).

Transactions have typically gotten "stuck" in the pipeline due to:
(A) The transaction failing to relay from the source chain into the Axelar network for processing.
(B) The transaction failing to get executed on the destination chain


Users can recovery such transactions that get stuck in the pipeline by either: 
1. searching for your transaction in the Axelarscan UI and having it invoke recovery, OR 
2. incorporating the AxelarJS SDK and invoking those methods directly

## 1. Axelarscan UI

(A) If the transaction failed to relay from the source chain into the Axelar network for processing - (A) above - Axelarscan UI will show that the transaction has not been `APPROVED`. It will show an option to "APPROVE" that will manually re-submit a request to the network.

![gmp-approve.png](/images/gmp-approve.png)

The CALL APPROVED status will be updated once the network approves the transaction.

![gmp-approve-successful.png](/images/gmp-approve-successful.png)

(B) If the transaction failed to get executed on the destination chain, then Axelarscan will provide the option for you to either:
1. Manually execute a transfer on the destination chain, OR
2. Increase gas payment to the gas receiver on the source chain

### Manually execute a transfer
Click the ‘Connect’ button under the label ‘Execute at destination chain’. Then click Execute.

![gmp-execute.png](/images/gmp-execute.png)

### Increase gas payment to the gas receiver on the source chain
The prepaid gas to the Gas Service contract [[in step 2](../gmp/building-on-gmp#step-2-pay-gas-to-the-gas-services-contract)] could be insufficient when the destination chain is too busy (with many transfers or other conditions). Therefore, Axelarscan provides options to resubmit a new amount of gas as well as an option to refund the paid gas. 

To do this:
1. Click the Connect button to connect your Metamask wallet. Then switch the wallet network to the transfer’s source chain by clicking the Switch Network button under the label ‘Pay new gas at source chain’.
![gmp-pay-gas-connect-wallet.png](/images/gmp-pay-gas-connect-wallet.png)
2. Click the ‘Pay new gas’ button.
![gmp-pay-gas-success.png](/images/gmp-pay-gas-success.png)

## 2. the AxelarJS SDK

All of the recovery methods above can be done programmatically through our SDK. The benefit of this would be if you would like to incorporate these recovery features above in your application directly. In fact, Axelarscan leverages all of these methods written into the SDK. 

See SDK docs for [[the full transaction recovery API](../axelarjs-sdk/tx-status-query-recovery#query-and-recover-gmp-transactions)]