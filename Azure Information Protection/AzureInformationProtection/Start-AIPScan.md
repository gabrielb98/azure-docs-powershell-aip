---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=841549
schema: 2.0.0
---

# Start-AIPScan

## SYNOPSIS
Instructs AIP scanner to start one time scan 

## SYNTAX

```
Start-AIPScan [-Reset] [<CommonParameters>]
```

## DESCRIPTION
The Start-AIPScan instructs a running AIPscanner service set to Manual schedule to start a one time scan. The scan is started immediately. First scan evaluates all discovered files in the defined repositories. Any consequent scan scans only new or changed files unless the AIP policy was changed. 
If the policy was changed the scanner will initiate full rescan of file in next scan cycle. 

If you want to force full rescan of files without change of policy use -Reset switch to instruct the scanner to reset the scanner cache.

If the scanner schedule is set to Always, the command is ignored.

## EXAMPLES

### Example 1: Initiate immediate one time scan
```powershell
PS C:\> Start-AIPScan
```

The scanner initiates incremental scan of all new or changed files since the last scan. If the policy was changed since last scan full rescan will be done.

### Example 2: Force scanner to immediate one time rescan of all files in the defined repositories
```powershell
PS C:\> Start-AIPScan -Reset
```

The scanner initiates full rescan of all files since in the defined repositories.

## PARAMETERS

### -Reset
Resets scanner cache that enables scanner to scan only newly created or modified files since the last scan.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.
For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS
