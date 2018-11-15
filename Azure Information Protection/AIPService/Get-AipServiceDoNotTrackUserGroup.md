---
external help file: AIPService.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=846355
schema: 2.0.0
ms.assetid: 176a6f8e-258b-4bb9-8690-dd1bae05530c
---

# Get-AipServiceDoNotTrackUserGroup

## SYNOPSIS
Gets the group for the users who must not be tracked by Information Protection service.

## SYNTAX

```
Get-AipServiceDoNotTrackUserGroup
```

## DESCRIPTION
The Get-AipServiceDoNotTrackUserGroup cmdlet gets the email address of the currently configured group for the users who must not be tracked by the Azure Information Protection service document tracking feature. 

This configuration might be needed for privacy requirements. For more information, see [Privacy controls for your document tracking site](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-document-tracking#privacy-controls-for-your-document-tracking-site).

You must use PowerShell to retrieve this information; you cannot see it by using a management portal. 

## EXAMPLES

### Example 1
```
PS C:\>Get-AipServiceDoNotTrackUserGroup
```

This command gets the email address of the currently configured group for the users who will not be tracked with the document tracking feature.

## PARAMETERS

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
