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

You can turn document tracking off either before you activate AIP protection or after. Once you've turned tracking features off, you can also re-enable them at any time.

Document tracking features differ when working with the unified labeling and classic clients, as described below:

**Unified labeling client**

To turn off document tracking features with the unified labeling client, make sure that you set the **EnableTrackAndRevoke** advanced client setting to **False** in addition to running this cmdlet.

> [!NOTE]
> If you have upgraded to the unified labeling client from the classic client, and have had document tracking turned off, it remains turned off after your upgrade.
> 

**Classic client**

When working with the classic client, this cmdlet turns off access to the document tracking site so that all users in your organization cannot track or revoke access to documents that they have protected. 

In addition, activity related to shared documents (who opened them, when, from which location) is not logged to the document tracking site. For example, if you later enable the document tracking site, users will see the documents that they protected while the site was disabled but cannot see who opened them.

When document tracking is turned off, users still see options that refer to tracking and revocation in applications such as Word and File Explorer, and the Azure Information Protection client. However, when users access the document tracking site, they see the following message:

**Your administrator has disabled document tracking for your organization**.
**Contact your administrator for details**.

For additional information about the document tracking site, see [Configuring and using document tracking for Azure Information Protection](/information-protection/rms-client/client-admin-guide-document-tracking) from the Azure Information Protection classic client administrator guide.

> [!NOTE]
> You must use PowerShell to disable document tracking; you cannot do this configuration by using a management portal.

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