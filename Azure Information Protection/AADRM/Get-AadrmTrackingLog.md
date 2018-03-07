---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400607
schema: 2.0.0
---

# Get-AadrmTrackingLog

## SYNOPSIS
Generates tracking information logs for all documents associated with a user email.

## SYNTAX

```
Get-AadrmTrackingLog -UserEmail <String> [-FromTime <DateTime>] [-ToTime <DateTime>]
```

## DESCRIPTION
The **Get-AadrmTrackingLog** cmdlet returns all the tracking information logs whose issuer or requester match the given email. You can specify a start time and stop time of entries to include. The logs will be output in json format to the powershell console.

You must use PowerShell to get these tracking information logs; you cannot do this action by using a management portal.

## EXAMPLES

### Example 1: Get all tracking information logs. 
```
PS C:\>Get-AadrmTrackingLog -UserEmail "test@microsoft.com" 
```

This command generates a log of all the tracking information for documents issued or requested by the user associated with email "test@microsoft.com."

### Example 2: Generate a log of commands for a specified time period.
```
PS C:\>Get-AadrmTrackingLog -UserEmail "test@microsoft.com" -FromTime "01/01/2018 00:00:00" -ToTime "01/31/2018 23:59:59"
```

This command generates a log of tracking information entries associated with given email, limited to items that fall within the specific time period by using the *FromTime* and *ToTime* parameters. In this example, the time period is all days in January 2018, using the US date format.

### Example 3: Get all logs and save to file.  
```
PS C:\>$trackingLogs = Get-AadrmTrackingLog -UserEmail "test@microsoft.com"
PS C:\>($trackingLogs | ConvertFrom-Json).SyncRoot | Export-Csv 'C:\Temp\TrackingLog.csv' -NoTypeInformation
```

This command uses [ConvertFrom-Json](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-4.0) cmdlet to convert from json to powershell object and the [Export-Csv] (https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-4.0) cmdlet to convert the tracking logs to a .csv format and saves them to the C:\Temp\TrackingLog.csv file.
For more information, type 'Get-Help Export-Csv'

## PARAMETERS

### -FromTime
Specifies the start time (inclusive) for the log file as a **DateTime** object. To obtain a **DateTime** object, use the [Get-Date](http://go.microsoft.com/fwlink/?LinkID=293966) cmdlet. Specify the date and time according to your system locale settings. For more information, type `Get-Help Get-Date`.

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
Specifies the stop time (inclusive) for the log file as a **DateTime** object. To obtain a **DateTime** object, use the **Get-Date** cmdlet. Specify the date and time according to your system locale settings. For more information, type `Get-Help Get-Date`.

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
Specifies an email address. The cmdlet gets the tracking log files for documents issued or requested by the user associated with this email address. 

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-Date](http://go.microsoft.com/fwlink/?LinkID=293966)
[ConvertFrom-Json] (https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-4.0)
[Export-Csv] (https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-4.0)
