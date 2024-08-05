---
description: >-
  Block header querying enables one to check whether a block has been dispatched
  from source chain and stored in destination chain.
---

# Query Block Header

There are three ways to query block header

1. Using event filter
2. Using Hashi Explorer (available soon)
3. Interacting with Hashi contract



## Using Event Filters

### Workflow

1. Block header is dispatched from source chain through a reporter contract `dispatchBlocks` function, and emit `BlockDispatched` event.
2. The reporter relay block header through the oracle and call adapter contract's `setHashes` function, and emit `HashStored` event.

Using event filter method allows you to target a specific oracle's `BlockDispatched` and `HashStored` events. If you need to check block header from multiple oracles, consider calling Hashi contract directly.

In this tutorial, we are going to use [Base](https://www.base.org/) as source chain, and check whether Base's block header has been dispatched to other destination chains.&#x20;

### Source Chain Block Dispatching

We are using [Viem](https://viem.sh/) in this example, alternatives are [etherjs](https://ethers.org/), [web3js](https://web3js.org/).

1. Create a public client for [Base](https://www.base.org/).
2.  Create event filters:&#x20;

    1. address: reporter address on Base (available on [deployment.md](../deployment.md "mention"))
    2. abi: ABI of the event to filter from. In this case, it is the `BlockDispatched` event.
    3. eventName: `BlockDispatched`
    4. args (optional):  args field target the exact parameter you want to query, if there is no available log that matches the args, it will return empty array.
       1. targetChainId: Chain ID of the destination chain that the block header will be relayed to. Comply with [EIP 155 ](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-155.md)standard. You may check the chain ID using[ ChainList.org](https://chainlist.org/). i.e. Polygon's Chain ID 137.
       2. blockNumber: The block number from source chain. i.e. Block Number from Base 18012478.
    5. fromBlock: Block to start including logs from.&#x20;
    6. toBlock:  Block to stop including logs from.

    For more info, check [Viem's guide on getContractEvents](https://viem.sh/docs/contract/getContractEvents#getcontractevents).

#### Code snippet

```
 // viem
 
 // 1. create client for Base
 const baseClient = createPublicClient({
    chain: base,
    transport: http(),
  });


 const reporterAddress = "0x495b872b329eba69F81A749f8A152766851C23b0";

// 2. Create event filters
 const blockDispatchedlogs = await baseClient.getContractEvents({
    address: reporterAddress,
    abi: [
      parseAbiItem(
        "event BlockDispatched(uint256 indexed targetChainId,address adapter,uint256 indexed blockNumber,bytes32 blockHeader)"
      ),
    ],
    eventName: "BlockDispatched",
    args: {
      targetChainId: 137n, // optional
      blockNumber: 18012478n, // optional
    },
    fromBlock: 18012508n,
    toBlock: "latest",
  });
```

#### Return

```
[
  {
    eventName: 'BlockDispatched',
    args: {
      targetChainId: 137n,
      blockNumber: 18012478n,
      adapter: '0x998dA7f6cF98541E4F4469cc9d53B9374F186591',
      blockHeader: '0x66a7e93c32c8238638c25e2ad0470ffbcff2949cb68ecfbbcfef124e5deff561'
    },
    address: '0x495b872b329eba69f81a749f8a152766851c23b0',
    blockHash: '0xa780983b1720cb52bd526230f7eba88ec39c23862f2fa2b73e694fa2f7aa70ee',
    blockNumber: 18012514n,
    data: '0x000000000000000000000000998da7f6cf98541e4f4469cc9d53b9374f18659166a7e93c32c8238638c25e2ad0470ffbcff2949cb68ecfbbcfef124e5deff561',
    logIndex: 298,
    removed: false,
    topics: [
      '0xdfde4db189423e6f919a3d3cb1306e03dc18b4e72bc0c6c13fe07c58b395335c',
      '0x0000000000000000000000000000000000000000000000000000000000000089',
      '0x000000000000000000000000000000000000000000000000000000000112d93e'
    ],
    transactionHash: '0x8f57cb6953d34e8cdfcecb0613dd1f849cb09bc1840accf7fd27fcac96e50cef',
    transactionIndex: 72
  }
]
```

### Destination Chain Block Header Querying

In this example, we check the adapter contract on [Polygon](https://polygon.technology/polygon-pos) if block header from Base has been dispatched.

1. Create a public client for [Polygon](https://polygon.technology/polygon-pos).
2.  Create event filters:

    1. address: adapter address on Base (available on [deployment.md](../deployment.md "mention"))
    2. abi: ABI of the event to filter from. In this case, it is the `HashStored` event.
    3. eventName: `HashStored`
    4. args (optional):  args field target the exact parameter you want to query, if there is no available log that matches the args, it will return empty array.
       1. id: block number from the source chain.
       2. hash: block header with respect to the block number (id).
    5. fromBlock: Block to start including logs from.&#x20;
    6. toBlock:  Block to stop including logs from.

    For more info, check [Viem's guide on getContractEvents](https://viem.sh/docs/contract/getContractEvents#getcontractevents).

#### Code snippet

```
// Viem

// 1. Create Polygon Client
  const polygonClient = createPublicClient({
    chain: polygon,
    transport: http(),
  });

  const adapterAddress = "0x998dA7f6cF98541E4F4469cc9d53B9374F186591";
 
 // 2. Create event filters
  const hashStoredLogs = await polygonClient.getContractEvents({
    address: adapterAddress,
    abi: [
      parseAbiItem("event HashStored(uint256 indexed id,bytes32 indexed hash)"),
    ],
    eventName: "HashStored",
    args: {
      id: 18012478n,
      hash: "0x66A7E93C32C8238638C25E2AD0470FFBCFF2949CB68ECFBBCFEF124E5DEFF561",
    },
    fromBlock: 60201668n,
    toBlock: "latest",
  });
  console.log(hashStoredLogs);
};


```

#### Return

```
[
  {
    eventName: 'HashStored',
    args: {
      id: 18012478n,
      hash: '0x66a7e93c32c8238638c25e2ad0470ffbcff2949cb68ecfbbcfef124e5deff561'
    },
    address: '0x998da7f6cf98541e4f4469cc9d53b9374f186591',
    topics: [
      '0x7c57815e36323391c63e53a2fe2969599eb6dbcf52484a3bd8909aef4a6704d7',
      '0x000000000000000000000000000000000000000000000000000000000112d93e',
      '0x66a7e93c32c8238638c25e2ad0470ffbcff2949cb68ecfbbcfef124e5deff561'
    ],
    data: '0x',
    blockNumber: 60201668n,
    transactionHash: '0xf871845c8e8a6f612b2706844069c06d924660c84c67580744591c4d62a8bbe4',
    transactionIndex: 21,
    blockHash: '0xb106d12f70119143db0564350b9183dd080178f591006dc258956b8845b5dadb',
    logIndex: 87,
    removed: false
  }
]
```



## Interacting with Hashi contract

### Workflow

1. Find the Hashi contract in [deployment.md](../deployment.md "mention")
2. Read contract function.&#x20;

#### Function arguments

1. `domain` : Chain ID of the source chain. i.e. 1 for Ethereum, 8453 for Base.
2. `id`: block number of the source chain. (Message ID of the message in the case of Message Dispatching)
3. `adapters` : adapter contract to query from. You may query specific adapter or multiple adapters.
4. `threshold` : In `checkHashWithThresholdFromAdapters` function, `threshold` argument is the number of hash stored by `adapters` agreed upon. I.e. If there are 3 `adapters` and 2 as `threshold`, the function will return true if 2/3 of the adapters store the same hash w.r.t the same `id`.

#### Function

1. `checkHashWithThresholdFromAdapters` : Return boolean, check whether the threshold amount of adapters store the same hash w.r.t the same domain & id.
2. `getHash` : Return bytes32 hash, check whether all the adapters store the same hash w.r.t the same domain & id.
3. `getHashFromAdapter` : Return bytes32 hash, check whether a specific adapter store hash w.r.t a domain & id.
4. `getHashesFromAdapters` : Return bytes32\[] hash, check hash from each adapters w.r.t the same domain & id.

For more details about the Hashi contract, check out [Hashi.sol](https://github.com/gnosis/hashi/blob/feat/v0.2.0/packages/evm/contracts/Hashi.sol).\


#### How to check if a block hash of block number X has been dispatched?

1. To check if a block number has been dispatched, you need to filter out the `BlockDispatched` from the reporter contract of the source chain. For a specific target chain, includes `targetChainId` in the filter argument.
2. Once you get the logs, you can check which block number has been dispatched from the source reporter contract to your destination adapter contract in the indexed block number event argument.&#x20;
3. Incidents might happen where the source reporter contract dispatches block and event `BlockDispatched` event correctly, but the block hash is not stored on the destination adapter contract, due to error from the oracle. You can check the status of the oracle by using tool provided by the oracles, for example:
   1. LayerZero: [https://layerzeroscan.com/](https://layerzeroscan.com/)
   2. AMB: [https://bridge.gnosischain.com/bridge-explorer](https://bridge.gnosischain.com/bridge-explorer)
   3. Hyperlane: [https://explorer.hyperlane.xyz/](https://explorer.hyperlane.xyz/)&#x20;
