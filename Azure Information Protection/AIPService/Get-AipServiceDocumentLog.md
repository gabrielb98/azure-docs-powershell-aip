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

## SYNTAX

```
Get-AipServiceDocumentLog -UserEmail <String> [-FromTime <DateTime>] [-ToTime <DateTime>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceDocumentLog** cmdlet returns protection information about the tracked documents for a specified user if that user protected documents (the Rights Management issuer) or was the Rights Management owner for documents, or protected documents were configured to grant access directly to the user. This cmdlet helps to answer the question "How are documents protected for a specified user?" The information returned includes:

- The document content ID, with the document name if available.
- The Rights Management owner and Rights Management issuer.
- The users and groups that were granted access.
- The protection template ID or specific usage rights that protects the document.
- Any expiry, offline access, or revocation setting.

For more information about the [Rights Management owner and IRights Management issuer](https://docs.microsoft.com/information-protection/deploy-use/configure-usage-rights#rights-management-issuer-and-rights-management-owner).

You can specify a start time and stop time of entries to include. The output is returned as a list of PowerShell objects in the PowerShell console.

You can alternatively use the document tracking site to get the protection information about the tracked documents. For more information, see the [Tracking and revoking documents for users](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-document-tracking#tracking-and-revoking-documents-for-users) section in the Azure Information Protection client admin guide.

## EXAMPLES

### Example 1: Get protection information about all tracked documents for a user
```
PS C:\>Get-AipServiceDocumentLog -UserEmail "test@contoso.com"
```

This command gets protection information about the tracked documents for a user who has the email address of "test@contoso.com" and that user is the Rights Management issuer or Rights Management owner for the document, or the document was configured to grant access to that user.

### Example 2: Get protection information about tracked documents for a user, for a specific time period
```
PS C:\>Get-AipServiceDocumentLog -UserEmail "test@contoso.com" -FromTime "01/01/2018 00:00:00" -ToTime "01/31/2018 23:59:59"
```

This command is the same as the previous example except that results are limited to documents that were protected within a specific time period by using the *FromTime* and *ToTime* parameters. In this example, the time period is all days in January 2018, using the US date format.

### Example 3: Get protection information about all tracked documents for a user and save the results to a .csv file
```
PS C:\>$documentLogs = Get-AipServiceDocumentLog -UserEmail "test@microsoft.com"
PS C:\>$documentLogs | Export-Csv 'C:\Temp\DocumentLog.csv' -NoTypeInformation
```

The first command gets the protection information about the tracked documents for a user who has the email address of "test@contoso.com" and that user is the Rights Management issuer or Rights Management owner for the document, or the document was configured to grant access to that user. The information is saved in a variable.

The second command then uses the [Export-Csv](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-4.0) cmdlet to convert the protection information into .csv format, and saves it to the C:\Temp\DocumentLog.csv file.

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

### -FromTime
Specifies the start time (inclusive) for the log file as a **DateTime** object. To obtain a **DateTime** object, use the [Get-Date](https://go.microsoft.com/fwlink/?LinkID=293966) cmdlet. Specify the date and time according to your system locale settings. For more information, type `Get-Help Get-Date`.

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

### -ToTime
Specifies the stop time (inclusive) for the log file as a **DateTime** object. To obtain a **DateTime** object, use the [Get-Date](https://go.microsoft.com/fwlink/?LinkID=293966) cmdlet. Specify the date and time according to your system locale settings. For more information, type `Get-Help Get-Date`.

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
Specifies the email address of the user. The cmdlet gets the protection information for documents if that user protected documents (the Rights Management issuer) or was the Rights Management owner for documents, or protected documents were configured to grant access directly to the user. Group addresses are not supported with this cmdlet. 

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-AipServiceTrackingLog](./Get-AipServiceTrackingLog.md)

