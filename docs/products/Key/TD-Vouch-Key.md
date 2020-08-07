---
layout: default
title: VK Tech Design
nav_order: 222
parent: Vouch Key
grand_parent: Products
has_toc: true
---

## Vouch Key Design {#vouchkeydesign}

### SDK components

```{r dk-sdk-asset-device-component-diag, echo=FALSE}
knitr::include_graphics('diagrams/dk-sdk-asset-device-component.svg', dpi = NA)
```
```{r dk-sdk-mobile-device-component-diag, echo=FALSE}
knitr::include_graphics('diagrams/dk-sdk-user-device-component.svg', dpi = NA)
```

### Auth docs & Proofs model

```{r child = 'diagrams/auth-doc+proofs-model.Rmd'}
```

### Domain model

```{r domain-model-class-diag, echo=FALSE}
knitr::include_graphics('diagrams/domain-model-class.svg', dpi = NA)
```

### Use Cases

#### Self endorse user organization persona

```{r self-endorse-user-org-personas, echo=FALSE, out.width='100%'}
knitr::include_graphics('diagrams/self-endorse-user-org-personas.svg', dpi = NA)
```

The Vouch API provides a new uuid for each userOrgPersonas item to ensure a deterministic outcome on the blockchain,
but doesn't make a judgement which items are new or which ones already exist in the database.

The ABCI app will take on the responsibility to match the incoming
userOrgPersonas with the existing Personas in the database, and decide whether it's a match or not.

If the item cannot be matched with an existing Persona it will be added with the client provided uuid, otherwise the
uuid is not used and is discarded.

#### Download Authoritative doc pkg

```{r retrieve-user-persona-auth-doc-proof-pkg, echo=FALSE, out.width='100%'}
knitr::include_graphics('diagrams/retrieve-user-persona-auth-doc-proof-pkg.svg', dpi = NA)
```

#### Retrieve Block hash pkgs & Authoritative doc pkg

```{r retrieve-block-hash-pkgs-diag, echo=FALSE, out.width='100%'}
knitr::include_graphics('diagrams/retrieve-block-hash-pkgs.svg', dpi = NA)
```

`retrieveBlockHashPkgs` is invoked with `trustedBlockHashPpkg` and `authDocProofPkg` in order to retrieve the required
`blockHashPkg`s between the `height` of the known `trustedBlockHashPpkg` on the phone and the height of the `authDocProofPkg`.
The size `n` of the `blockHashPkg`s is either `1` or `> 1`; If no validator node changes occurred between the heights specified
only the so called `proof blockHashPkg` is returned at index `0`, else if `n > 1` it means that validator node changes did
occurr and these so called `intermediate blockHashPkg`s are returned between index `0` and `n-2`, with the `proof blockHashPkg`
at index `n-1`

All intermediate `blockHashPkgs` are stored so user devices can serve any (offline) downstream device.
The `proof blockHashPkg` is not stored as it has no value beyond authenticating the `proof` in the `authDocProofPkg`

The `currentBlockHeight` indicates which `intermediate blockHashPkgs` need to be sent before sending the `proof blockHashPkg`


#### Enroll Asset Device



