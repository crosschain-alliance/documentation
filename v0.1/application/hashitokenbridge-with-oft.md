# 🌄 Safe Junction with OFT

<figure><img src="../../.gitbook/assets/diagram (4) (1).png" alt=""><figcaption></figcaption></figure>

## How it works&#x20;

1\. Deploy two `SJLZEndpoints`, one on each of the source and destination chains. SJLZEndpoint acts as a Layer Zero compatible endpoint, utilizing Hashi for cross-chain message propagation.&#x20;

2\. Deploy two `SJToken` contracts, following the `OFT` (Omnichain Fungible Token) standard. One contract on the source chain and the other on the destination chain. Reference the[ OFT documentation](https://layerzero.gitbook.io/docs/evm-guides/layerzero-omnichain-contracts/oft/oftv2) for guidance.&#x20;

3\. Execute `xTransfer` on the SJToken to start a cross-chain minting or burning process. Ensure you approve the required token amount for wrapping if you are on the native chain.&#x20;

4\. The `xTransfer` function internally calls `_send`, a function defined in the OFT standard. This function, in turn, invokes the `send` function on `SJLZEndpoint` with a specific payload.&#x20;

5\. The `SJLZEndpoint` employs `Yaho` to relay the message across chains using the Hashi Message Relays.&#x20;

6\. Each involved bridge processes the message and stores the hash of the message in its adapter.&#x20;

7\. After all bridges have processed the message, Hashi executes it.&#x20;

8\. Upon execution, `Yaru` calls `SJLZEndpoint.receivePayload`, which then calls `lzReceive` on the host SJToken. The `lzReceive` implemented within the OFT contract, mints the corresponding amount of tokens.

### Reference

1. [https://github.com/crosschain-alliance/sj-core-contracts/tree/feat/oft](https://github.com/crosschain-alliance/sj-core-contracts/tree/feat/oft)
