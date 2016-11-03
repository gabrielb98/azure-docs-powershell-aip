---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=623036
schema: 2.0.0
ms.assetid: 0D84EE44-D412-40CA-A106-576E23CB81E8
---

# Enable-AadrmDocumentTrackingFeature

## SYNOPSIS
Enables document tracking for Rights Management.

## SYNTAX

```
Enable-AadrmDocumentTrackingFeature [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Enable-AadrmDocumentTrackingFeature** cmdlet enables the document tracking feature for Azure Rights Management (Azure RMS).
This cmdlet enables access to the document tracking site so that users can track or revoke access to protected documents that they have shared.
This setting is organization-wide; you cannot enable document tracking for some users in your organization and not for others.

By default, document tracking is enabled, so you would run this cmdlet only if somebody had previously disabled document tracking for your organization.
After enabling document tracking, users can see information in the document tracking site for all the protected documents that they have shared, and not just information from when you enabled the feature.
For example, they could revoke a document that they shared when document tracking was disabled.

For more information about document tracking and revocation, see Track and revoke your documents when you use the RMS sharing applicationhttps://docs.microsoft.com/rights-management/rms-client/sharing-app-track-revoke (https://docs.microsoft.com/rights-management/rms-client/sharing-app-track-revoke) from the Rights Management sharing application user guide.

## EXAMPLES

### Example 1: Enable document tracking
```
PS C:\>EnableAadrmDocumentTrackingFeature
```

This command enables document tracking for Azure RMS.

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
Prompts you for confirmation before running the cmdlet.Prompts you for confirmation before running the cmdlet.

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
The cmdlet is not run.Shows what would happen if the cmdlet runs.
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

[Disable-AadrmDocumentTrackingFeature](./Disable-AadrmDocumentTrackingFeature.md)

[Get-AadrmDocumentTrackingFeature](./Get-AadrmDocumentTrackingFeature.md)


