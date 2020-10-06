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
ms.date: 03/04/2020
ms.author: bagol
---

# Azure Information Protection

You can use the following PowerShell modules with Azure Information Protection: 

- **AADRM**
    
    This module is now deprecated and replaced with the AIPService module, which provides the same functionality with renamed cmdlets. The renamed cmdlets in the current module have aliases to the old cmdlets.
    
    Support for this older module ends **July 15, 2020**.
    
    The cmdlets in this module let you administer the protection service (Azure Rights Management) for Azure Information Protection.
    

- **AIPService**
    
    These cmdlets let you administer the protection service (Azure Rights Management) for Azure Information Protection. The AIPService module replaces the older module, AADRM.

    For more information about when to use these PowerShell cmdlets and to see groupings of cmdlets by administration tasks, see [Administering protection from Azure Information Protection by using PowerShell](/information-protection/deploy-use/administer-powershell).
    
    For upgrading and installation instructions, see [Installing the AIPService PowerShell module](/information-protection/deploy-use/install-powershell).
    
    Note: Some cmdlets from the AADRM module were not carried forward to this new module, because they were already deprecated and no longer used.

- **AzureInformationProtection**
    
    This module has cmdlets for the Azure Information Protection unified labeling client, and the Azure Information Protection client (classic).
    
    For the Azure Information Protection unified labeling client: The cmdlets let you label files and get information about files that are labeled. These cmdlets are installed with the [Azure Information Protection unified labeling client](/information-protection/rms-client/aip-clientv2) and can be used with Azure Information Protection only.
    
    For the Azure Information Protection client (classic): The cmdlets let you protect and unprotect files, label files, and get information about files that are protected and labeled. These cmdlets are installed with the [Azure Information Protection client](/information-protection/rms-client/aip-client) and can be used with Azure Information Protection, the protection service (Azure Rights Management) for Azure Information Protection, and Active Directory Rights Management Services (AD RMS)
    
    For information about when and how to use these PowerShell cmdlets, see [Using PowerShell with the Azure Information Protection unified labeling client](/information-protection/rms-client/clientv2-admin-guide-powershell) and [Using PowerShell with the Azure Information Protection client](/information-protection/rms-client/client-admin-guide-powershell).
    
    For installation instructions, see [Install the Azure Information Protection unified labeling client for users](/information-protection/rms-client/clientv2-admin-guide-install) and [Install the Azure Information Protection client for users](/information-protection/rms-client/client-admin-guide-install). Note that this module requires Windows PowerShell 4.0 and that this prerequisite is not checked by the installation. The module installs automatically when you install the full version of the Azure Information Protection clients but you can also install just the module by using the `PowerShellOnly=true` parameter.

