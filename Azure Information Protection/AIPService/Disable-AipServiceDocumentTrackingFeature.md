---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 5C8ED12E-4A84-446E-962F-5E886CB40DF9
online version: https://go.microsoft.com/fwlink/?linkid=2045125
schema: 2.0.0
---

# Disable-AipServiceDocumentTrackingFeature

## SYNOPSIS
Turns off document tracking for Azure Information Protection.

## SYNTAX

```
Disable-AipServiceDocumentTrackingFeature [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Disable-AipServiceDocumentTrackingFeature** cmdlet turns off the document tracking feature for Azure Information Protection, so that users in your organization cannot track or revoke access to documents that they have protected.

Document tracking is turned on by default, but you may need to turn it off for privacy requirements in your organization or region. This setting is organization-wide, and you cannot turn it off for some users in your organization but not others.

To turn off document tracking features with the unified labeling client, make sure that you set the **EnableTrackAndRevoke** advanced client setting to **False** in addition to running this cmdlet.

> [!NOTE]
> If you have upgraded to the unified labeling client from the classic client, and have had document tracking turned off, it remains turned off after your upgrade.
>
## EXAMPLES

### Example 1: Disable document tracking
```
PS C:\>Disable-AipServiceDocumentTrackingFeature
```

This command disables document tracking for Azure Information Protection.

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

[Enable-AipServiceDocumentTrackingFeature](./Enable-AipServiceDocumentTrackingFeature.md)

[Get-AipServiceDocumentTrackingFeature](./Get-AipServiceDocumentTrackingFeature.md)