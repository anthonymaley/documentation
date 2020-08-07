---
layout: default
title: VI - Client SDK
nav_order: 213
parent: Vouch Identity
grand_parent: Products
has_toc: false
---



# Client SDK Architecture

## Background

As Vouch Zero Password (VZP) and related user facing mobile products need to run
on both Android and iOS, React Native was selected as a key technology to
decrease time to delivery. During the development of VZP it became clear that
there was a significant amount business logic that could be decoupled from UI
concerns. This code evolved into a library - vouch-mobile-shared.

Testing iOS and Android applications remained challenging. At the time there
was no clear solution, so it was decided that we would benefit from at least
testing the business logic and the basic flows. This was done by decoupling
vouch-mobile-shared even further.

While vouch-mobile-shared was mostly business logic, certain facilities like
HTTP and crypto had to be provided by a "host" environment. These integration points
were teased apart so that compatible features from a Node.js environment could
be used instead. This lead to a integration test repo, vzp-test which could test
the business logic separately from UI concerns.

But some coupling still remained, and starting with the development of the
Digital Key SDK, we fully separated the SDK from vouch-mobile-shared. By
doing so, the SDK which can be embedded in Android or iOS, and we embed it just
like our customers would in more full feature UI products. That is, we dogfood 
our own SDK, our usage no more privileged than a customer's.

## Structure

The SDK is written as ClojureScript library. On Android it runs in an instance
of the Google V8 JavaScript engine. On iOS it runs in an instance of WebKit's
JavaScriptCore. However, consumers of the SDK are protected from the details as
we supply a Objective-C/Swift facade and a Java facade that represents the
official SDK api.

By doing so we can develop a feature in the SDK *once*. Then for each platform
we only need to modify the facade.

Note this means that when we consume it from a React Native application, we treat
the SDK just as our customer would - an Objective-C library or a Android library
as the case may be.

A close reader may note that React Native itself uses V8 and JavaScriptCore and
wonder whether our SDK might create issues. In all cases we run in our own JS
engine instance separate from any other JS engine instance a customer
or ourselves might use. Again, our consumption of the SDK is identical to a
customers - it's just an iOS/Android library. The fact that the SDK is written
in ClojureScript and uses a JS engine is a hidden implementation detail.

## Benefits

Vouch Zero Password and related applications are customer facing security
products. This means a fair amount of subtle cryptographic business logic in the
software. In the past, this business logic would be duplicated between
Objective-C and Java. At the time this was viewed as expedient towards the goal
of a minimally viable product. 

However, over time it became clear that specification changes came with relative
frequency and this would require changes in two different code bases.
Specification changes to security oriented applications would often involve
subtle changes to hashing, cryptographic functions, and the steps to complete a
flow. In actuality making a subtle change twice meant debugging a subtle
change twice. Time and time again this would require a surprising amount
of effort for what appeared to be a small specification change.

In the new approach, we instead write all critical business logic of the
application once in ClojureScript. This means that changes to our specification
need only be tested once, and we can be more confident that our
applications will behave the same regardless of the host platform.

Platform specific code then remains in only two areas, and the effort remains
reasonable as these areas are generally tangential to the critical
specifications. One is providing a platform idiomatic API, that is something
that Objective-C/Swift and Java developers find natural to program against. The
other is writing simple host platform integrations for features not available to
pure JavaScript environments. This is covered in more detail in the following
section.

## Considerations for Feature Development

The above approach is not without tradeoffs. The Google V8 and JavaScriptCore
are "pure" - that is they have no expectation about their embedding and thus
have no features which are not covered in the JavaScript language specification.
There is no `XmlHttpRequest`, no DOM, and no `setTimeout`. So while it is true
that we can develop features quickly, this is somewhat dependent on the what
underlying facilities these features might need.

We have already written platform specific integrations to cryptographic utilites
as well as HTTP. But if for example we would need Server Sent Events (SSE) or
WebSockets, we would need to find suitable supporting libraries for Objective-C
and Java and expose that to the SDK.

Note that this is not actually different from what we would have to do if we
maintained two separate code bases, one for iOS and Android. But it clarifies
the point that the above strategy does not alleviate effort when some feature
requires some platform functionality we don't currently leverage.

## Testing Redux

It now appears that we may be able to do end-to-end testing directly with iOS
and Android emulators via GitHub actions. This is currently being investigated.