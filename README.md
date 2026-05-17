# Week 0: Foundations of Blockchain & Cryptography

Welcome to the first week of your Web3 journey! This week is all about the "why" and "how" behind the technology. Before we dive into writing smart contracts, we need to understand the bedrock they sit on: decentralized ledgers, cryptographic primitives, and the architecture of Ethereum.

## 🎯 Learning Objectives

By the end of this week, we'll reach several milestones:

* Explain what a **blockchain** actually is (and isn't).
* Describe how **hash functions** and **public/private keys** secure data.
* Understand the core components of **Ethereum** (ETH, EVM, and Smart Contracts).
* Outline the differences between **Layers**.
* Differentiate between **Proof of Work (PoW)** and **Proof of Stake (PoS)**.
* Explain how **Merkle Trees** allow for efficient data verification.
* Recognize basic **Smart Contract security principles**.


## 🏗️ Blockchain Basics
Think of a blockchain as a **digital record book** that isn't kept by a single person or company. Instead, it's shared across a global network of computers (nodes).

* **Blocks & Chains:** Transactions are grouped into "blocks." Each block points back to the one before it using a unique digital fingerprint (a hash). If you change one transaction in an old block, its hash changes, which breaks the link to every following block. This makes the ledger **immutable**.
* **Decentralization:** Because everyone has a copy of the book, no single party can "edit" history. This creates a system that is censorship resistant and transparent.

> **📂 Deep Dive:** [What is a Blockchain? (Ledger Academy)](https://www.ledger.com/academy/what-is-blockchain)


## 🔐 Cryptography: The Engine Room
Blockchain security isn't magic; it's math. There are two main concepts you need to master:

### 1. Cryptographic Hash Functions
A hash function takes any input (a word, a file, a movie) and turns it into a fixed length string of characters. 
* **Deterministic:** The same input always gives the same output.
* **Irreversible:** You can't turn the hash back into the original data.
* **Collision Resistant:** Even changing a single comma in a 500 page book will result in a completely different hash.

> **📂 Deep Dive:** [Hash Functions (GeeksforGeeks)](https://www.geeksforgeeks.org/dsa/cryptography-hash-functions/) | [SHA-256 Algorithm (SimpliLearn)](https://www.simplilearn.com/tutorials/cyber-security-tutorial/sha-256-algorithm)


**Try it in Python:**
You can see this in action using the `hashlib` library. This script generates a SHA-256 hash, the same standard used by Bitcoin and Ethereum.

```python
import hashlib

def sha256_hash(data):
    # Create a new sha256 hash object
    sha256 = hashlib.sha256()
    
    # Update the hash object with the bytes of the data
    sha256.update(data.encode('utf-8'))
    
    # Return the hexadecimal representation of the hash
    return sha256.hexdigest()

# Example usage
data = "Hello, World!"
print(f"SHA256 hash of '{data}' is: {sha256_hash(data)}")
```

### 2. Public Key Cryptography
This is how we handle "identity" without passwords. Every user has a **Key Pair**:
* **Private Key:** Your "digital signature." Never share this. It's used to authorize transactions.
* **Public Key:** Your "account number." This is what you share so people can send you funds.
Anyone can use your Public Key to verify that a transaction was indeed signed by your Private Key, without ever seeing the secret key itself.

> **📂 Deep Dive:** [Digital Signatures (Binance Academy)](https://academy.binance.com/en/articles/what-is-a-digital-signature)


## ⟠ Ethereum Overview
While Bitcoin is "Digital Gold," Ethereum is "Digital Oil" or a "Global Computer." It doesn't just record transactions; it runs **Smart Contracts**.

* **Smart Contracts:** These are self executing pieces of code that live on the blockchain. They work exactly as programmed without any chance of downtime or third party interference.
* **Ether (ETH):** The native currency used to pay for the "work" the network does.
* **EVM (Ethereum Virtual Machine):** Think of this as the giant, shared computer that every node on the network runs to process the code in smart contracts.

> **📂 Deep Dive:** [What is Ethereum? (Official)](https://ethereum.org/en/what-is-ethereum/) | [EVM Deep Dive](https://ethereum.org/en/developers/docs/evm/)


## 🧱 Architecture & Layers
The blockchain world is organized in layers to help it scale:
* **Layer 1 (The Base):** The main blockchain (Ethereum, Bitcoin). This is where final security and consensus happen.
* **Layer 2 (The Scalers):** Solutions like Optimism, Arbitrum, or the Lightning Network that handle transactions "off chain" to make them faster and cheaper, then settle back to Layer 1.
* **Layer 3 (The Apps):** The user interface decentralized apps (dApps) like Uniswap or OpenSea.

> **📂 Deep Dive:** [Blockchain Layers (Binance Academy)](https://academy.binance.com/en/articles/what-is-layer-1-in-blockchain) | [Ethereum's Layer 2 Hub](https://ethereum.org/en/layer-2/)


## 🤝 Consensus: How do we agree?
Since there is no "boss" in a decentralized network, nodes need a way to agree on which transactions are valid.
* **Proof of Work (PoW):** Nodes (miners) use electricity to solve complex math puzzles. It's very secure but uses a lot of energy.
* **Proof of Stake (PoS):** Nodes (validators) "stake" their own tokens (ETH) as collateral. If they follow the rules, they earn rewards. If they lie, they lose their stake. This is ~99.9% more energy efficient than PoW.

> **📂 Deep Dive:** [The Merge (Ethereum)](https://ethereum.org/en/roadmap/merge/)


## 🌳 Merkle Trees
How do we verify one transaction among millions without downloading the whole blockchain? We use a **Merkle Tree**.
It's a structure that hashes pairs of transactions together repeatedly until only one hash—the **Merkle Root**—remains. This root acting as a "summary" of every transaction in the block. If even one bit of a transaction changes, the entire root changes.

> **📂 Deep Dive:** [Merkle Tree Concept (Investopedia)](https://www.investopedia.com/terms/m/merkle-tree.asp)


## ⚠️ Smart Contract Security Basics
In Web3, "Code is Law." If there’s a bug in your contract, a hacker can drain funds, and there is no "undo" button.
* **Checks Effects Interactions:** Always update your internal state (like balances) before sending money out.
* **Use Audited Libraries:** Don't reinvent the wheel. Use [OpenZeppelin](https://openzeppelin.com/contracts/) for standard, secure contract components.
* **Immutability:** Once it’s deployed, you usually can't change it. Test, test, and test again on "Testnets" (fake money networks) before going live.


## 🛠️ Interactive Tools & Simulators
The best way to learn is to break things. Use these tools to see the concepts in action:

1. [Blockchain Demo](https://andersbrownworth.com/blockchain/): A must see visuals. Watch how changing one block turns the whole chain red.
2. [SHA-256 Hash Generator](https://emn178.github.io/online-tools/sha256.html): Type anything and see how the hash changes instantly.
3. [Proof of Work Simulator](https://andersbrownworth.com/blockchain/block): See how "mining" actually works by finding a valid nonce.
4. [Remix IDE](https://remix.ethereum.org/): The browser based home for writing your first smart contracts.


## 📝 Week 0 Assignments
1. **Explainer:** Choose one concept (Hashing, Consensus, or Merkle Trees) and explain it to a 10 year old in your own words.
2. **The Ripple Effect:** Use the [Blockchain Demo](https://andersbrownworth.com/blockchain/blockchain). Change a piece of data in Block #2. What happens to Block #3, #4, and #5? Why?

- Submit in .md file in this format name-rollno-year.


## 📚 Recommended Resources
* **[Coinbase Learn (Crypto Basics)](https://www.coinbase.com/en-in/learn/crypto-basics)**: A massive library of beginner friendly guides on everything crypto.
* **[Ethereum.org Learn Hub](https://ethereum.org/en/learn/)**: The gold standard for documentation.
* **[Ledger Academy](https://www.ledger.com/academy)**: Great for clear, high level explainers on keys and security.
* **[EthHub](https://docs.ethhub.io/)**: Open source info on everything Ethereum.
* **[3Blue1Brown – How Does Bitcoin Actually Work?](https://www.youtube.com/watch?v=bBC-nXj3Ng4&t=1301s)**: An excellent visual explanation of how Bitcoin, blockchain, mining, and cryptographic trust work under the hood

*Good luck with Week 0! If you can wrap your head around these basics, the rest of the course will make much more sense.*
