---
title: Overview of PowerShell for Azure Information Protection| Microsoft Docs
description: An introduction to the PowerShell modules that you can use with Azure Information Protection.
services: azure
author: batamig
manager: rkarlin
ms.product: information-protection
ms.service: information-protection
ms.devlang: powershell
ms.topic: reference
ms.date: 10/14/2020
ms.author: bagol
---

# Azure Information Protection

Use the following PowerShell modules with Azure Information Protection: 

- **[AIPService](#aipservice).** Used to administer Azure Information Protection's Azure Rights Management protection service, and replaces the deprecated [AADRM](#aadrm) module.

- **[AzureInformationProtection](#azureinformationprotection).** Used to support Azure Information Protection client functionality.



## AIPService
    
These cmdlets let you administer the Azure Rights Management protection service for Azure Information Protection. 

The AIPService module replaces the older module, [AADRM](#aadrm).

For more information about when to use these PowerShell cmdlets and to see groupings of cmdlets by administration tasks, see [Administering protection from Azure Information Protection by using PowerShell](/information-protection/deploy-use/administer-powershell).
    
For upgrading and installation instructions, see [Installing the AIPService PowerShell module](/information-protection/deploy-use/install-powershell).
    

## AzureInformationProtection

This module has cmdlets for the Azure Information Protection client, including both the unified labeling and classic clients. The cmdlets are installed together with the client. 

For more information, see:

- **Unified labeling client:**
    - [About the AIP unified labeling client](/information-protection/rms-client/aip-clientv2)
    - [Using PowerShell with the AIP unified labeling client](/information-protection/rms-client/clientv2-admin-guide-powershell)
    - [Install the AIP unified labeling client for users](/information-protection/rms-client/clientv2-admin-guide-install)

- **Classic client:**
    - [About the AIP classic client](/information-protection/rms-client/aip-client)
    - [Using PowerShell with the AIP classic client](/information-protection/rms-client/client-admin-guide-powershell)
    - [Install the AIP classic client for users](/information-protection/rms-client/client-admin-guide-install)


> [!TIP]
> Not sure of the differences between these two clients? See this [FAQ](/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client).

### Installing the AzureInformationProtection module

- This module requires Windows PowerShell 4.0. This prerequisite is not checked by the installation. 
- The module installs automatically when you install the full version of the Azure Information Protection clients. Alternately, you can install the module only by using the `PowerShellOnly=true` parameter.

### Classic client deprecation

To provide a unified and streamlined customer experience, the **Azure Information Protection classic client** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021.** 

This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).

## AADRM
    
The cmdlets in this module let you administer the Azure Rights Management protection service for Azure Information Protection.

This module is now deprecated and replaced with the [AIPService](#aipservice) module, which provides the same functionality with renamed cmdlets. 

The renamed cmdlets in the current module have aliases to the old cmdlets. Cmdlets from the AADRM module that were already deprecated and no longer used were not carried forward to the newer AIPService module.

Support for this older module ended **July 15, 2020**.  
