---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 5b4a72f5-2df1-4ae1-b020-a3d30f759a8b
online version: https://go.microsoft.com/fwlink/?linkid=2045007
schema: 2.0.0
---

# Clear-AipServiceDoNotTrackUserGroup

## SYNOPSIS
Clears the group for the users who must not be tracked by Azure Information Protection.

## SYNTAX

```
Clear-AipServiceDoNotTrackUserGroup [<CommonParameters>]
```

## DESCRIPTION
The **Clear-AipServiceDoNotTrackUserGroup** cmdlet removes the currently configured group for the users who must not be tracked by the Azure Information Protection document tracking feature. This configuration might be needed for privacy requirements. For more information, see [Privacy controls for your document tracking site](/information-protection/rms-client/client-admin-guide-document-tracking#privacy-controls-for-your-document-tracking-site).

This cmdlet does not delete the specified group from Azure Active Directory. Instead, a group will no longer be used to exempt users from tracking. As a result, all users in your organization will now be tracked when you use the document tracking feature. 

You must use PowerShell to remove this group from the Azure Information Protection service; you cannot do this configuration by using a management portal.

## EXAMPLES

### Example 1
```
PS C:\>Clear-AipServiceDoNotTrackUserGroup
```

This command removes the currently configured group (if set) that exempts users from being tracked by the document tracking feature. As a result, all users in your organization can be tracked when you use the document tracking feature.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Disable-AipServiceSuperUserFeature](./Disable-AipServiceSuperUserFeature.md)

[Enable-AipServiceDocumentTrackingFeature](./Enable-AipServiceDocumentTrackingFeature.md)

[Get-AipServiceDoNotTrackUserGroup](./Get-AipServiceDoNotTrackUserGroup.md)

[Set-AipServiceDoNotTrackUserGroup](./Set-AipServiceDoNotTrackUserGroup.md)