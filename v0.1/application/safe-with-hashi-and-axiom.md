# 🦺 Safe with Hashi & Axiom

<figure><img src="../../.gitbook/assets/Screenshot 2024-05-29 at 15.53.38.png" alt=""><figcaption><p>Workflow</p></figcaption></figure>



## Overview

This is a PoC of how [Axiom](https://docs.axiom.xyz/) can be used on top of our original [Safe with Hashi](safe-with-hashi.md) project. Leveraging Axiom's V2 query and ZK verification on chain, any transaction initiated from the Main Safe can be executed trustlessly on the Secondary Safe.



## How it works

1. Begin by deploying two Safes - the Main Safe and the Secondary Safe. Attach a module called `AxiomControllerModule` to the Secondary Safe.
2. Users wishing to execute a cross-chain transaction should call `execTransaction` on the `Peripheral` contract through the MainSafe which will emit `Operation` event and listened by Off chain relayer. The `data` field in the event consists of the calldata to be executed by Secondary Safe.
3. Relayer call `sendQuery` on[ AxiomV2Query](https://docs.axiom.xyz/protocol/protocol-design/axiom-query-protocol/) contract, to prove that the event is emitted on source chain.
4. AxiomV2Query contract emits `QueryInitiatedOnChain` event and triggers Axiom Prover to generate the ZK proof with respect to the query.
5. Once the ZK proof is generated, Axiom will call `fulfillQuery`  on AxiomV2Query contract, which will eventually call AxiomControllerModule to execute the transaction on behalf of Secondary Safe using `execTransactionFromModule.`



### Reference&#x20;

1. [https://github.com/crosschain-alliance/safe-crosschain/tree/feat/axiom](https://github.com/crosschain-alliance/safe-crosschain/tree/feat/axiom)
2.
