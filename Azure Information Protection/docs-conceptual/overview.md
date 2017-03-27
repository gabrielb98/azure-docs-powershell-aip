---
title: Overview of PowerShell for Azure Information Protection| Microsoft Docs
description: An introduction to the PowerShell modules that you can use with Azure Information Protection.
services: azure
author: sdwheeler
manager: carmonm
ms.product: azure
ms.service: powershell
ms.devlang: powershell
ms.topic: reference
ms.date: 03/09/2017
ms.author: sewhee
---

# Azure Information Protection

You can use the following PowerShell modules to administer the Azure Rights Management service for Azure Information Protection, and to classify and protect files in bulk. 

* AADRM

    These cmdlets let you administer the Azure Rights Management service. For more information
    about when you must use these PowerShell cmdlets and to see groupings of cmdlets by
    administration tasks, see
    [Administering Azure Rights Management by Using Windows PowerShell](/information-protection/deploy-use/administer-powershell).

* AzureInformationProtection

    These cmdlets are installed with the [Azure Information Protection client](/information-protection/rms-client/aip-client).
    This module replaces the RMS Protection Tool and the AD RMS Bulk Protection Tool. These cmdlets
    can be used with the Azure Information Protection service, the Azure Rights Management service
    (Azure RMS), and Active Directory Rights Management Services (AD RMS). For more information, see [Using PowerShell with the Azure Information Protection client](/information-protection/rms-client/client-admin-guide-powershell).

* RMSProtection Module

    These cmdlets are installed with the RMS
    Protection Tool. The RMS Protection tool is now replaced by the Azure Information Protection
    client, which includes a new PowerShell module, AzureInformationProtection.
