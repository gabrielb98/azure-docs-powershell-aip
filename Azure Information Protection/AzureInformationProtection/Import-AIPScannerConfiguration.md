---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2053104
schema: 2.0.0
---

# Import-AIPScannerConfiguration

## SYNOPSIS
Imports local configuration for the Azure Information Protection scanner.

## SYNTAX

```
Import-AIPScannerConfiguration -FileName <String> [<CommonParameters>]
```

## DESCRIPTION
Note: This cndlet is available only in the preview version of the scanner.

The Import-AIPScannerConfiguration cmdlet imports local configuration settings for the Azure Information Protection scanner. When you install the scanner, settings are configured for you with their default installation values. You can configure most of the scanner configuration settings in the Azure portal. However, you must use this cmdlet if you need to import configuration settings from a file because the scanner cannot support online configuration.

Any changes will be used the next time the scanner runs. If you need the changes to take effect immediately, restart the Azure Information Protection Scanner service on the Windows server computer.

## EXAMPLES

### Example 1: Import local configuration settings for the Azure Information Protection scanner
```powershell
PS C:\> Import-AIPScannerConfiguration -FileName "C:\Scannerconfig\Eu-set.json"
Configuration was imported successfully.

```

The scanner is configured to prevent getting its configuration directly from the Azure Information Protection service, and the configuration settings are imported from a file named C:\Scannerconfig\Eu-set.json.

## PARAMETERS

### -FileName
Specifies a file that contains scanner configuration settings that are exported from the Azure portal.

The file is used to do a one-time import of configuration settings into the scanner configuration database. 


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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.
For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

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

[Start-AIPScan](./Start-AIPScan.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Update-AIPScanner](./Update-AIPScanner.md)
