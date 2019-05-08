---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 176a6f8e-258b-4bb9-8690-dd1bae05530c
online version: https://go.microsoft.com/fwlink/?linkid=2044894
schema: 2.0.0
---

# Get-AipServiceDoNotTrackUserGroup

## SYNOPSIS
Gets the group for the users who must not be tracked by Azure Information Protection.

## SYNTAX

```
Get-AipServiceDoNotTrackUserGroup [<CommonParameters>]
```

## DESCRIPTION
The Get-AipServiceDoNotTrackUserGroup cmdlet gets the email address of the currently configured group for the users who must not be tracked by the Azure Information Protection document tracking feature. 

This configuration might be needed for privacy requirements. For more information, see [Privacy controls for your document tracking site](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-document-tracking#privacy-controls-for-your-document-tracking-site).

You must use PowerShell to retrieve this information; you cannot see it by using a management portal. 

## EXAMPLES

### Example 1
```
PS C:\>Get-AipServiceDoNotTrackUserGroup
```

This command gets the email address of the currently configured group for the users who will not be tracked with the document tracking feature.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

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
