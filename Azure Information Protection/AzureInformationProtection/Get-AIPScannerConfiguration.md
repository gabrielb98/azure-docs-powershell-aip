---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=858206
schema: 2.0.0
---

# Get-AIPScannerConfiguration

## SYNOPSIS
Gets the configuration settings for the Azure Information Protection scanner.

## SYNTAX

```
Get-AIPScannerConfiguration [<CommonParameters>]
```

## DESCRIPTION
The Get-AIPScannerConfiguration cmdlet gets the configuration settings for the Azure Information Protection scanner. Most of the settings install with a default value, so you need to specify them only if you want to use another value, or you have previously set them and now need to reconfigure them. To do so, use the [Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md) cmdlet.

The configuration settings include whether the scanner is in discovery mode only or applies labels, whether a file will be relabeled, whether file attributes are changed, what is logged in the reports, whether the scanner runs once or continuously, whether all files are scanned or only new and changed files, what justification message to use when required, and the Rights Management owner for protected files.

## EXAMPLES

### Example 1a: Gets the configuration for the Azure Information Protection scanner - GA version
```
PS C:\> Get-AIPScannerConfiguration

Enforce	                 : Off
ReportLevel              : Info
Schedule                 : OneTime
Type                     : Full
JustificationMessage     : Reclassified by Azure Information Protection Scanner
DiscoverInformationTypes : PolicyOnly
ScannedFileTypes         : *,"-.lnk","-.exe","-.com","-.cmd","-.bat","-.dll","-.ini","-.pst","-.sca","-.drm","-.sys","-.cpl","-.inf","-.drv","-.dat","-.tmp","-.msp","-.msi","-.pdb","-.jar"
```

This command gets the current configuration settings for the Azure Information Protection scanner. In this example, the output shows that the scanner is using the installation default values. The one exception is the justification message, which has been specified.

- The scanner is in discovery mode for reporting purposes only. Labels are not applied to files.
- The reports contains details of files that were successfully labeled.
- The scanner will run one time and then stop the service, rather than run continuously.
- The scanner will run discovery on all files
- The string "Reclassified by Azure Information Protection Scanner" is supplied and logged when the scanner applies a label that requires justification.
- The scanner looks for conditions and patterns that are defined in your Azure Information Protection policy
- The scanner includes all file types to scan, except for the default file types that the Azure Information Protection client excludes by default.


### Example 1b: Gets the configuration for the Azure Information Protection scanner - preview version
```
PS C:\> Get-AIPScannerConfiguration

Enforce	                 : Off
ReportLevel              : Info
Schedule                 : Manual
JustificationMessage     : Reclassified by Azure Information Protection Scanner
DiscoverInformationTypes : PolicyOnly
ScannedFileTypes         : *,"-.lnk","-.exe","-.com","-.cmd","-.bat","-.dll","-.ini","-.pst","-.sca","-.drm","-.sys","-.cpl","-.inf","-.drv","-.dat","-.tmp","-.msp","-.msi","-.pdb","-.jar"
```

This command gets the current configuration settings for the Azure Information Protection scanner. In this example, the output shows that the scanner is using the installation default values. The one exception is the justification message, which has been specified.

- The scanner is in discovery mode for reporting purposes only. Labels are not applied to files.
- The reports contains details of files that were successfully labeled.
- The scanner will run one time when it's manually started. 
- The string "Reclassified by Azure Information Protection Scanner" is supplied and logged when the scanner applies a label that requires justification.
- The scanner looks for conditions and patterns that are defined in your Azure Information Protection policy
- The scanner includes all file types to scan, except for the default file types that the Azure Information Protection client excludes by default.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.
For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Add-AIPScannerScannedFileTypes](Add-AIPScannerScannedFileTypes.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)

[Get-AIPScannerStatus](./Get-AIPScannerStatus.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Remove-AIPScannerScannedFileTypes](./Remove-AIPScannerScannedFileTypes.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Set-AIPScannerRepository](./Set-AIPScannerRepository.md)

[Set-AIPScannerScannedFileTypes](./Set-AIPScannerRepository.md)

[Start-AIPScan](./Start-AIPScan.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Update-AIPScanner](./Update-AIPScanner.md)

