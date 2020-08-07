---
layout: default
title: VI Tech Design
nav_order: 212
parent: Vouch Identity
grand_parent: Products
has_toc: true
---

# Product Technical Design

## Vouch Identity

### SDK components

```{r di-sdk-component-diag2, echo=FALSE}
knitr::include_graphics('diagrams/di-sdk-component.svg', dpi = NA)
```

### Use Cases

#### Enroll User Device with OIDC

The tenant app uses the sdk to enroll the user device in the Digital Identity Platorm.

The OIDC id token is used as proof, retaining the existing
registration procedures with verification mechanisms that the customer has in place today.

The OIDC id token must contain `sub`, `phone_number` and `phone_number_verified` claims
with `email`, `email_verified` claims being optional.

```{r enrollment-oidc-diag, echo=FALSE}
knitr::include_graphics('diagrams/enrollment-oidc.svg', dpi = NA)
```

#### Self Endorse User Organization Personas

The tenant app uses the sdk to endorse the enrolled user in the Digital Key platfrom
with the relevant personas within the context of that organization.

The OIDC id token is used a proof, it must contain `orgId` and `userOrgPersona`
claims which indicate which organization the user
 is member of, and what personas the user exercises within that organization.

```{r self-endorse-user-org-personas-diag, echo=FALSE}
knitr::include_graphics('diagrams/self-endorse-user-org-personas.svg', dpi = NA)
```