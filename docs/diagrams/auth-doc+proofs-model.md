---
layout: default
title: Auth-doc and Proofs Model
nav_order: 901
parent: Diagrams
---

  
**authDocProofPkg**

```ruby
authDocProofPkg = [
    authDoc:                bstr,               ; auth doc (e.g. userPersonaAuthDoc) encoded with cbor
    k:                      bstr,               ; SMT key
    proof:                  bstr,               ; SMT compressed proof
    height:                 int,                ; block height
]
```

**userPersonaAuthDoc**
```ruby
userPersonaAuthDoc = [
    personaId:              bstr .size 16,      ; internal unique id of the persona
    personaIsRevoked:       bool,               ; flag which indicates whether the persona is revoked
    personaType:            tstr,               ; persona type. e.g. "skb-installer"
    userId:                 bstr .size 32,      ; sha256 digest of the auth server user id
    userDevicePubKey:       bstr .size 32,      ; user device sign pub key
]
```

**assetAccessAuthDoc**
```ruby
assetAccessAuthDoc = [
    assetAccessId:              bstr .size 16,      ; internal unique id of the asset access
    assetAccessIsRevoked:       bool,               ; flag which indicates whether the asset access is revoked
    assetAccessIssueDate:       timestamp,          ; timestamp which indicates when issued
    assetAccessValidStartDate:  timestamp,          ; timestamp which indicates start time of valid access
    assetAccessValidEndDate:    timestamp,          ; timestamp which indicates end time of valid access
    assetAccessPersonaType:     tstr,               ; persona type. e.g. "owner"
    assetMfgId:                 bstr,               ; the asset mfg id, the car vin
    userId:                     bstr .size 32,      ; sha256 digest of the auth server user id
    userDeviceSignPubKey:       bstr .size 32,      ; user device sign pub key
    entitlements:               [0* int],           ; array of enumerated entitlements
]
```

**blockHashPkg**
```ruby
blockHashPkg = [
    header: [
        version:               [
                                 block:  uint,
                                 app:    uint
                               ],
        chainId:               tstr .size (1..255),
        height:                int,
        time:                  timestamp,
        lastBlockId:           blockId,
        lastCommitHash:        bstr .size 32 / null,
        dataHash:              bstr .size 32 / null,
        validatorsHash:        bstr .size 32,
        nextValidatorsHash:    bstr .size 32,
        consensusHash:         bstr .size 32,
        appHash:               bstr / null,
        lastResultsHash:       bstr .size 32 / null,
        evidenceHash:          bstr .size 32 / null,
        proposerAddress:       bstr .size 20,
    ],
    commit: [
        height:                int,
        round:                 int,
        blockId:               blockId,
        signatures:            [ 1* [
                                      validatorAddress:  bstr .size 20,
                                      timestamp:         timestamp,
                                      signature:         bstr .size 64
                                    ]
                               ]
    ],
    ? nextValidators:            [ 0* [
                                      address:           bstr .size 20,
                                      pubKey:            bstr .size 32,
                                      votingPower:       uint
                                    ]
                               ]
]
blockId = [
  hash:    bstr .size 32,
  part:    [
             total:    uint,
             hash:     bstr .size 32
           ],
]
```

** Common definitions **

```ruby
timestamp = [seconds: int, nanoseconds: int]
```