---
title: Set up HoloLens in a commercial environment
description: Learn more about deploying and managing HoloLens in enterprise environments.
ms.prod: hololens
ms.sitesec: library
ms.assetid: 88bf50aa-0bac-4142-afa4-20b37c013001
author: scooley
ms.author: scooley
ms.topic: article
ms.localizationpriority: medium
ms.date: 07/15/2019
---

# Deploy HoloLens in a commercial environment

You can deploy and configure HoloLens at scale in a commercial setting.  This article provides instructions for deploying HoloLens devices in a commercial environment. This guide assumes basic familiarity with HoloLens. Follow the [get started guide](hololens1-setup.md) to set up HoloLens for the first time.

## Overview of Deployment Steps

1. [Determine what features you need](hololens-requirements.md#step-1-determine-what-you-need)
1. [Determine what licenses you need](hololens-licenses-requirements.md)
1. [Configure your network for HoloLens](hololens-commercial-infrastructure.md).
    1. This section includes bandwidth requirements, URL and Ports that need to be whitelisted on your firewall, Azure AD guidance, Mobile Device Management Guidance, app deployment/management guidance, and certificate guidance.
1. (Optional) [Configure HoloLens using a provisioning package](hololens-provisioning.md)
1. [Enroll Device](hololens-enroll-mdm.md)
1. [Set up ring based updates for HoloLens](hololens-updates.md)
1. [Enable Bitlocker device encryption for HoloLens](hololens-encryption.md)

## Step 1. Determine what you need

Before deploying the HoloLens in your environment, it is important to first determine what features, apps, and type of identities are needed.

### Type of Features

Your feature requirements will determine which HoloLens you need. One popular feature that we see deployed in customer environments frequently is Kiosk Mode. A list of HoloLens key features, and the editions of HoloLens that support them, can be found [here](hololens-commercial-features.md).

**What is Kiosk Mode?**

Kiosk mode is a way to restrict the apps that a user has access to. This means that users will only be allowed to access certain apps.

**What Kiosk Mode do I require?**

There are two types of Kiosk Modes: Single app and multi-app. Single app kiosk mode allows user to only access one app while multi-app kiosk mode allows users to access multiple specified apps. To determine which kiosk mode is right for your corporation, the following two questions need to be answered:

1. **Do different users who are require different experiences/restrictions?** Example, User A is a field service engineer who only needs access to Remote Assist. User B is a trainee who only needs access to guides… etc.
    1. If yes, you will require the following:
        1. Azure AD Accounts as the method of signing into the devices.
        1. Multi-app kiosk mode.
    1. If no, continue to question two
1. **Do you require a multi-app experience?**
    1. If yes, Multi-app kiosk is mode is needed
    1. If your answer to question 1 and 2 are both no, Single-app kiosk mode can be used

**How to set up Kiosk Mode**

There are two main ways ([provisioning packages](hololens-kiosk.md#set-up-kiosk-mode-using-a-provisioning-package-windows-10-version-1803) and [MDM](hololens-kiosk.md#set-up-kiosk-mode-using-microsoft-intune-or-mdm-windows-10-version-1803)) to deploy kiosk mode for HoloLens. These options will be discussed later in the document; however, you can use the links above to jump to the respective sections in this doc.

### Apps

This deployment guide will cover the following types of apps:

1. Remote Assist
2. Guides
3. Customer Apps

Each step in this document will include instructions for each specific app.

### Type of identity

Determine the type of identity that will be used to sign into the device.

1. **Local Accounts:** This account is local to the device (like a local admin account on a windows PC). This will allow only 1 user to log into the device.
2. **MSA:** This will be a personal account (like outlook, hotmail, gmail, yahoo, etc.) This will allow only 1 user to log into the device.
3. **Azure Active Directory (Azure AD) accounts:** This is an account created in Azure AD. This grants your corporation the ability to manage the HoloLens device. This will allow multiple users to log into the HoloLens 1st Gen Commercial Suite/the HoloLens 2 device.

### Determine your enrollment method

1. Bulk enrollment with a security token in a provisioning package.  
  Pros: this is the most automated approach  
  Cons: takes initial server-side setup  
1. Auto-enroll on user sign in.  
  Pros: easiest approach  
  Cons: users will need to complete set up after the provisioning package has been applied
1. _not recommended_ - Manually enroll post-setup.  
  Pros: possible to enroll after set up  
  Cons: most manual approach and devices aren't centrally manageable until they're manually enrolled.

  More information can be found [here](hololens-enroll-mdm.md)

### Determine if you need a provisioning package

There are two methods to configure a HoloLens device (Provisioning packages and MDMs). We suggest using your MDM to configure you HoloLens device, however, there are some scenarios where using a provisioning package is the better choice:

1. You want to skip the Out of Box Experience (OOBE)
1. You are having trouble deploying certificate in a complex network. The majority of the time you can deploy certificates using MDM (even in complex environments). However, some scenarios require certificates to be deployed through the provisioning package.

## Next Step: [Determine what licenses you need](hololens-licenses-requirements.md)

## Get support

Get support through the Microsoft support site.

[File a support request](https://support.microsoft.com/supportforbusiness/productselection?sapid=e9391227-fa6d-927b-0fff-f96288631b8f).