---
layout: default
title: PP - Vouch Admin App
parent: Product Proposals
grand_parent: Proposals
nav_order: 314
has_children: false
---
## Toyota Dealer Admin App Proposal

Key use cases for Admin App:

1. Dealer service technicians to install SKB, link to VIN and Test Operation of digital key.
2. Transfer Ownership to a customer (and revoke existing keys)
3. Fleet Management (movement within dealership by dealer staff with assigned role)
4. Share Access to an individual user - if not done at organization level
5. Revoke access to individual when shared
6. Sign in with existing dealer credentials (linked to Forgerock instance)
7. Send error logs if install fails (To be worked out still where and who gets these logs)
8. Change Vehicle. search by Vin (or scan) and switch to that vehicle for digital key control.

### Dealer user Login

Credentials will be stored on dealer instance of the Toyota ForgeRock Platfom.

Connection failure and Invalid Credentials also show here.

```{r 6a.1.1, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Sign In", fig.align = 'center', out.width = '30%'}
knitr::include_graphics("Design/SignIn-Active.png)
```

```{r 6a.1.2, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Sign In", fig.align = 'center', out.width = '30%'}
knitr::include_graphics("Design/SignIn-FAIL.png)
```

```{r 6a.1.3, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Sign In INVALID Account Information", fig.align = 'center', out.width = '30%'}
knitr::include_graphics("DesignSignIn-INVALID.png)
```

### Registration

After sign in, the dashboard screen should be presented.

A car based on VIN should be shown if there is an existing connection to a vehicle, otherwise a blank image should be shown

```{r 6a.2.1, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Sign In ", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/TAA/Dashboard.png")
```

```{r 6a.2.2, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Sign In ", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/TAA/Dashboard-No-Vehicle.png")
```

#### Registration Install Guide

Screen to offer install instructions wit offer to skip. If selected the instructions screen shopuld be presented, if not then onto next screen in the flow.

```{r 6a.3.1, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Install Guide Option", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Registration-Operations-Install-Guide-or-SKIP.png ")
```

```{r 6a.3.2, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Install Guide", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Registration-Operations-Install-Guide.png ")
```

#### Registration SKB Enter or Scan QR

This screen provides the option to scan the qr code on the SKB device or to manually enter the ID of the device.

```{r 6a.4.1, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Register SKB Scan or Enter ID", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Register-Scan-or-Enter-ID-Continue.png ")
```

If scan is selected, the scan function should be activated.

```{r 6a.4.2, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Register SKB Scan QR Code", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Registration-SKB-Scan.png ")
```

If a match is found, the match screen should be displayed indicating that.

```{r 6a.4.3, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Register SKB Found", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Registration-SKB-Found.png ")
```


#### Registration SKB - VIN Match

To pair the SKB device to a car, we need to link the VIN number to the SKB id.
This screen provides the option to scan the VIN on a car or to manually enter the ID of the device.

If manually entered, the continue button would appear highlighted

```{r 6a.5.1, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Register SKB - VIN", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Registration-Enter-VIN.png ")
```

If manually entered, the continue button would appear highlighted

```{r 6a.5.2, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Register SKB - Enter VIN", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Registration-VIN-Manual.png ")
```

If scan is chosen, we would activate the camera to scan VIN on the vehicle and perform search.

```{r 6a.5.3, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Register SKB - VIN Scan", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Registration-Vin-Scan.png ")
```

If VIN is found after manual entry or Scan then the below screen would be presented.

```{r 6a.5.4, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Register SKB - VIN Found", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Registration-VIN-Found.png ")
```

### Change Car

In order for dealer staff to be able to control vehicles via digital key, they need to switch cars by scanning or entering the vehicles VIN number.

from the dashboard, selecting Change car will start this process, or alternativly by selecting the dropdown from top middle of the screen where the current model is indicated.

```{r 6a.5.1, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Change Car", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/dashboard.png ")
```


#### Change Car - VIN Search

Here the user can either choose to enter (cut and paste maybe) a VIN for the car they want to control

or

choose to scan the VIN by pressing the scan button.

```{r 6a.10.1, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Register SKB - Enter VIN", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Change-car-Enter-VIN.png ")
```

If scan, we need to pop the VIN Scanner (this may be a plugin?)

```{r 6a.10.2, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Change Car - Scan VIN", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Change-car-Scan-Vin.png ")
```

If match is found then we should display the results.

If not found we should error and return to the Enter Vin choice screen.

```{r 6a.10.3, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Chnage Car - Found match", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Change-car-found.png ")
```


### Controls & Sharing

To operate the digital key, the control screen will allow the user to perform the following functions:

1. unlock Doors
2. Lock Doors
3. Unlock Trunk
4. Start/Stop Vehicle.


```{r 6a.6.1, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Controls", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Controls.png ")
```


####  Sharing

Dealers should be part of a role & organization that sharing is not needed but this functionality is worth adding if dealer want to add in someone not in their org.

Sharing is started by selecting the "share with" link on the controls screen and a list of pre used contacts (if any) will appear.

```{r 6a.6.1, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Contacts", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Sharing-Select-contact.png ")
```

If the contact is new then by pressing the "add contact"  button the screen will change to the local contact list for the user to select a contact on their device.

```{r 6a.6.2, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Add Contacts", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Contact-list.png ")
```

Once selected the contact now appears as selected in in the share key screen.

When "share key" is pressed a new key request is sent to that individual. If they do not already have the Admin App installed, it will direct them to do so by sending invite to their cell number via SMS and will automatically on-board them.

```{r 6a.6.3, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Share Key", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Sharing-SHARE.png ")
```

Once on-boarded they will receive a new key share request and the information fromt he sharer should be the dealers info.

```{r 6a.6.4, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Share Key Accept", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Sharing-ACCEPT.png ")
```

When the new driver accepts the key the owner/sharing party, then will be prompted to confirm the share, taking time to ensure the correct contact is accepting.


```{r 6a.6.5, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Share Key Confirm", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Sharing-CONFIRM.png ")
```

The app should now be redirected to the controls screen to allow control of the vehicle.

####  Revocation

If sharing is done on individual basis, we need to be able to revoke those keys individually also.

When a key is shared to a contact, selecting that contact will show dropdown option to revoke, which contains the Revoke button,

```{r 6a.7.1, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Revoke Dropdown", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Revoke-Key-Dropdown.png ")
```

pressing the Revoke button will revoke the key.

```{r 6a.7.2, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Revoke", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Revoke-Key-REVOKE-BUTTON.png ")
```

####  Ownership Transfer

Ownership transfer is almost identical to key sharing. SMS optional screen available also if we want to just type number in directly.

```{r 6a.8.1, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Transfer", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Transfer.png ")
```

```{r 6a.8.2, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Transfer Accept", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Transfer-ACCEPT.png ")
```

```{r 6a.8.3, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Transfer Confirm", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Transfer-CONFIRM.png ")
```

```{r 6a.8.4, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Transfer SMS", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/SMS.png ")
```

####  Notifications

Examples of notification types

```{r 6a.9.1, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Revoke Dropdown", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Notifications-Lock-Screen.png ")
```

```{r 6a.9.2, echo=FALSE, fig.retina=3, fig.cap="Toyota Admin App Revoke", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/TAA/Controls-Notifications.png ")
```

