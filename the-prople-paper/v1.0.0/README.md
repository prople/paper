# Overview

`The Prople Paper` is a paper build to give people a clear insight about the `Prople` from its a general ideas, concepts into high-level architecture designs. This paper will contains:

- Introduce a concept of `Personalization Platform`
- Introduce a concept of `Prople Platform`

The primary objective from sharing this paper is to invite people who has a same mission and vision, to join and contribute to this project.

---

> All of the described contents at this version (`v1.0.0`) has a chance to be changed again in the next version 

## Table of Contents

1. [Abstract](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/abstract.md)
2. [Introduction](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/introduction.md)
3. [Background](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/background.md)
    - [The Evolution of Web](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/background.md#the-evolution-of-web-read---write---own)
        - [Web1](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/background.md#web1---read)
        - [Web2](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/background.md#web2---write)
        - [Web3](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/background.md#web3---own)
    - [Related Projects - Decentralized Movements](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/background.md#related-projects---decentralized-movements)
        - [SolidProject](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/background.md#solidproject)
        - [AT Protocol & BlueSky](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/background.md#at-protocol--bluesky)
        - [Mastodon](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/background.md#mastodon)
        - [Lens Protocol](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/background.md#lens-protocol)
    - [Evaluation](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/background.md#evaluation)
        - [The Open Standards](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/background.md#the-open-standards)
        - [The Chain Abstraction & Network Interoperability](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/background.md#the-chain-abstractions--network-interoperability)
    - [Prople Solutions](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/background.md#prople-solutions)
4. [Personalization](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/personalization.md)
    - [Overview](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/personalization.md#overview)
        - [The Raise Of Cryptography](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/personalization.md#the-raise-of-cryptography)
        - [The Raise Of Decentralized and P2P Networks](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/personalization.md#the-raise-of-decentralized-and-p2p-networks)
        - [Prople: The Personalization Platform](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/personalization.md#prople-the-personalization-platforms)
    - [Core Domains](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/personalization.md#core-domains)
        - [Identity](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/personalization.md#identity)
            - [DID](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/personalization.md#did-decentralized-identity)
            - [SSI](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/personalization.md#ssi-self-sovereign-identity)
        - [Social](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/personalization.md#social)
            - [ActivityPub](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/personalization.md#activitypub)
            - [Matrix Protocol](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/personalization.md#matrix-protocol)
        - [Finance](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/personalization.md#finance)
            - [Public Blockchain Network](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/personalization.md#public-blockchain-network)
            - [Sovereign Crypto Wallet](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/personalization.md#sovereign-crypto-wallet)
5. [Architecture](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/architecture.md)
    - [Principles](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/architecture.md#principles)
    - [Components](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/architecture.md#components)
        - [Vessel: Personal Self Sovereign Agent & Wallet](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/architecture.md#vessel-personal-self-sovereign-agent--wallet)
            - [Packages](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/architecture.md#packages)
            - [Cryptography](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/architecture.md#cryptography)
        - [VSP: Vessel Service Provider](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/architecture.md#vsp-vessel-service-provider)
            - [Example Use Cases](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/architecture.md#example-use-cases)
        - [Vessel Webhooks](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/architecture.md#vessel-webhooks)