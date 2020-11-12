---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 3F0BC472-41CC-41CA-A1B5-ACB84B1C2DA9
online version: https://go.microsoft.com/fwlink/?linkid=2045059
schema: 2.0.0
---

# Get-AipServiceDocumentTrackingFeature

## SYNOPSIS
**Relevant for:** AIP classic client only

Indicates whether document tracking is enabled or disabled for Azure Information Protection.

## SYNTAX

```
Get-AipServiceDocumentTrackingFeature [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceDocumentTrackingFeature** cmdlet indicates whether the Azure Information Protection document tracking feature is enabled or disabled.

You must use PowerShell to get this information about document tracking; you cannot get this information by using a management portal.

For additional information about the document tracking site, see [Configuring and using document tracking for Azure Information Protection](/information-protection/rms-client/client-admin-guide-document-tracking) from the Azure Information Protection client administrator guide.


> [!NOTE]
> To provide a unified and streamlined customer experience, the **Azure Information Protection classic client** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021.** 
> 
> This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).
>

## EXAMPLES

### Example: Determine whether the document tracking site is enabled
```
PS C:\>Get-AipServiceDocumentTrackingFeature
```

This command determines whether the Azure Information Protection document tracking feature is enabled.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AipServiceDocumentTrackingFeature](./Disable-AipServiceDocumentTrackingFeature.md)

[Enable-AipServiceDocumentTrackingFeature](./Enable-AipServiceDocumentTrackingFeature.md)