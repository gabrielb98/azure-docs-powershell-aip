---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 9802F554-834A-4BA0-A086-C7F8B2976939
online version: https://go.microsoft.com/fwlink/?linkid=2146792
schema: 2.0.0
---

# Clear-AipServiceDocumentRevoke

## SYNOPSIS
Un-revokes a specified, protected document that currently has a revoke status.

> [!NOTE]
> Track and revoke features for the unified labeling client are currently in PREVIEW. The [Azure Preview Supplemental Terms](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) include additional legal terms that apply to Azure features that are in beta, preview, or otherwise not yet released into general availability. 
> 
## SYNTAX
```
Clear-AipServiceDocumentRevoked [-Force] -ContentId <Guid> - IssuerName <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Clear-AipServiceDocumentRevoked** cmdlet clears the document's revoke status, and un-revokes a specified protected document, based on the document's contentID and Rights Management issuer. 

For example, use this cmdlet if you have accidentally revoked access to the specified document, and want to now grant access again.

Before running this cmdlet you must first load the **AipService.dll**.

## EXAMPLES

### Example 1: Unrevoke access for a specific document
```
Import-Module -Name "C:\Program Files\WindowsPowerShell\Modules\AIPService\1.0.0.4\AipService.dll"
Clear-AipServiceDocumentRevoked -ContentId c03bf90c-6e40-4f3f-9ba0-2bcd77524b87 - IssuerName  "alice@contoso.com"
```

This command clears the revoked state for a document with a contentID value of **c03bf90c-6e40-4f3f-9ba0-2bcd77524b87,** which was protected by a user with the **alice@contoso.com** email address.

## PARAMETERS

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContentId
Specifies the contentID value for the document you want to return tracking data for.

To retrieve the contentID for a specific document, use the [Get-AipServiceDocumentLog](Get-AipServiceDocumentLog.md) cmdlet.
 
```yaml
Type: String
Parameter Sets: String
Aliases: 

Required: True
Position: Named
Default value: None
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

### -IssuerName
Specifies the email of the Rights Management issuer for the document you want to unrevoke access for.

```yaml
Type: String
Parameter Sets: Email address
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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
Default value: None
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

[Get-AipServiceDocumentLog](Get-AipServiceDocumentLog.md)

[Set-AipServiceDocumentRevoked](Set-AipServiceDocumentRevoked.md)

[Get-AipServiceDocumentTrackingFeature](Get-AipServiceDocumentTrackingFeature.md)