---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: B497A721-7EA4-4876-B2B9-874299BB3C33
online version: https://go.microsoft.com/fwlink/?linkid=2044954
schema: 2.0.0
---

# Get-AipServiceDocumentLog

## SYNOPSIS
Gets protection information about documents that are tracked by Azure Information Protection.

This cmdlet is supported by both the Azure Information Protection classic and unified labeling clients, with different usage, as described below.

## SYNTAX
```
Get-AipServiceDocumentLog -ContentName <String> -Owner <String> [-FromTime <DateTime>] [-ToTime <DateTime>] [-WhatIf] [-Confirm]
 [<CommonParameters>]

```
## DESCRIPTION
The **Get-AIPServiceDocumentLog** cmdlet runs a query to return protection information about tracked documents.

Information returned includes:
- The document content ID, with the document name if available.
- The Rights Management owner and Rights Management issuer.
- The users and groups that were granted access.
- The protection template ID or specific usage rights that protect the document.
- Any expiry, offline access, or revocation setting.

You can specify a start time and stop time of entries to include. The output is returned as a list of PowerShell objects in the PowerShell console.

For more information, see [Rights Management owners and IRights Management issuers](/information-protection/deploy-use/configure-usage-rights#rights-management-issuer-and-rights-management-owner).

When used with the unified labeling client, the query is based on the document name, the owner email, or both.

You must specify at least one of the following parameters:

- **ContentName**
- **Owner**

> [!TIP]
> If you use the **ContentName** parameter, we recommend that you also use the **FromTime** and **ToTime** parameters to filter your content to a specific time period.
>

## EXAMPLES

### Example 1: (Unified labeling client only) Get protection information about all tracked documents with a specific filename, which were protected in a specific timeframe
```
Get-AipServiceDocumentLog -ContentName "test.docx" -FromTime "12/01/2020 00:00:00" -ToTime "12/31/2020 23:59:59"
```

This command runs a query and returns protection information about all tracked documents stored on your tenant with the filename **test.docx**, which were protected in December 2020.

### Example 2: (Unified labeling client only) Get protection information about all tracked documents with a specific filename and owner, which were protected in a specific timeframe
```
Get-AipServiceDocumentLog -ContentName "test.docx" -Owner “alice@microsoft.com” -FromTime "12/01/2020 00:00:00" -ToTime "12/31/2020 23:59:59"
```

This command runs a query and returns protection information about all tracked documents stored on your tenant that match the following details:

- The filename is **test.docx**
- The file was protected by a user with the email **alice@contoso.com**
- The file was protected in December 2020.


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

### -ContentName
Specifies the tracked document's full name, including the file extension. 

If you have the unified labeling client, you must include either this parameter, or the **Owner** parameter, or you can include both.

> [!TIP]
> If you use this parameter, we recommend that you also use the the **FromTime** and **ToTime** date filters to filter the data returned.
> 

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -FromTime
Specifies the start time (inclusive) for the log file as a **DateTime** object. To obtain a **DateTime** object, use the [Get-Date](/powershell/module/Microsoft.PowerShell.Utility/Get-Date?viewFallbackFrom=powershell-4.0) cmdlet. Specify the date and time according to your system locale settings. 

For more information, type `Get-Help Get-Date`.

```yaml
Type: DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Owner
Specifies the email address of the user who protected the document (the Rights Management issuer or owner).

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ToTime
Specifies the stop time (inclusive) for the log file as a **DateTime** object. To obtain a **DateTime** object, use the [Get-Date](/powershell/module/Microsoft.PowerShell.Utility/Get-Date?viewFallbackFrom=powershell-4.0) cmdlet. Specify the date and time according to your system locale settings. 

For more information, type `Get-Help Get-Date`.

```yaml
Type: DateTime
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

[Get-AipServiceTrackingLog](./Get-AipServiceTrackingLog.md)

**Unified labeling client only:**

[Set-AipServiceDocumentRevoked](Set-AipServiceDocumentRevoked.md)

[Clear-AipServiceDocumentRevoked](Clear-AipServiceDocumentRevoked.md)