---
description: Contract addresses on mainnet and testnet.
---

# Deployment

## Mainnet

<figure><img src="../.gitbook/assets/hiashiv0.2.png" alt=""><figcaption></figcaption></figure>

Note:

1. Current deployments on mainnet involves only general message passing based oracles, while zk Light Client based oracle will be available soon. ZK light client based oracle is already available on testnet.
2. More chain connections will be available soon.

### Core contracts

<table><thead><tr><th width="123">Chain</th><th>Hashi </th><th>Header Storage</th><th>Yaho</th></tr></thead><tbody><tr><td>Ethereum</td><td><a href="https://etherscan.io/address/0xA86bc62Ac53Dc86687AB6C15fdebC71ad51fB615">0xA86bc62Ac53Dc86687AB6C15fdebC71ad51fB615</a></td><td><a href="https://etherscan.io/address/0x117D7D593e6a7d9699a763C552BFA3177a46B957">0x117D7D593e6a7d9699a763C552BFA3177a46B957</a></td><td><a href="https://etherscan.io/address/0xbAE4Ebbf42815BB9Bc3720267Ea4496277d60DB8">0xbAE4Ebbf42815BB9Bc3720267Ea4496277d60DB8</a></td></tr><tr><td>Gnosis Chain</td><td><a href="https://gnosisscan.io/address/0xA86bc62Ac53Dc86687AB6C15fdebC71ad51fB615">0xA86bc62Ac53Dc86687AB6C15fdebC71ad51fB615</a></td><td><a href="https://gnosisscan.io/address/0x117D7D593e6a7d9699a763C552BFA3177a46B957">0x117D7D593e6a7d9699a763C552BFA3177a46B957</a></td><td><a href="https://gnosisscan.io/address/0xbAE4Ebbf42815BB9Bc3720267Ea4496277d60DB8">0xbAE4Ebbf42815BB9Bc3720267Ea4496277d60DB8</a></td></tr><tr><td>Polygon</td><td><a href="https://polygonscan.com/address/0xA86bc62Ac53Dc86687AB6C15fdebC71ad51fB615">0xA86bc62Ac53Dc86687AB6C15fdebC71ad51fB615</a></td><td><a href="https://polygonscan.com/address/0x117D7D593e6a7d9699a763C552BFA3177a46B957">0x117D7D593e6a7d9699a763C552BFA3177a46B957</a></td><td><a href="https://polygonscan.com/address/0xbAE4Ebbf42815BB9Bc3720267Ea4496277d60DB8">0xbAE4Ebbf42815BB9Bc3720267Ea4496277d60DB8</a></td></tr><tr><td>BNB</td><td><a href="https://bscscan.com/address/0xbAE4Ebbf42815BB9Bc3720267Ea4496277d60DB8">0xbAE4Ebbf42815BB9Bc3720267Ea4496277d60DB8</a></td><td><a href="https://bscscan.com/address/0x79e4D1B8b8De0bC2F8A3DC477480C935C66F373E">0x79e4D1B8b8De0bC2F8A3DC477480C935C66F373E</a></td><td><a href="https://bscscan.com/address/0xC82e50cc90C84DC492B4Beb6792DEeB496d52424">0xC82e50cc90C84DC492B4Beb6792DEeB496d52424</a></td></tr><tr><td>Base</td><td><a href="https://basescan.org/address/0x79e4D1B8b8De0bC2F8A3DC477480C935C66F373E#code">0x79e4D1B8b8De0bC2F8A3DC477480C935C66F373E</a></td><td><a href="https://basescan.org/address/0xC82e50cc90C84DC492B4Beb6792DEeB496d52424#code">0xC82e50cc90C84DC492B4Beb6792DEeB496d52424</a></td><td><a href="https://basescan.org/address/0xfe2bafe5aCA5bF884F8a9148535F11B46f6D1c8f">0xfe2bafe5aCA5bF884F8a9148535F11B46f6D1c8f</a></td></tr><tr><td>Arbitrum*</td><td><a href="https://arbiscan.io/address/0x117D7D593e6a7d9699a763C552BFA3177a46B957#code">0x117D7D593e6a7d9699a763C552BFA3177a46B957</a></td><td><a href="https://arbiscan.io/address/0x6f04acf44aab94965268c0d04a0b6d5e6c03dff3#code">0x6F04acf44aab94965268c0d04a0b6D5E6C03DFF3</a></td><td><a href="https://arbiscan.io/address/0x79e4D1B8b8De0bC2F8A3DC477480C935C66F373E#code">0x79e4D1B8b8De0bC2F8A3DC477480C935C66F373E</a></td></tr><tr><td>Optimism</td><td><a href="https://optimistic.etherscan.io/address/0x79e4D1B8b8De0bC2F8A3DC477480C935C66F373E#code">0x79e4D1B8b8De0bC2F8A3DC477480C935C66F373E</a></td><td><a href="https://optimistic.etherscan.io/address/0xC82e50cc90C84DC492B4Beb6792DEeB496d52424#code">0xC82e50cc90C84DC492B4Beb6792DEeB496d52424</a></td><td><a href="https://optimistic.etherscan.io/address/0x7237bb8d1d38DF8b473b5A38eD90088AF162ad8e#code">0x7237bb8d1d38DF8b473b5A38eD90088AF162ad8e</a></td></tr></tbody></table>

\*Arbitrum uses ArbHeaderStorage.sol instead of HeaderStorage.sol

### Oracle: Layer Zero&#x20;

Reporter dispatches blocks or messages from source chain, and Adapter stores hash on the destination chain.&#x20;

#### Reporter

<table><thead><tr><th width="138">Chain</th><th>Reporter Address</th><th>Supported Destination Chain</th></tr></thead><tbody><tr><td>Ethereum</td><td> <a href="https://etherscan.io/address/0xbc5f67da5347cd4304e9623bc86e71a874287ea1">0xbc5f67da5347cd4304e9623bc86e71a874287ea1</a></td><td>Polygon, BNB, Arbitrum, Optimism, Base</td></tr><tr><td>Gnosis Chain</td><td><a href="https://gnosisscan.io/address/0x9f2e5aaf38023D3f9a5bC9B4C2c9f523Fd75E36b#code">0x9f2e5aaf38023D3f9a5bC9B4C2c9f523Fd75E36b</a></td><td>Polygon, BNB, Arbitrum, Optimism, Base</td></tr><tr><td>Polygon</td><td> <a href="https://polygonscan.com/address/0x147Abe85112154b3D5bF55d10cEE64aeD0279479#code">0x147Abe85112154b3D5bF55d10cEE64aeD0279479</a></td><td>Gnosis, Gnosis Chain, BNB, Arbitrum, Optimism, Base</td></tr><tr><td>BNB</td><td><a href="https://bscscan.com/address/0x3E80f3987A570eC1C5c91e982dc88FCC01f4aA11#code">0x3E80f3987A570eC1C5c91e982dc88FCC01f4aA11</a></td><td>Gnosis, Polygon, Arbitrum, Optimism, Base</td></tr><tr><td>Arbitrum</td><td><a href="https://arbiscan.io/address/0x6602dc9b6bd964C2a11BBdA9B2275308D1Bbc14f#code">0x6602dc9b6bd964C2a11BBdA9B2275308D1Bbc14f</a></td><td>Gnosis, Polygon, BNB, Optimism, Base</td></tr><tr><td>Optimism</td><td><a href="https://optimistic.etherscan.io/address/0xd60899683383E53AB8807F0cD34e3a6Dd6dF66a3#code">0xd60899683383E53AB8807F0cD34e3a6Dd6dF66a3</a></td><td>Gnosis, Polygon, BNB, Arbitrum, Base</td></tr><tr><td>Base</td><td><a href="https://basescan.org/address/0x495b872b329eba69F81A749f8A152766851C23b0#code">0x495b872b329eba69F81A749f8A152766851C23b0</a></td><td>Gnosis, Polygon, BNB, Arbitrum, Optimism</td></tr></tbody></table>

#### Adapter

<table><thead><tr><th width="139">Chain</th><th>Adapter Address</th><th>Supported Source Chain</th></tr></thead><tbody><tr><td>Gnosis Chain</td><td><a href="https://gnosisscan.io/address/0xC82e50cc90C84DC492B4Beb6792DEeB496d52424">0xC82e50cc90C84DC492B4Beb6792DEeB496d52424</a></td><td>Polygon, BNB, Arbitrum, Optimism, Base</td></tr><tr><td>Polygon</td><td><a href="https://polygonscan.com/address/0x998dA7f6cF98541E4F4469cc9d53B9374F186591#writeContract">0x998dA7f6cF98541E4F4469cc9d53B9374F186591</a></td><td>Ethereum, BNB, Arbitrum, Optimism, Base</td></tr><tr><td>BNB</td><td><a href="https://bscscan.com/address/0xDbdF80c87f414fac8342e04D870764197bD3bAC7#writeContract">0xDbdF80c87f414fac8342e04D870764197bD3bAC7</a></td><td>Ethereum, Gnosis Chain, Polygon, Arbitrum, Optimism, Base</td></tr><tr><td>Arbitrum</td><td><a href="https://arbiscan.io/address/0xA86bc62Ac53Dc86687AB6C15fdebC71ad51fB615#writeContract">0xA86bc62Ac53Dc86687AB6C15fdebC71ad51fB615</a></td><td>Ethereum, Gnosis Chain, Polygon, BNB, Optimism, Base</td></tr><tr><td>Optimism</td><td><a href="https://optimistic.etherscan.io/address/0xA86bc62Ac53Dc86687AB6C15fdebC71ad51fB615#code">0xA86bc62Ac53Dc86687AB6C15fdebC71ad51fB615</a></td><td>Ethereum, Gnosis Chain, Polygon, BNB, Arbitrum, Base</td></tr><tr><td>Base</td><td><a href="https://basescan.org/address/0xA86bc62Ac53Dc86687AB6C15fdebC71ad51fB615#code">0xA86bc62Ac53Dc86687AB6C15fdebC71ad51fB615</a></td><td>Ethereum, Gnosis Chain, Polygon, BNB, Arbitrum, Optimism</td></tr></tbody></table>



### Oracle: AMB

Source Chain: Ethereum

Reporter: [0xDbdF80c87f414fac8342e04D870764197bD3bAC7](https://etherscan.io/address/0xDbdF80c87f414fac8342e04D870764197bD3bAC7)

Destination Chain: Gnosis Chain

Adapter: [0x79e4D1B8b8De0bC2F8A3DC477480C935C66F373E](https://gnosisscan.io/address/0x79e4D1B8b8De0bC2F8A3DC477480C935C66F373E)



## Testnet

#### Sepolia

<table><thead><tr><th width="264">Contract</th><th>Address</th></tr></thead><tbody><tr><td>HeaderStorage</td><td><a href="https://sepolia.etherscan.io/address/0x48800eBEf4491C65b2172d3628DdDDC9c47fe430">0x48800eBEf4491C65b2172d3628DdDDC9c47fe430</a></td></tr><tr><td>Hashi</td><td><a href="https://sepolia.etherscan.io/address/0x78E4ae687De18B3B71Ccd0e8a3A76Fed49a02A02#code">0x78E4ae687De18B3B71Ccd0e8a3A76Fed49a02A02</a></td></tr><tr><td>Yaho</td><td><a href="https://sepolia.etherscan.io/address/0x21eAB033C7D2DF6A67AeF6C5Bda9A7F151eB9f52">0x21eAB033C7D2DF6A67AeF6C5Bda9A7F151eB9f52</a></td></tr><tr><td>Yaru (listen to Yaho from Chiado)</td><td><a href="https://sepolia.etherscan.io/address/0xBA9165973963a6E5608f03b9648c34A737E48f68#code">0xBA9165973963a6E5608f03b9648c34A737E48f68</a></td></tr><tr><td>Yaru (listen to Yaho from Lukso testnet)</td><td><a href="https://sepolia.etherscan.io/address/0x05B40580B851eA6c73CEd39d5c8aB91bAd7C4FF7#readProxyContract">0x05B40580B851eA6c73CEd39d5c8aB91bAd7C4FF7</a></td></tr><tr><td>AMBReporter</td><td><a href="https://sepolia.etherscan.io/address/0xc6755144d60548f3DD420F47Cf48DAe553bBf042#code">0xc6755144d60548f3DD420F47Cf48DAe553bBf042</a></td></tr><tr><td>CCIP Reporter</td><td><a href="https://sepolia.etherscan.io/address/0xf66871C91952b09270d223cD3A1e5Dad57b14fbC#readProxyContract">0xf66871C91952b09270d223cD3A1e5Dad57b14fbC</a></td></tr><tr><td>Wormhole Reporter </td><td><a href="https://sepolia.etherscan.io/address/0xeE8082F48e768e096c2EEC5C80DC818eb6E15858">0xeE8082F48e768e096c2EEC5C80DC818eb6E15858</a></td></tr><tr><td>AMBAdapter</td><td><a href="https://sepolia.etherscan.io/address/0x3F5929bee6A59661D6CcC9c4eB751048009CE11B#code">0x3F5929bee6A59661D6CcC9c4eB751048009CE11B</a></td></tr><tr><td>DendrETH Adapter (updates block header from Chiado)</td><td><a href="https://sepolia.etherscan.io/address/0x4e630e1a7b90230b459d7338d65de015acdd54a4#code">0x4e630e1a7b90230b459d7338d65de015acdd54a4</a></td></tr></tbody></table>

#### Chiado

<table><thead><tr><th width="265">Contract</th><th>Address</th></tr></thead><tbody><tr><td>HeaderStorage</td><td>0xCA179da79CC27f8eb4cB540Eeb62f2F171521222</td></tr><tr><td>Hashi</td><td><a href="https://gnosis-chiado.blockscout.com/address/0x78E4ae687De18B3B71Ccd0e8a3A76Fed49a02A02#code">0x78E4ae687De18B3B71Ccd0e8a3A76Fed49a02A02</a></td></tr><tr><td>Yaho</td><td><a href="https://gnosis-chiado.blockscout.com/address/0x21eAB033C7D2DF6A67AeF6C5Bda9A7F151eB9f52?tab=contract">0x21eAB033C7D2DF6A67AeF6C5Bda9A7F151eB9f52</a></td></tr><tr><td>Yaru (listen to Yaho from Sepolia)</td><td><a href="https://gnosis-chiado.blockscout.com/address/0xBA9165973963a6E5608f03b9648c34A737E48f68?tab=contract">0xBA9165973963a6E5608f03b9648c34A737E48f68</a></td></tr><tr><td>AMBReporter</td><td><a href="https://gnosis-chiado.blockscout.com/address/0xc6755144d60548f3DD420F47Cf48DAe553bBf042?tab=txs">0xc6755144d60548f3DD420F47Cf48DAe553bBf042</a></td></tr><tr><td>AMBAdapter</td><td><a href="https://gnosis-chiado.blockscout.com/address/0x3F5929bee6A59661D6CcC9c4eB751048009CE11B#code">0x3F5929bee6A59661D6CcC9c4eB751048009CE11B</a></td></tr><tr><td>CCIP Adapter</td><td><a href="https://gnosis-chiado.blockscout.com/address/0x8A2A7509B98f0f21BEFF82e2520A920DB61fFa9d?tab=contract">0x8A2A7509B98f0f21BEFF82e2520A920DB61fFa9d</a></td></tr><tr><td>Wormhole Adapter </td><td><a href="https://gnosis-chiado.blockscout.com/address/0x79e4D1B8b8De0bC2F8A3DC477480C935C66F373E">0x79e4D1B8b8De0bC2F8A3DC477480C935C66F373E</a></td></tr><tr><td>DendrETH Adapter (updates block header from Sepolia)</td><td><a href="https://gnosis-chiado.blockscout.com/address/0x355C483e7D7D73eb9C06DDA1819a0Cc99712233c?tab=txs">0x355C483e7D7D73eb9C06DDA1819a0Cc99712233c</a></td></tr></tbody></table>

#### Lukso Testnet

<table><thead><tr><th width="262">Contract</th><th>Address</th></tr></thead><tbody><tr><td>HeaderStorage</td><td><a href="https://explorer.execution.testnet.lukso.network/address/0xE644169dd6E3c375772386dF39Ef6F2928Df921a#code">0xE644169dd6E3c375772386dF39Ef6F2928Df921a</a></td></tr><tr><td>Hashi</td><td><a href="https://explorer.execution.testnet.lukso.network/address/0x94c04fE1d20B0c3fcADB44C042c38C4E337Ccc49?tab=contract">0x94c04fE1d20B0c3fcADB44C042c38C4E337Ccc49</a></td></tr><tr><td>Yaho</td><td><a href="https://explorer.execution.testnet.lukso.network/address/0x58CCfAadc4E9A8f3448494281d030843dE137B8c#code">0x58CCfAadc4E9A8f3448494281d030843dE137B8c</a></td></tr><tr><td>Yaru (listen to Yaho from Sepolia)</td><td><a href="https://explorer.execution.testnet.lukso.network/address/0xBd5CE0aAE635B36Eec47018aA42e1A322CE26A54#code">0xBd5CE0aAE635B36Eec47018aA42e1A322CE26A54</a></td></tr><tr><td>DendrETH (updates block header from Sepolia) </td><td><a href="https://explorer.consensus.testnet.lukso.network/address/0xD875797F284887296B8812a8E50a1da3AD92f6Da">0xD875797F284887296B8812a8E50a1da3AD92f6Da</a></td></tr></tbody></table>



Note:

1. Light Client based oracle doesn't require a reporter contract on source chain to dispatch Message or block headers, it only need a adapter contract on destination chain. Proof will be generated off chain and submitted to adapter contract for verification. Once verification is valid, hash will be stored.
2. Light Client based oracle: DendrETH, Spectre, Telepathy, etc.
3. General Message Passing (GMP) oracle: AMB, LayerZero, CCIP, Hyperlane, etc.&#x20;

