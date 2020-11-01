---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=858202
schema: 2.0.0
---

# Add-AIPScannerRepository

## SYNOPSIS
Adds a data repository to be scanned by the Azure Information Protection scanner. 

## SYNTAX

```
Add-AIPScannerRepository [-Path] <String> [-OverrideLabel <OverrideLabel>]
 [-PreserveFileDetails <PreserveFileDetails>] [-DefaultOwner <String>] [-SetDefaultLabel <DefaultLabel>]
 [-DefaultLabelId <Guid>] [-MatchPolicy <MatchPolicy>] [<CommonParameters>]
```

## DESCRIPTION
**Relevant for:** AIP classic client only

This cmdlet is deprecated for the current version of the Azure Information Protection scanner installed with the classic client. Instead, use the [Azure portal to configure the scanner](/information-protection/deploy-aip-scanner).

> [!NOTE]
> To provide a unified and streamlined customer experience, the **Azure Information Protection classic client** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021.** 
> 
> This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).
>