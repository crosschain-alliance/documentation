# Glossary

## Core contracts

### Hashi

Hashi is a stateless contract that acts as an entry point for other adapter contracts. It retrieves hashes associated with specific message IDs from designated adapter contracts and checks whether a predefined threshold is met.

Source code: [https://github.com/gnosis/hashi/blob/feat/v0.2.0/packages/evm/contracts/Hashi.sol](https://github.com/gnosis/hashi/blob/feat/v0.2.0/packages/evm/contracts/Hashi.sol)



### Yaho

* Yaho contract is deployed on the source chain to send messages to reporter contracts. When using the Yaho contract, you can define the security parameters of a message, including the reporter on the source chain, the adapter on the destination chain, and the threshold. You can also specify message-related data, such as the target chain ID, receiver address on the destination chain, and calldata.
* For Light Client-based oracles (like DendrETH, Spectre, etc.), the reporter address should be set to the zero address, and only the adapter address on the destination chain needs to be specified.
* Each message has a unique nonce to prevent double-spending attacks.

Source code: [https://github.com/gnosis/hashi/blob/feat/v0.2.0/packages/evm/contracts/Yaho.sol](https://github.com/gnosis/hashi/blob/feat/v0.2.0/packages/evm/contracts/Yaho.sol)

### Yaru

Yaru contract is deployed on the destination chain and is used to execute messages. It checks if the threshold from a set of designated adapters is met by interacting with the Hashi contract. If the threshold is met, Yaru continues to call the receiver contract to execute the message.

Source code: [https://github.com/gnosis/hashi/blob/feat/v0.2.0/packages/evm/contracts/Yaru.sol](https://github.com/gnosis/hashi/blob/feat/v0.2.0/packages/evm/contracts/Yaru.sol)



### Oracle

* Oracles consist of on-chain and off-chain components that help relay hashes or messages. These oracles can be general message-passing bridges like Hyperlane, LayerZero, AMB, etc., or Light Client-based oracles like DendrETH, Spectre, Telepathy, etc.
* For general message-passing bridges, the oracle includes a reporter contract on the source chain and an adapter contract on the destination chain. For Light Client-based oracles, only an adapter contract on the destination chain is needed.

Source code: [https://github.com/gnosis/hashi/tree/feat/v0.2.0/packages/evm/contracts/adapters](https://github.com/gnosis/hashi/tree/feat/v0.2.0/packages/evm/contracts/adapters)



### Reporter

A reporter contract inherits [Reporter](https://github.com/gnosis/hashi/blob/feat/v0.2.0/packages/evm/contracts/adapters/Reporter.sol) interface. It calls the underlying bridge contracts to relay a block header or a message.



### Adapter

An adapter contract inherits [Adapter](https://github.com/gnosis/hashi/blob/feat/v0.2.0/packages/evm/contracts/adapters/Adapter.sol) interface. For general message-passing bridges, the adapter contract is called by the bridge contract to store the hash of a message or block. For Light Client-based oracles, it is called when submitting proof of a block header or dispatched message event for verification. The hash is stored if the proof is valid.



### Block header / Block hash

"Block header" or "Block hash" are used interchangeably throughout this doc. It is the 32bytes hash of an execution block in an EVM chain, which is fetched from Solidity's [blockhash](https://docs.soliditylang.org/en/latest/units-and-global-variables.html#block-and-transaction-properties) function.&#x20;



