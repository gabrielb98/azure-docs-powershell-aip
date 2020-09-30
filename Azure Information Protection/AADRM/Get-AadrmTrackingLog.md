---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=869788
schema: 2.0.0
ms.assetid: B81D7053-016A-44C2-896A-040F6510C7ED
---

# Get-AadrmTrackingLog

## SYNOPSIS
Gets tracking information for protected documents.

## SYNTAX

```
Get-AadrmTrackingLog -UserEmail <String> [-FromTime <DateTime>] [-ToTime <DateTime>]
```

## DESCRIPTION
[!INCLUDE [AADRM is deprecated](../includes/aadrm-deprecated.md)]

The **Get-AadrmTrackingLog** cmdlet returns tracking information about protected documents for a specified user who protected documents (the Rights Management issuer) or who accessed protected documents. This cmdlet helps to answer the question "Which protected documents did a specified user track or access?" Information returned includes:

- The document content ID, with the document name if available.
- The Rights Management issuer.
- The users who accessed the document, when, and from what location. 
- What protection template ID or specific usage rights were used to protect the document and whether access was granted or denied.

You can specify a start time and stop time of entries to include. The output is returned as a list of PowerShell objects in the PowerShell console.

You can alternatively use the document tracking site to get the protection information about the tracked documents. For more information, see the [Tracking and revoking documents for users](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-document-tracking#tracking-and-revoking-documents-for-users) section in the admin guide.

## EXAMPLES

### Example 1: Get all tracking information for a user 
```
PS C:\>Get-AadrmTrackingLog -UserEmail "test@contoso.com" 
```

This command generates a log of all the tracking information for documents that were protected by or accessed by the user with the email address "test@contoso.com".

### Example 2: Get tracking information for a user, for a specific time period
```
PS C:\>Get-AadrmTrackingLog -UserEmail "test@contoso.com" -FromTime "01/01/2018 00:00:00" -ToTime "01/31/2018 23:59:59"
```

This command is the same as the previous example except that the results are limited to documents that were tracked within a specific time period by using the *FromTime* and *ToTime* parameters. In this example, the time period is all days in January 2018, using the US date format.

### Example 3: Get all tracking information for a user and save the results to a .csv file  
```
PS C:\>$trackingLogs = Get-AadrmTrackingLog -UserEmail "test@contoso.com"
PS C:\>$trackingLogs | Export-Csv 'C:\Temp\TrackingLog.csv' -NoTypeInformation
```

The first command generates a log of all the tracking information for documents that were protected by or accessed by the user with the email address "test@contoso.com", and saves the result in a variable.

The second command then uses the [Export-Csv](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-4.0) cmdlet to convert the tracking information into .csv format, and saves it to the C:\Temp\TrackingLog.csv file.

## PARAMETERS

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
Specifies the email address of the user. The cmdlet gets the tracking information for documents that were protected by, or accessed by the user who has this email address. 

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-AadrmDocumentLog](./Get-AadrmDocumentLog.md)


