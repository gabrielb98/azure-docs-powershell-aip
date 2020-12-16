---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 9802F554-834A-4BA0-A086-C7F8B2976939
online version: https://go.microsoft.com/fwlink/?linkid=2147076
schema: 2.0.0
---

# Set-AipServiceDocumentRevoked

## SYNOPSIS
Revokes access for specified users, to a specified tracked and protected document.

> [!NOTE]
> Track and revoke features for the unified labeling client are currently in PREVIEW. The [Azure Preview Supplemental Terms](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) include additional legal terms that apply to Azure features that are in beta, preview, or otherwise not yet released into general availability. 
> 
## SYNTAX

```
Set-AipServiceDocumentRevoked [-Force] -ContentId <Guid> - IssuerName <String> [-WhatIf]  [-Confirm]  [<CommonParameters>]
```

## DESCRIPTION
Relevant for the unified labeling client only

The **Set-AipServiceDocumentRevoked** cmdlet revokes access to a specified document, based on the document's contentID and Rights Management issuer.

To retrieve the contentID for a specific document, use the [Get-AipServiceDocumentLog](Get-AipServiceDocumentLog.md) cmdlet.

## EXAMPLES

### Example 1: Revoke access to a specific protected document
```
PS C:\>Set-AipServiceDocumentRevoked -ContentId c03bf90c-6e40-4f3f-9ba0-2bcd77524b87 - IssuerName  “alice@microsoft.com”
```
This command revokes access to the document identified using the c03bf90c-6e40-4f3f-9ba0-2bcd77524b87 contentID and 
This command sets the document state as revoked for the document with contentId as c03bf90c-6e40-4f3f-9ba0-2bcd77524b87 & IssuerName as alice@microsoft.com.

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
Specifies the email address of a user or group to have administrative rights for the protection service. If the user has no email address, specify the user's Universal Principal Name.

```yaml
Type: String
Parameter Sets: String
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

[Clear-AipServiceDocumentRevoked](Clear-AipServiceDocumentRevoked.md)

[Get-AipServiceDocumentTrackingFeature](Get-AipServiceDocumentTrackingFeature.md)