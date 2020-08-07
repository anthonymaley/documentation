---
layout: default
title: PP - Vouch Key App
parent: Product Proposals
grand_parent: Proposals
nav_order: 312
has_children: false
---
## Vouch Key Automotive App Proposal

To make our product viable for July sales and October usage, we need to design and build the Vouch Key application.

The following screens illustrate (roughly) how the app should operate and what the functionality should be.

This is still **draft** at present and through conversation as a team we can define and agree these features in detail.

### Splash Screen

To be shown on app launch after install or restart of application only.

```{r 6.1.1, echo=FALSE, fig.retina=3, fig.cap="Vouch Automotive Key Splash Screen", fig.align = 'center', out.width = '30%'}
knitr::include_graphics("Design/AK/Splash.png")
```

### SMS Invite

This functionality remains the same.

```{r 6.2.1, echo=FALSE, fig.retina=3, fig.cap="Vouch Automotive Key SMS Invite", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/AK/Invite.png")
```

### SMS On-boarding

These screens are Identical to the existing app and the functionality remains the same also.

```{r 6.3.1, echo=FALSE, fig.retina=3, fig.cap="Vouch Automotive Key SMS On-boarding", fig.align = 'center', out.width = '250%'}
knitr::include_graphics("Design/Ak/Sms.png")
```


### Home Screen / Main Navigation

This screen should be limited to immediate functions to allow for instant control of the car.

__Critical functionality__

- Car selection: Ability to see which car is currently selected and a obvious and frictionless way to change car quickly. Swipe right to left on the image should bring in the next car and from there swipe left to right should take you back to previous.

- Car status: Status of car locked or unlocked state should be immediately obvious to the user, the ability to quickly change that state should also be obvious and instant. If the car is out of range, this should be reflected too.

- Start | Stop: When we have UWB connected car, we can surface the start | stop to the driver or when inside the car only. Most use cases right now however will not have UWB so just like lock | unlock, we should surface state and function to change state for Start | Stop.

- Navigation to second level functions:  Navigation to Sharing, detailed controls and Profile/account should be obvious but abstracted from main screen functionality.


```{r 6.5.1, echo=FALSE, fig.retina=3, fig.cap="Vouch Key Automotive Home Screen", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/AK/Home.png")
```

### Profile | Account | Preferences Screen(s)

__Profile | Account:__

The profile/account function should allow the user to perform the following actions.

- Update Account Information
    - Name
    - Email
    - Cell Number

- Add Car

- Remove Car

- Transfer Ownership

- Suspend Car / Report Stolen: This should disable all keys until owner reactivates

- Reactive Car: Should reactivate car after it has been suspended.

- Delete Account: Delete Vouch account

```{r 6.6.1, echo=FALSE, fig.retina=3, fig.cap="Vouch Automotive Key Profile", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/AK/Profile.png")
```

__Preferences:__

- Edit Driving Profile: Idea that eventually this can allow for head unit integration and set preferences via a profile. Bluetooth preferences, navigation favourites, seat position etc can be set this way. Link to capable head unit requuired.

- Priority Preferences: Choose which priority phones should be connected to car when multiple are detected. UWB feature that can detect driver vs passenger and then choose based on preference which key / profile to use for head unit profile etc.

Distance unlock/lock settings: UWB feature that will allow for setting of distance to allow unlock to happen. Also automated lock preferences - distance to auto lock or send notification to driver to lock.


```{r 6.6.2, echo=FALSE, fig.retina=3, fig.cap="Vouch Automotive Key Preferences", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/AK/Preferences.png")
```

### Access Sharing

Showcase feature of the product and our platform. Sharing allows for secure and frictionless sharing cross platform remotley. Sharing should start by selecting the car or by driving it from the car image/screen. Should be obvious what car is been shared.

### Initial Sharing

The initial sharing screen should allow the user to select existing contact or add a new one.

```{r 6.7.1, echo=FALSE, fig.retina=3, fig.cap="Vouch Automotive Key Sharing", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/AK/Sharing.png")
```
### Set Options

This screen will offer options to select which access privileges to share and whether or not they can re-share.

```{r 6.7.2.1, echo=FALSE, fig.retina=3, fig.cap="Vouch Automotive Key Sharing Options", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/AK/Sharing2.png")
```
```{r 6.7.2.2, echo=FALSE, fig.retina=3, fig.cap="Vouch Automotive Key Sharing Options Choice", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/AK/Sharing3.png")
```
### Set Date Range

This screen will allow a start and end date range to be set. Access should not be possible outside of these dates.

```{r 6.7.3, echo=FALSE, fig.retina=3, fig.cap="Vouch Automotive Key Sharing Date Range", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/AK/Sharing5.png")
```

### Revoke Access Share

This feature should revoke a shared access grant.

```{r 6.7.4, echo=FALSE, fig.retina=3, fig.cap="Vouch Automotive Key Sharing Revoke", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/AK/Sharing4.png")
```

## Control Screen

__Extended Controls__

This screen should be like a dashboard that has controls for every function that the key can operate. This will be based on OEM and Model type.

All controls should reflect current state and toggle press should change that state and be reflected in UI.

```{r 6.7.4, echo=FALSE, fig.retina=3, fig.cap="Vouch Automotive Key Controls", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/AK/Controls.png")
```


### Other Capabilities that need discussion

### History

If its possible we should list out the last X uses of the Key.

```{r 6.8.1, echo=FALSE, fig.retina=3, fig.cap="Vouch Automotive Key History", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/AK/History.png")
```


### Add device - __NOT SURE IF NEEDED - CAN WE JUST ENROLL ON EACH DEVICE?__

  This should allow the user to add another device (2nd phone or iPad) or pair a wearable device (apple watch etc)

  ```{r 6.9.1.1, echo=FALSE, fig.retina=3, fig.cap="Vouch Identity Add Device", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/AK/Adddevice1.png")
```
```{r 6.9.1.2, echo=FALSE, fig.retina=3, fig.cap="Vouch Identity Add Device", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/AK/Adddevice2.png")
```


### Apple Watch Approval

In a similar way to how Apple levarage the Apple Watch to authenticate access, i would like to mirror this capability for Vouch.

This would be active if watch is active and paired to device with Vouch installed and would prompt user for watch approval over a prompt on the device as a priority.

```{r 6.4.1, echo=FALSE, fig.retina=3, fig.cap="Vouch Identity Apple Watch Approval", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Design/AK/Watch.png")
```



