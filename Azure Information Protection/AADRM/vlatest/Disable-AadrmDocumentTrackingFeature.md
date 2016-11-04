---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=623032
schema: 2.0.0
ms.assetid: 5C8ED12E-4A84-446E-962F-5E886CB40DF9
---

# Disable-AadrmDocumentTrackingFeature

## SYNOPSIS
Disables document tracking for Rights Management.

## SYNTAX

```
Disable-AadrmDocumentTrackingFeature [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Disable-AadrmDocumentTrackingFeature** cmdlet disables the document tracking feature for Azure Rights Management (Azure RMS).
This cmdlet disables access to the document tracking site so that all users in your organization cannot track or revoke access to protected documents that they have shared.
Document tracking is enabled by default for an organization using Azure RMS but you might need to disable this feature for privacy requirements that are specific to your organization or region.
This setting is organization-wide; you cannot disable document tracking for some users in your organization and not for others.

When document tracking is disabled, users still see options that refer to tracking and revocation in applications such as Word and File Explorer, and the RMS sharing application.
However, when users access the document tracking site, they see the following message:

**Your administrator has disabled document tracking for your organization.**
**Contact your administrator for details.**

You can disable document tracking either before you activate Azure RMS, or after.
After you have disabled document tracking, you can re-enable it at any time.

For more information about document tracking and revocation, see Track and revoke your documents when you use the [RMS sharing application](https://docs.microsoft.com/rights-management/rms-client/sharing-app-track-revoke) (https://docs.microsoft.com/rights-management/rms-client/sharing-app-track-revoke) from the Rights Management sharing application user guide.

## EXAMPLES

### Example 1: Disable document tracking
```
PS C:\>Disable-AadrmDocumentTrackingFeature
```

This command disables document tracking for Azure RMS.

## PARAMETERS

### -Force
Forces the command to run without asking for user confirmation.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Enable-AadrmDocumentTrackingFeature](./Enable-AadrmDocumentTrackingFeature.md)

[Get-AadrmDocumentTrackingFeature](./Get-AadrmDocumentTrackingFeature.md)

[RMS sharing application](https://docs.microsoft.com/rights-management/rms-client/sharing-app-track-revoke)
