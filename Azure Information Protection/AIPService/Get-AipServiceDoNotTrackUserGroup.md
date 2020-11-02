---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 176a6f8e-258b-4bb9-8690-dd1bae05530c
online version: https://go.microsoft.com/fwlink/?linkid=2044894
schema: 2.0.0
---

# Get-AipServiceDoNotTrackUserGroup

## SYNOPSIS
**Relevant for:** Classic client only

Gets the group for the users who must not be tracked by Azure Information Protection.

## SYNTAX

```
Get-AipServiceDoNotTrackUserGroup [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceDoNotTrackUserGroup** cmdlet gets the email address of the currently configured group for the users who must not be tracked by the Azure Information Protection document tracking feature. 

This configuration might be needed for privacy requirements. For more information, see [Privacy controls for your document tracking site](/information-protection/rms-client/client-admin-guide-document-tracking#privacy-controls-for-your-document-tracking-site).

You must use PowerShell to retrieve this information; you cannot see it by using a management portal. 


> [!NOTE]
> To provide a unified and streamlined customer experience, the **Azure Information Protection classic client** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021.** 
> 
> This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).
>

## EXAMPLES

### Example 1
```
PS C:\>Get-AipServiceDoNotTrackUserGroup
```

This command gets the email address of the currently configured group for the users who will not be tracked with the document tracking feature.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

### None

## OUTPUTS

### System.String
This operation returns the group email address as a **String**. If a group has not been configured, an empty **String** is returned.

## NOTES

## RELATED LINKS

[Clear-AipServiceDoNotTrackUserGroup](./Clear-AipServiceDoNotTrackUserGroup.md)

[Disable-AipServiceSuperUserFeature](./Disable-AipServiceSuperUserFeature.md)

[Enable-AipServiceDocumentTrackingFeature](./Enable-AipServiceDocumentTrackingFeature.md)

[Set-AipServiceDoNotTrackUserGroup](./Set-AipServiceDoNotTrackUserGroup.md)