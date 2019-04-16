---
title: Overview of PowerShell for Azure Information Protection| Microsoft Docs
description: An introduction to the PowerShell modules that you can use with Azure Information Protection.
services: azure
author: cabailey
manager: mbaldwin
ms.product: information-protection
ms.service: powershell
ms.devlang: powershell
ms.topic: reference
ms.date: 02/14/2018
ms.author: cabailey
---

# Azure Information Protection

You can use the following PowerShell modules with Azure Information Protection: 

- **AADRM**
    
    These cmdlets let you administer the protection service (Azure Rights Management) for Azure Information Protection. 
    
    For more information about when to use these PowerShell cmdlets and to see groupings of cmdlets by administration tasks, see [Administering Azure Rights Management by Using Windows PowerShell](/information-protection/deploy-use/administer-powershell).
    
    For installation instructions, see [Installing the AADRM PowerShell module](/information-protection/deploy-use/install-powershell)

- **AzureInformationProtection**
    
    This module has cmdlets for the Azure Information Protection unified labeling client, and the Azure Information Protection client.
    
    For the Azure Information Protection unified labeling client: The cmdlets let you label files and get information about files that are labeled. These cmdlets are installed with the [Azure Information Protection unified labeling client](/information-protection/rms-client/aip-clientv2) and can be used with Azure Information Protection only.
    
    For the Azure Information Protection client: The cmdlets let you protect and unprotect files, label files, and get information about files that are protected and labeled. These cmdlets are installed with the [Azure Information Protection client](/information-protection/rms-client/aip-client) and can be used with Azure Information Protection, the protection service (Azure Rights Management) for Azure Information Protection, and Active Directory Rights Management Services (AD RMS)
    
    
    For information about when and how to use these PowerShell cmdlets, see [Using PowerShell with the Azure Information Protection unified labeling client](/information-protection/rms-client/clientv2-admin-guide-powershell) or [Using PowerShell with the Azure Information Protection client](/information-protection/rms-client/client-admin-guide-powershell).
    
    For installation instructions, see [Install the Azure Information Protection unified labeling client for users](/information-protection/rms-client/clientv2-admin-guide-install) or [Install the Azure Information Protection client for users](/information-protection/rms-client/client-admin-guide-install). Note that this module requires Windows PowerShell 4.0 and that this prerequisite is not checked by the installation. The module installs automatically when you install the full version of the Azure Information Protection clients but you can also install just the module by using the `PowerShellOnly=true` parameter.

