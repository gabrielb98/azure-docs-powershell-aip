---
title: Overview of PowerShell for Azure Information Protection| Microsoft Docs
description: An introduction to the PowerShell modules that you can use with Azure Information Protection.
services: azure
author: batamig
manager: rkarlin
ms.product: information-protection
ms.service: powershell
ms.devlang: powershell
ms.topic: reference
ms.date: 09/24/2020
ms.author: bagol
---

# Azure Information Protection

This documentation describes the following PowerShell modules and cmdlets:

- [AzureInformationProtection module](#azureinformationprotection-module)
- [AADRM module](#aadrm-module)

For more information about cmdlets used by the Azure Information Protection unified labeling client, see the [Azure Information Protection PowerShell documentation](/powershell/azure/aip/overview).

## AzureInformationProtection module

This documentation includes only cmdlets used by the Azure Information Protection classic client.

To provide a unified and streamlined customer experience, **Azure Information Protection client (classic)** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021**. This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).

When used with the classic client, the cmdlets let you protect and unprotect files, label files, and get information about files that are protected and labeled. These cmdlets are installed with the classic client and can be used with Azure Information Protection, the protection service (Azure Rights Management) for Azure Information Protection, and Active Directory Rights Management Services (AD RMS).

The module installs automatically when you install the full version of the Azure Information Protection clients but you can also install just the module by using the `PowerShellOnly=true` parameter.

> [!NOTE]
> This module requires Windows PowerShell 4.0, and this requirement is not checked by the installation. 
> 

For more information, see:

- [Using PowerShell with the Azure Information Protection client](/azure/information-protection/rms-client/client-admin-guide-powershell)
- [Install the Azure Information Protection client for users](/azure/information-protection/rms-client/client-admin-guide-install)
    

## AADRM module

This module is now deprecated and replaced with the **AIPService** module, which provides the same functionality with renamed cmdlets. The renamed cmdlets in the current module have aliases to the old cmdlets.
    
Support for this older module ended **July 15, 2020**.

The cmdlets in this module let you administer the protection service (Azure Rights Management) for Azure Information Protection.

For more information about the AIPService module, see the [Azure Information Protection PowerShell documentation](/powershell/azure/aip/overview).

> [!NOTE]
> Some cmdlets from the legacy AADRM module were not carried forward to this new module, because they were already deprecated and no longer used. Support for the AADRM module ended on July 15, 2020.
>
