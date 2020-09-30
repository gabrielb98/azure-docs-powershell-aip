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

You can use the following PowerShell modules with Azure Information Protection: 

## AzureInformationProtection module

This module has cmdlets for the Azure Information Protection unified labeling client, and the Azure Information Protection client (classic).

For the Azure Information Protection unified labeling client: The cmdlets let you label files and get information about files that are labeled. These cmdlets are installed with the [Azure Information Protection unified labeling client](/information-protection/rms-client/aip-clientv2) and can be used with Azure Information Protection only.

The module installs automatically when you install the full version of the Azure Information Protection clients but you can also install just the module by using the `PowerShellOnly=true` parameter.

> [!NOTE]
> This module requires Windows PowerShell 4.0, and this requirement is not checked by the installation. 
> 

For more information, see:
- [Install the Azure Information Protection unified labeling client for users](/information-protection/rms-client/clientv2-admin-guide-install)
- [Using PowerShell with the Azure Information Protection unified labeling client](/information-protection/rms-client/clientv2-admin-guide-powershell)

### Use the AzureInformationProtection module with the AIP classic client

To provide a unified and streamlined customer experience, **Azure Information Protection client (classic)** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021**. This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).

When used with the classic client, the cmdlets let you protect and unprotect files, label files, and get information about files that are protected and labeled. These cmdlets are installed with the classic client and can be used with Azure Information Protection, the protection service (Azure Rights Management) for Azure Information Protection, and Active Directory Rights Management Services (AD RMS).

For more information about cmdlets that are supported only with the classic client, see:

- [Legacy PowerShell documentation](previous-versions/azure/devops/powershell/azure/aip/overview)
- [Using PowerShell with the Azure Information Protection client](previous-versions/azure/information-protection/rms-client/client-admin-guide-powershell)
- [Install the Azure Information Protection client for users](previous-versions/azure/information-protection/rms-client/client-admin-guide-install)
    


- **AADRM**
    
    This module is now deprecated and replaced with the AIPService module, which provides the same functionality with renamed cmdlets. The renamed cmdlets in the current module have aliases to the old cmdlets.
    
    Support for this older module ended **July 15, 2020**.
    
    The cmdlets in this module let you administer the protection service (Azure Rights Management) for Azure Information Protection.
    

- **AIPService**
    
    These cmdlets let you administer the protection service (Azure Rights Management) for Azure Information Protection. The AIPService module replaces the older module, AADRM.

    For more information about when to use these PowerShell cmdlets and to see groupings of cmdlets by administration tasks, see [Administering protection from Azure Information Protection by using PowerShell](/information-protection/deploy-use/administer-powershell).
    
    For upgrading and installation instructions, see [Installing the AIPService PowerShell module](/information-protection/deploy-use/install-powershell).
    
    > [!NOTE]
    > Some cmdlets from the legacy AADRM module were not carried forward to this new module, because they were already deprecated and no longer used. Support for the AADRM module ended on July 15, 2020.
    >
 
- **AzureInformationProtection**
    
    This module has cmdlets for the Azure Information Protection unified labeling client, and the Azure Information Protection client (classic).

>[!NOTE] 
> To provide a unified and streamlined customer experience, **Azure Information Protection client (classic)** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021**. This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).
    
    For the Azure Information Protection unified labeling client: The cmdlets let you label files and get information about files that are labeled. These cmdlets are installed with the [Azure Information Protection unified labeling client](/information-protection/rms-client/aip-clientv2) and can be used with Azure Information Protection only.
    
    For the Azure Information Protection client (classic): The cmdlets let you protect and unprotect files, label files, and get information about files that are protected and labeled. These cmdlets are installed with the [Azure Information Protection client](/information-protection/rms-client/aip-client) and can be used with Azure Information Protection, the protection service (Azure Rights Management) for Azure Information Protection, and Active Directory Rights Management Services (AD RMS)
    
    For information about when and how to use these PowerShell cmdlets, see [Using PowerShell with the Azure Information Protection unified labeling client](/information-protection/rms-client/clientv2-admin-guide-powershell) and [Using PowerShell with the Azure Information Protection client](/information-protection/rms-client/client-admin-guide-powershell).
    
    For installation instructions, see [Install the Azure Information Protection unified labeling client for users](/information-protection/rms-client/clientv2-admin-guide-install) and [Install the Azure Information Protection client for users](/information-protection/rms-client/client-admin-guide-install). Note that this module requires Windows PowerShell 4.0 and that this prerequisite is not checked by the installation. The module installs automatically when you install the full version of the Azure Information Protection clients but you can also install just the module by using the `PowerShellOnly=true` parameter.

