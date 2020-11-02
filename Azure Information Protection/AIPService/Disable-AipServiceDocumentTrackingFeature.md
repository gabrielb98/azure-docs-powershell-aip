---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 5C8ED12E-4A84-446E-962F-5E886CB40DF9
online version: https://go.microsoft.com/fwlink/?linkid=2045125
schema: 2.0.0
---

# Disable-AipServiceDocumentTrackingFeature

## SYNOPSIS
**Relevant for:** Classic client only

Disables document tracking for Azure Information Protection.

## SYNTAX

```
Disable-AipServiceDocumentTrackingFeature [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Disable-AipServiceDocumentTrackingFeature** cmdlet disables the document tracking feature for Azure Information Protection. This cmdlet disables access to the document tracking site so that all users in your organization cannot track or revoke access to documents that they have protected. In addition, activity related to shared documents (who opened them, when, from which location) is not logged to the document tracking site. For example, if you later enable the document tracking site, users will see the documents that they protected while the site was disabled but cannot see who opened them.

You must use PowerShell to disable document tracking; you cannot do this configuration by using a management portal.

Document tracking is enabled by default for an organization using the protection service from Azure Information Protection, but you might need to disable this feature for privacy requirements that are specific to your organization or region. This setting is organization-wide; you cannot disable document tracking for some users in your organization and not for others.

When document tracking is disabled, users still see options that refer to tracking and revocation in applications such as Word and File Explorer, and the Azure Information Protection client. However, when users access the document tracking site, they see the following message:

**Your administrator has disabled document tracking for your organization.**
**Contact your administrator for details.**

You can disable document tracking either before you activate the protection service for Azure Information Protection, or after. After you have disabled document tracking, you can re-enable it at any time.

For additional information about the document tracking site, see [Configuring and using document tracking for Azure Information Protection](/information-protection/rms-client/client-admin-guide-document-tracking) from the Azure Information Protection client administrator guide.

> [!NOTE]
> To provide a unified and streamlined customer experience, the **Azure Information Protection classic client** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021.** 
> 
> This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).
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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Enable-AipServiceDocumentTrackingFeature](./Enable-AipServiceDocumentTrackingFeature.md)

[Get-AipServiceDocumentTrackingFeature](./Get-AipServiceDocumentTrackingFeature.md)