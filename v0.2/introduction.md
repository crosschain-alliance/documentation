---
description: What's new in Hashi v2.0?
---

# Introduction

Hashi v2.0 introduces several enhancements focusing on increased security and improved developer experience. Below are the detailed changes:

**1. Enhanced Message Structure**

**Hashi v1.0 Message Structure:**

```jsx
Message {
    address to;
    uint256 toChainId;
    bytes data;
}
```

In v1.0, the `Message` struct included basic fields:

* **to:** The address to which the message is sent.
* **toChainId:** The chain ID of the target chain.
* **data:** The message data.

**Hashi v2.0 Message Structure**

The new `Message` struct in v2.0 has been expanded to include more specific details, making each message request more comprehensive, customizable, and secure.

```jsx
jsxCopy codestruct Message {
    uint256 nonce;
    uint256 targetChainId;
    uint256 threshold;
    address sender;
    address receiver;
    bytes data;
    IReporter[] reporters;
    IAdapter[] adapters;
}
```

* **nonce:** A unique number for each transaction to prevent replay attacks and ensure uniqueness.
* **targetChainId:** The chain ID of the target chain (previously toChainId).
* **threshold:** The minimum number of reporters needed to validate the message.
* **sender:** The address initiating the message.
* **receiver:** The address receiving the message.
* **data:** The message data, as in v1.0.
* **IReporter\[] reporters:** An array of reporters that relay the message hash.
* **IAdapter\[] adapters:** An array of adapters that handle message hash storage.

The new structure ensures that messages are not only unique but can also be verified by multiple independent reporters, enhancing security.

**2. Improved Message Hash Calculation**

**Hashi v1.0**

In v1.0, the message hash was calculated using a combination of various fields, which made the process more complex.

```jsx
Hash = keccak256(abi.encode(uint256 chainId, uint256 id, address origin, address sender, Message message));
```

* The hash included the chain ID, message ID, origin, sender, and the message itself.

**Hashi v2.0**

In v2.0, the calculation has been simplified to improve efficiency and reduce potential errors. The hash is now computed by ABI encoding and hashing the entire `Message` struct.

```jsx
Hash = keccak256(abi.encode(Message message));
```

**3. Renaming for Clarity**

**OracleAdapters to Adapters:**

* The term "OracleAdapters" has been renamed to "Adapters" for better readability and understanding.

**4. Unified Reporter Role**

**Previously:** In v1.0, there were two distinct roles:

* **HeaderReporter:** Responsible for reporting message headers.
* **MessageRelayer:** Responsible for relaying message hashes.

**Now in v2.0:** These roles have been merged into a single, more streamlined role:

* **Reporter:** A unified role that initiates can relay both message headers and mesage hashes.

#### Summary

Hashi v2.0 focuses on enhancing security and developer experience by:

* Introducing a more detailed and secure `Message` struct.
* Simplifying message hash calculation.
* Renaming components for clarity.
* Unifying roles to streamline operations and reduce complexity.

\
Reference

1. Github: [https://github.com/gnosis/hashi/tree/feat/v0.2.0](https://github.com/gnosis/hashi/tree/feat/v0.2.0)
