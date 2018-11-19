---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400607
schema: 2.0.0
ms.assetid: D7136388-0197-4074-AC15-BA4DA07223C7
---

# Get-AadrmAdminLog

## SYNOPSIS
Generates logs for all Rights Management administrative commands.

## SYNTAX

```
Get-AadrmAdminLog -Path <String> [-FromTime <DateTime>] [-ToTime <DateTime>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Get-AadrmAdminLog** cmdlet generates logs for all Rights Management administrative commands. You can specify a start time and stop time of entries to include.

You must use PowerShell to get these admin logs; you cannot do this action by using a management portal.

## EXAMPLES

### Example 1: Generate a log of all commands
```
PS C:\>Get-AadrmAdminLog -Path "C:\Temp\AdminLog.log"
```

This command generates a log that contains all the Rights Management administrative commands that have been run for your organization's Azure Rights Management service.

### Example 2: Generate a log of commands for a specified time period
```
PS C:\>Get-AadrmAdminLog -Path "C:\Temp\AdminLog.log" -FromTime "05/01/2015 00:00:00" -ToTime "05/31/2015 23:59:59"
```

This command generates a log of administrative commands for your Azure RMS tenant, limited to items that fall within the specific time period by using the *FromTime* and *ToTime* parameters. In this example, the time period is all days in May 2015, using the US date format.

### Example 3: Generate a log of commands for the last 45 days
```
PS C:\>$days = (Get-Date).AddDays(-45) 
PS C:\>Get-AadrmAdminLog -Path "C:\Temp\AdminLog.log" -FromTime $days
```

This command generates a log of administrative commands for your Azure RMS tenant, limited to items within the last 45 days (inclusive). The first command sets the variable for the *FromTime* parameter to be today's date minus 45 days. Then the second command gets the entries from the log for this time period, by using this variable.

## PARAMETERS

### -Force
Indicates that the cmdlet overwrites, without prompting for confirmation, an existing log file that has the same path.

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

### -Path
Specifies an existing path and a file name for the log.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-Date](http://go.microsoft.com/fwlink/?LinkID=293966)
