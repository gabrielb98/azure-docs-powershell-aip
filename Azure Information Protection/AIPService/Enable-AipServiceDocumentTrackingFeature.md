---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 0D84EE44-D412-40CA-A106-576E23CB81E8
online version: https://go.microsoft.com/fwlink/?linkid=2044867
schema: 2.0.0
---

# Enable-AipServiceDocumentTrackingFeature

## SYNOPSIS
Turns on document track and revoke features for Azure Information Protection.

## SYNTAX

```
Enable-AipServiceDocumentTrackingFeature [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Enable-AipServiceDocumentTrackingFeature** cmdlet turns on the document track and revoke features for Azure Information Protection.

Activity related to shared documents (who opened them, when, from which location) is shown for only when the document track and revoke features are turned on. 


- This setting is organization-wide; you cannot turn on document tracking for some users in your organization and not for others.

- You must use PowerShell to turn on document tracking; you cannot do this configuration by using a management portal.

- By default, document tracking is turned on, so you would run this cmdlet only if somebody had previously turned off document tracking for your tenant. 


For more information, see:

- [Administrator Guide: Track and revoke document access with Azure Information Protection](/information-protection/rms-client/track-and-revoke-admin)

- [User Guide: Revoke document access with Azure Information Protection](/information-protection/rms-client/revoke-access-user) 

**Classic client only**:

If you are using the classic client, document tracking provides uses with access to the document tracking site, where they can view the protected documents that they have shared to date.

For more information, see:
[Configuring and using document tracking for Azure Information Protection for the classic client](/information-protection/rms-client/client-admin-guide-document-tracking).

## EXAMPLES

### Example 1: Turn on document tracking
```
PS C:\>EnableAipServiceDocumentTrackingFeature
```

This command turns on document tracking for Azure Information Protection.

## PARAMETERS

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

### -WhatIf
Shows what would happen if the cmdlet runs. The cmdlet is not run.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. 

For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AipServiceDocumentTrackingFeature](./Disable-AipServiceDocumentTrackingFeature.md)

[Get-AipServiceDocumentTrackingFeature](./Get-AipServiceDocumentTrackingFeature.md)

[Get-AipServiceDocumentLog](Get-AipServiceDocumentLog.md)