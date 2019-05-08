---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 3F0BC472-41CC-41CA-A1B5-ACB84B1C2DA9
online version: https://go.microsoft.com/fwlink/?linkid=2045059
schema: 2.0.0
---

# Get-AipServiceDocumentTrackingFeature

## SYNOPSIS
Indicates whether document tracking is enabled or disabled for Azure Information Protection.

## SYNTAX

```
Get-AipServiceDocumentTrackingFeature [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceDocumentTrackingFeature** cmdlet indicates whether the Azure Information Protection document tracking feature is enabled or disabled.

You must use PowerShell to get this information about document tracking; you cannot get this information by using a management portal.

For additional information about the document tracking site, see [Configuring and using document tracking for Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-document-tracking) from the Azure Information Protection client administrator guide.

## EXAMPLES

### Example: Determine whether the document tracking site is enabled
```
PS C:\>Get-AipServiceDocumentTrackingFeature
```

This command determines whether the Azure Information Protection document tracking feature is enabled.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AipServiceDocumentTrackingFeature](./Disable-AipServiceDocumentTrackingFeature.md)

[Enable-AipServiceDocumentTrackingFeature](./Enable-AipServiceDocumentTrackingFeature.md)
