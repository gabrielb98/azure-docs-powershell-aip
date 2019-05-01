---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 0D84EE44-D412-40CA-A106-576E23CB81E8
online version: https://go.microsoft.com/fwlink/?linkid=2044867
schema: 2.0.0
---

# Enable-AipServiceDocumentTrackingFeature

## SYNOPSIS
Enables document tracking for Azure Information Protection.

## SYNTAX

```
Enable-AipServiceDocumentTrackingFeature [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Enable-AipServiceDocumentTrackingFeature** cmdlet enables the document tracking feature for Azure Information Protection. This cmdlet enables access to the document tracking site so that users can track or revoke access to documents that they have protected. This setting is organization-wide; you cannot enable document tracking for some users in your organization and not for others.

You must use PowerShell to enable document tracking; you cannot do this configuration by using a management portal.

By default, document tracking is enabled, so you would run this cmdlet only if somebody had previously disabled document tracking for your tenant. When document tracking is enabled, users can access the document tracking site to see the protected documents that they have shared to date. Activity related to shared documents (who opened them, when, from which location) is shown for only when the document tracking site is enabled. For example, a user could revoke a document that they shared when document tracking was disabled but they cannot not see who opened this document when document tracking was disabled.

For additional information about the document tracking site, see [Configuring and using document tracking for Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-document-tracking) from the Azure Information Protection client administrator guide.

## EXAMPLES

### Example 1: Enable document tracking
```
PS C:\>EnableAipServiceDocumentTrackingFeature
```

This command enables document tracking for Azure Information Protection.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AipServiceDocumentTrackingFeature](./Disable-AipServiceDocumentTrackingFeature.md)

[Get-AipServiceDocumentTrackingFeature](./Get-AipServiceDocumentTrackingFeature.md)

