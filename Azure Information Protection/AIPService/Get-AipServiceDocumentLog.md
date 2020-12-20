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

> [!NOTE]
> Track and revoke features for the unified labeling client are currently in PREVIEW. The [Azure Preview Supplemental Terms](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) include additional legal terms that apply to Azure features that are in beta, preview, or otherwise not yet released into general availability. 
> 
## SYNTAX

### Unified labeling client
```
Get-AipServiceDocumentLog -ContentName <String> -Owner <String> [-FromTime <DateTime>] [-ToTime <DateTime>] [-WhatIf] [-Confirm]
 [<CommonParameters>]

```

### Classic client
```
Get-AipServiceDocumentLog -UserEmail <String> [-FromTime <DateTime>] [-ToTime <DateTime>] [-WhatIf] [-Confirm]
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

**Unified labeling client**

When used with the unified labeling client, the query is based on the document name, the owner email, or both.

You must specify at least one of the following parameters:

- **ContentName**
- **OwnerEmail**

> [!TIP]
> If you use the **ContentName** parameter, we recommend that you also use the **FromTime** and **ToTime** parameters to filter your content to a specific time period.
> 

**Classic client**

When used with the classic client, this cmdlet returns protection information about the tracked documents for a specified user if that user protected documents (the Rights Management issuer) or was the Rights Management owner for documents, or protected documents were configured to grant access directly to the user. 

You can alternatively use the document tracking site to get the protection information about the tracked documents. For more information, see the [Tracking and revoking documents for users](/information-protection/rms-client/client-admin-guide-document-tracking#tracking-and-revoking-documents-for-users) section in the Azure Information Protection client admin guide.

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

### Example 3: (Classic client only) Get protection information about all tracked documents for a user
```
Get-AipServiceDocumentLog -UserEmail "test@contoso.com"
```

This command gets protection information about the tracked documents for a user who has the email address of "test@contoso.com" and that user is the Rights Management issuer or Rights Management owner for the document, or the document was configured to grant access to that user.

### Example 4: (Classic client only) Get protection information about tracked documents for a user, for a specific time period
```
Get-AipServiceDocumentLog -UserEmail "test@contoso.com" -FromTime "01/01/2018 00:00:00" -ToTime "01/31/2018 23:59:59"
```

This command is the same as the previous example except that results are limited to documents that were protected within a specific time period by using the *FromTime* and *ToTime* parameters. In this example, the time period is all days in January 2018, using the US date format.

### Example 5: (Classic client only) Get protection information about all tracked documents for a user and save the results to a .csv file
```
$documentLogs = Get-AipServiceDocumentLog -UserEmail "test@microsoft.com"
$documentLogs | Export-Csv 'C:\Temp\DocumentLog.csv' -NoTypeInformation
```

The first command gets the protection information about the tracked documents for a user who has the email address of "test@contoso.com" and that user is the Rights Management issuer or Rights Management owner for the document, or the document was configured to grant access to that user. The information is saved in a variable.

The second command then uses the [Export-Csv](/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-4.0) cmdlet to convert the protection information into **.csv** format, and saves it to the **C:\Temp\DocumentLog.csv** file.

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
**Relevant for:** Unified labeling client only

Specifies the tracked document's full name, including the file extension. 

If you have the unified labeling client, you must include either this parameter, or the **OwnerEmail** parameter, or you can include both.

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
**Relevant for:** Unified labeling client only

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

### -UserEmail
**Relevant for:** Classic client only


Specifies the email address of the user. The cmdlet gets the protection information for documents if that user protected documents (the Rights Management issuer) or was the Rights Management owner for documents, or protected documents were configured to grant access directly to the user. 

Group addresses are not supported with this cmdlet. 

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
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