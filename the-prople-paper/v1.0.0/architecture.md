|   Paper   |   Section |   Version |   Author  |   CreatedAt   |
|   ------- |   ------- |   ------  |   ------  |   ---------   |
|   [The Prople Paper](https://github.com/prople/paper/tree/main/the-prople-paper/v1.0.0)   |   `Architecture` | v1.0.0 | [rstlix0x0](https://github.com/rstlix0x0/) |    July, 23th, 2024  01:15 UTC

---

# Architecture

## Components

### Vessel: Personal Self Sovereign Agent & Wallet

`Prople Vessel` is a software which like a *container* that deployed in some server's environments, it can be a cloud or bare metal environment, or even deployed in *localhost* and use some tools, maybe like *ngrok* to make it reachable through the Internet.

> A `Vessel` should be able to deployed in any environments which able to reached through the Internet. It should not be like a *blockchain node* or *validator* that need a high level computation or expensive resource computation.

The `Vessel Daemon` that need to be deployed and run, will open a single port used to maintain `HTTP JSON-RPC API`. The `API` itself will have a functionalities to maintain:

- `Identity`
- `Connection`
- `Social`
- `Finance`

It choose the `JSON-RPC` as main protocol communication becaus its simplicty, no need to maintain multiple endpoints and its handlers, just a single enpdpoint that able to receive multiple commands.

> Each of an *actor* will may have multiple *vessels*, but a single *vessel* will only be owned by a single *actor*.

```mermaid
flowchart LR
    actor --> vessel_1
    actor --> vessel_2
    actor --> vessel_n
```

All communication between *actors* will have through their *vessels*, and the communication protocol used between *vessels* is via `JSON-RPC API`.

```mermaid
sequenceDiagram
    actor Alice
    participant AV as AliceVessel

    participant BV as BobVessel
    actor Bob

    Alice->>AV: send message to bob

    AV->>BV: forward message
    Note right of AV: JSON RPC API

    BV->>Bob: notify bob
    Bob->>BV: reply message
    
    BV->>AV: forward message 
    Note right of AV: JSON RPC API
    
    AV->>Alice: notify alice
```

#### Packages 

The `Vessel` codebase separated into multiple `Rust Packages`:

```mermaid
---
title: Prople Vessel Packages 
---
classDiagram
    direction RL

    class vessel-core
    vessel-core: +identity
    vessel-core: +connection
    vessel-core: +social
    vessel-core: +finance

    namespace external {
        class prople-did
        class prople-crypto
    }

    vessel-core <.. vessel-rpc : depends    
    vessel-rpc <-- vessel-cli : manage 
    vessel-rpc <-- vesseld : use

    prople-did <.. vessel-core : depends
    prople-crypto <.. prople-did : depends
```

Internal packages:

- `vessel-core`: It's a core domain abstractions which provides all domain logics
- `vessel-rpc` : It's an RPC handlers and also persistent storage
- `vessel-cli` : It's a command-line utility used to communicate with the *actor vessel*
- `vesseld` : It's a *vessel daemon* or binary application that will be deployed and executed in some environments 

External packages:

- `prople/did` : It's a package build to modeling the `DID`
- `prople/crypto` : It's a package used to manage cryptography algorithms 

#### Cryptography

There are two important needs for the *cryptography* :

- Key exchanges
- Digital signatures

The cryptography at the `prople/crypto` designed specifically only for `Prople Ecosystem`. There are multiple algorithms used:

- `ECDH`: Used to generate *keypairs* (public and private keys), to establish a *shared secret key*
- `EdDSA`: It's a digital signature scheme, which will be used as the *unique identifier*
- `Blake3`: Used for a *hash function*
- `Chacha20-Poly1305`: It's a `AEAD (Authenticated Encryption with Additional Data)` algorithm
- `Base58`: Used for encoding format

---

The *key exchanges* will be used to create a secure channel of communication between *actors*.

There are two kind of *connections* :

- Public connection
- Private connection

For an *actor* to be able to connected and share *private messages*, they have to be *connected*. This special connection, means they need to exchange their *ECDH public keys*. These keys will be used to generate the *shared secret key*, which is a combination between private keys and public keys from others. Once this *secret keys* generated, their next communication will be formed in the *encrypted messages*. [^1] 

This kind of algorithms used through the `DIDComm` standard.

> DIDComm uses DIDs (Decentralized Identifiers) to establish confidential, ongoing connections, without the need for usernames and passwords.
>
> DIDComm protocols enable trusted interactions between parties [^2][^3]

---

The `EdDSA` algorithm used for two cases:

- Message digital signatures
- Identity unique identifiers

The algorithm behind the *unique identifiers*:

```
eddsa::KeyPair -> get publicKey -> hash: SHA3 -> hash: Blake3 -> multibase: Base58Btc 
```

This algorithm actually follow what `Bitcoin` when generate the *address*, but using different hashing algorithms. 

|   Bitcoin |   Prople  |
|   ------- |   ------  |
|   `SHA256` & `RIPEMD` |   `SHA3` & `BLAKE3`   |

[^1]: https://en.wikipedia.org/wiki/Elliptic-curve_Diffie%E2%80%93Hellman
[^2]: https://didcomm.org/
[^3]: https://identity.foundation/didcomm-messaging/spec/v2.1/
---

> [The Prople Paper: Architecture](https://github.com/prople/paper/blob/main/the-prople-paper/v1.0.0/architecture.md) © 2024 by [rstlix0x0](https://github.com/rstlix0x0/) is licensed under [Creative Commons Attribution-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/?ref=chooser-v1) 
