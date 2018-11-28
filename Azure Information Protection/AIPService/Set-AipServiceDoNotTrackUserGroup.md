---
external help file: AIPService.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=2045407
schema: 2.0.0
ms.assetid: a168cc5e-4e90-4a6d-8241-2f6d9dc27d7e
---

# Set-AipServiceDoNotTrackUserGroup

## SYNOPSIS
Sets a group for the users who must not be tracked by Azure Information Protection.

## SYNTAX

```
Set-AipServiceDoNotTrackUserGroup -EmailAddress <String>
```

## DESCRIPTION
The Set-AipServiceDoNotTrackUserGroup cmdlet sets a group for Azure Information Protection when you use document tracking and you have users who must not be tracked. This configuration might be needed for privacy requirements. For more information, see [Privacy controls for your document tracking site](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-document-tracking#privacy-controls-for-your-document-tracking-site).

If this cmdlet has been run before, running it again overwrites the group that was set previously. You can set only one group, but it can contain nested groups.

You must use PowerShell to set this group so that users are not tracked; you cannot do this configuration by using a management portal.

## EXAMPLES

### Example 1
```
PS C:\>Set-AipServiceDoNotTrackUserGroup -GroupEmailAddress "DoNotTrackUserGroup@contoso.com"
```

This command sets a group that has the email address of DoNotTrackUserGroup@contoso.com for the Contoso organization so that users in that group will not be tracked with the document tracking feature.

## PARAMETERS

### -EmailAddress
Specifies the email address of the group whose members will be exempt from being tracked with the document tracking feature.

You can specify a group that contains individual users, or nested groups. The email address must be a valid group email address that already exists in the organization.

Note: Global administrators can always track the activities of these members.


```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Clear-AipServiceDoNotTrackUserGroup](./Clear-AipServiceDoNotTrackUserGroup.md)

[Disable-AipServiceSuperUserFeature](./Disable-AipServiceSuperUserFeature.md)

[Enable-AipServiceDocumentTrackingFeature](./Enable-AipServiceDocumentTrackingFeature.md)

[Get-AipServiceDoNotTrackUserGroup](./Get-AipServiceDoNotTrackUserGroup.md)

