---
layout: default
title: Domain Model Class
nav_order: 903
parent: Diagrams
---

@startmermaid
classDiagram
    class User
    User: +id String
    User: +email String
    User: +phoneNr String
    User: +personas List~Persona~
    User: +devices List~Device~
    Persona <|-- UserOrgPersona
    Persona <|-- UserAssetPersona
    Persona <|-- OrgAssetPersona
    class Persona
    Persona: +id String
    Persona: +active? boolean
    Persona: +type String  %% e.g. skb-installer
    class UserOrgPersona
    UserOrgPersona: +user User
    UserOrgPersona: +org Organization
    class UserAssetPersona
    UserAssetPersona: +user User
    UserAssetPersona: +asset Asset
    class OrgAssetPersona
    OrgAssetPersona: +org Organization
    OrgAssetPersona: +asset Asset
    class Organization
    Organization: +id String
    class Asset
    Asset: +id String
    Asset: +devices List~Device~
    Device <|-- UserDevice
    Device <|-- AssetDevice
    class Device
    Device: +id String
    Device: +pubKey String %% multi-key representation
    class UserDevice
    UserDevice: +user User
    class AssetDevice
    AssetDevice: +asset Asset
    AssetDevice: +manufacturer-ref String  %% "this is the serial nr / device id as set by the manufacturer"
@endmermaid
