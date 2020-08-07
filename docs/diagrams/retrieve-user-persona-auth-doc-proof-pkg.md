---
layout: default
title: retrieve-user-persona-auth-doc-proof-pkg
nav_order: 902
parent: Diagrams
---
@startmermaid
sequenceDiagram
    participant APP as Tenant App
    participant DKMSDK as DK Mobile SDK
    participant DKAPI as DK API
    participant DKT as DK Tendermint
    participant DKABCI as DK ABCI App
    participant DKDD as DK Datom Database
    participant DKMT as DK Merkle Tree
    participant DKDSDK as DK Device SDK
    APP->>+DKMSDK: invoke `retrieveUserPersonaAuthDocProofPkg` with `userId`, `orgId` and `personaType`
    DKMSDK->>+DKAPI: signed request to `retrieveUserPersonaAuthDocProofPkg` endpoint with `userId`, `orgId` and `personaType`
    loop until `authDocProofPkg` is composed
        DKAPI->>DKDD: query for `Persona` using `request body attributes
        Note over DKABCI,DKDD: find user with `device-id equal` to `public-key` hash, and given `user-id`, then try to find within that user a Persona for given org and persona-type
        DKAPI->>DKMT: init tree with annotated root hash and lookup `userPersonaAuthDoc` + proof with key `persona/id` of found `Persona`
        alt if `userPersonaAuthDoc` found
                DKAPI->>DKAPI: compose `authDocProofPkg` with `auth-doc` set to `userPersonaAuthDoc`, `key`, `proof` and `height`
            else
               DKAPI->>+DKT: broadcast tx with signed request body encoded into `tx` param
               Note right of DKT: broadcast_tx_commit can be used to keep things simple while investigating broadcast_tx_sync
               DKT->>DKABCI: beginBlock
               DKT->>DKABCI: deliverTx
               DKABCI->>DKABCI: decode `tx` param and verify request signature for user
               DKABCI->>DKDD: query for `Persona` using `Data` param attributes
               DKABCI->>DKMT: compose flattened `userPersonaAuthDoc` from found Persona, serialize with cbor lib and store
               DKABCI->>DKT: return deliverTx ok response
               DKT->>DKABCI: Commit
               DKT->>-DKAPI: pass through broadcast tx response
        end
    end
    DKAPI->>-DKMSDK: serialise `authDocProofPkg` with cbor and return
@endmermaid
 