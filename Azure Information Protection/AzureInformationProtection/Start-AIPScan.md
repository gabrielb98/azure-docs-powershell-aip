---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2004364
schema: 2.0.0
---

# Start-AIPScan

## SYNOPSIS
**Relevant for:** Unified labeling client only

Instructs the Azure Information Protection scanner to start a one-time scan cycle. 

## SYNTAX

```
Start-AIPScan [-Reset] [-Force] [<CommonParameters>]
```

## DESCRIPTION
The **Start-AIPScan** cmdlet instructs the Azure Information Protection scanner to immediately start a one-time scan cycle. The scanner service must be started already and the scanner schedule must be configured for a manual schedule. 

To configure the schedule, use the [Azure portal to configure the scanner](/azure/information-protection/deploy-aip-scanner).

By default, all files are scanned the first time the scanner runs and then, unless the Azure Information Protection policy is changed, only new or changed files are scanned. However, you can change this behavior when you use the *-Reset* parameter with this cmdlet, which forces the scanner to scan all files.
  
> [!NOTE]
> If the scanner schedule is set to **Always,** this cmdlet is ignored.
> 
## EXAMPLES

### Example 1: Initiate immediate one-time scan for new and changed files
```PowerShell
PS C:\> Start-AIPScan
```

Because this is not the first time that the scanner has run and the Azure Information Protection policy has not changed since the last scanning cycle, the scanner initiates an incremental scan for all new or changed files since the last scanning cycle.

### Example 2: Initiate immediate one time scan for all files
```PowerShell
PS C:\> Start-AIPScan -Reset
```

The scanner initiates a full scan of all the files, even if they have been scanned before and the Azure Information Protection policy has not changed.

## PARAMETERS

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
### -Reset
Resets the scanner cache so that the scanner initiates a full scan of all the files, even if they have been scanned before and the Azure Information Protection policy has not changed.

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

For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Get-AIPScannerStatus](./Get-AIPScannerStatus.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Update-AIPScanner](./Update-AIPScanner.md)