---
layout: default
title: Reversing Sherlock
nav_order: 80
parent: Blogs
has_children: false
has_toc: false
---
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

# Reversing Sherlock

## We where waiting for Sherlock, an insight into how we tried to avoid being Sherlock-ed by Apple.

We knew about Apple/BMW announcement, we knew the detail of the specification for CCC and we knew how our product complimented it while delivering digital access for the entire Vehicle OEM lifecycle, and not just the keys in a wallet approach that focusses on individual car owners that was announced today. We designed our product to be flexible with the ability to augment what companies have already, while giving us the ability to change direction based on market conditions and available technologies. We knew all this BUT we where still waiting for Sherlock ... will apple manage to do something magical that we couldn’t predict and Sherlock our product?

### An Insight into building products that Apple could Sherlock.

From the first day I used an Apple Macintosh I was hooked, the design, the products, the quality, the attitude, everything made sense and matched my expectations of how products should be, I’ve used their product to this day. It’s quite unusual to be on the other side of the fence, as a product creator, building using my own and the teams beliefs and principles but also both consciously and unconsciously influenced by product experiences shaped by being consumers of their products. Trying to predict where they will go and make sure our product compliments and not competes has been challenging but incredibly exciting.

Turns out, on this occasion, Sherlock was busy elsewhere are we are now in a great place to ride the waves that the Apple/BMW announcement will make.

Apple has done what it should, they focused on delivering a consumer only experience specific to their platforms. This is as we would expect them to do and keep the door open for our company and others to deliver a broader, full lifecycle based product. We all win.

### So what did Apple/BWM announce and what makes our product, Vouch Key Automotive, different?

#### Apple shared the following features in a super slick overview.

1. NFC based unlock and NFC based start stop.
    2. Sharing over iMessage/wallet
3. Ultra Wideband technology support for proximity unlock


#### Here is how we compare:

|| __Apple__| __Vouch__|
| :-:| :------| :------|
| 1 | __NFC based unlock__\ NFC is required both in the smartphone and in the handle of the car, this is a good feature to allow for flat battery devices still to be usable. It does require constant use of the phone to hold against the door. | __NFC / Ultra Wideband / BLE unlock__\ Vouch Key support multiple different protocols and standards to provide a friction free experience, NFC for backup, should your device be drained but otherwise we can use UWB to unlock the car on approach, either from your phone or a fob.
| 2 | __NFC based start/ stop__\  It requires the driver to place phone in the 'special' location in the car to allow it to be started. everytime. I imagine this will get old quickly. | __NFC / LF/RF / CAN / UWB Start Stop__\  UWB will allow for detection of phone/watch/fob in the driver seat or car, we can also use other OEM methods, like CAN IDs to embed into the app to start/stop | |
| 3 | __Sharing over iMessage/wallet with permissions__ \  While this is a nice feature it does ha security risks attached, namely how do you know it went to the correct person? They may be in your contacts for close friends and family but for a new share, getting the number wrong is a possibility. | __Sharing over iMessege / In App Sharing / WhatsApp etc__ Our sharing can be done over iMessage, it does require an identity for the user to be associated in the OEM application, i.e. BMW would have an app that would on-board the friend instantly and the sharing process would have an inline visual confirmation step to ensure the correct person received the key |
| 4 | __Ultra Wideband technology support for proximity unlock__ This is the game changer, it will require a phone with the UWB chip, so a good reason to buy the iPhone 12 i would guess | __Ultra Wideband technology support for proximity unlock__ We offer this now but only via a fob, this is useful for valet or service technicians etc, we fully expect to leverage the UWB inside phones as they become available to us.|

__So, this shows our product can do all and more in what apple demonstrated. Vouch Key can also do all of this now and more as i will outline below:__

#### What they did not demonstrate.

Importantly, they did not demo all aspects of a digital key product, this is probably due to the limitations of the CCC specifications not having a full range of lifecycle capabilites at this stage.

|| __Apple__| __Vouch__|
| :-:| :------| :------|
| 1 | __Apple Watch Control__\ Not Shown |  __Apple Watch Control__\ This is a major gap, we believe wearables will be the window into operating your car digitally, not the phone itself. Our product allows for operation of the car from the watch but more importantly we use the watch to surface the interactions, like confirmation of lock when you walk away, or a quick prompt to ask for permission, ot a quick way to check status of the vehicle.
| 2 | __Organization Usage__\ Not available. CCC does not support this. | __Organization Usage__\  at its heart Vouch Key is an identity platform, so we can provide access to all cars to an individual, group or entire organization. This provides use case coverage for manufacturer staff in plants, logistics partners, dealer fleet management as well as rental and car sharing. | |
| 3 | __Other Key Standards than CCC__ Not Possible | __Other Key Standards than CCC__  Vouch can be the central key/access platform and link to many different standards for keys, for example we have our own key technology but we can also link to CCC or other standards, this allows manufacturers to build the back end systems for sharing, revocation, key management, owner identity, Rental integration, 3rd party delivery etc. just once. |
| 4 | __Remote Offline Sharing__ not possible, each driver needs to pair physically with the nfc module in the car before it will work, there is a PIN shown on the head unit and that needs to be entered into the phone to pair  | __Renote Offline Sharing__   | with Vouch Key, we can remotley share access to the vehicle without access to the vehicle required. When the driver approaches the car the new key will just work automatically. No PIN code sequences or other special pairing required.
| 4 | __Car manufacturer relationship with driver__ not possible | __Car manufacturer relationship with driver__  We believe that the car manufacturer needs to have a direct relationship with the car owner, especially when it comes to security and privacy. Vouch allows the OEM to have thier own app and offer a full experience to their customers, which a key is just part of. Establishing a secure identity and linking that identity to phones, watches and cars can really drive innovative experiences that the OEM should be able to offer. |


Our product is focused on the entire manufacturing, logistics, sales and fleet management as well as providing an amazing experience to the car owners and drivers.  Apple customers (and soon Google and Samsung) will be keen to add their car keys to their apple wallets and this will pressurize vehicle manufacturers to support the CCC standard to allow this. However, it will only be possible for cars equipped with the latest ECU hardware and those models will be in short supply for a good while. Our product, while it can work with ECU based solutions, can also be used in an aftermarket situation. We can either provide the hardware or leverage existing hardware to allow our solution to work.

Perhaps the biggest difference is the identity aspect of our solution, we can securely establish and link the identity of the driver to each vehicle and we can do that at many levels, individuals, roles and entire organizations, this allows us not only assert the owner of a vehicle but also roles (service technicians, valets, 3rd party delivery) and even organization (entire dealerships, rental companies, fleet, logistics etc)

We also design and build our own ECU and IoT hardware so that we can offer an end-to-end service to our clients, this also allows us to drive features, just like apple do, based on the hardware innovations available to us in the market. One of those is Ultra Wideband (UWB) which Apple are pushing heavily for the iPhone 12 and the car key.  Our product already supports this but without the hardware support in smartphones, we have had to build our own hardware fobs to demo that capability, while we wait for the UWB support in smartphones.  You can see more of our work on UWB here (link to mikes blog)

### How it links to CCC….

OEMs will be required to stand-up CCC compatible secure infrastructure that Apple/Google/Samsung can connect with to establish the key for each owner but beyond that OEMs will be unable to leverage this for their own or 3rd party uses (rental, fleet, direct to customer).  Our solution will allow OEMs to implement one single digital access/key platform and then use that across all areas, while still be able to link the CCC users to this same platform.  This allows OEMs to offer both options to customers and not be beholding to Apple/Google/Samsung to provide the features and experience.

### Sherlock, until the next time...

So, we managed to avoid Sherlock this time around and we hope to have a successful product launch. This annoucement has provided us with education to the world on what a digital key is and can do, it will make it easier for us to position our product to companies on the back of it and we believe Vouch Key is positioned well to be a very successful product.

Vouch.io is a product company, based in Atlanta GA. 

All product enquires should be directed to hello@vouch.io

Find out more at https://vouch.io/
