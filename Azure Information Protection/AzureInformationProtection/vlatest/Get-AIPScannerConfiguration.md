---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=858206
schema: 2.0.0
---

# Get-AIPScannerConfiguration

## SYNOPSIS
Gets the configuration settings for the Azure Information Protection scanner.

## SYNTAX

```
Get-AIPScannerConfiguration
```

## DESCRIPTION
The Get-AIPScannerConfiguration cmdlet gets the configuration settings for the Azure Information Protection scanner. Most of the settings install with a default value, so you need to specify them only if you want to use another value, or you have previously set them and now need to reconfigure them. To do so, use the [Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md) cmdlet. 

The configuration settings include whether the scanner is in discovery mode only or applies labels, whether a file will be relabeled, whether file attributes are changed, what is logged in the reports, whether the scanner runs once or continuously, what justification message to use when required, and the Rights Management owner for protected files.

Note: This cmdlet is in preview and requires the current preview version of the Azure Information Protection client.

## EXAMPLES

### Example 1: Gets the configuration for the Azure Information Protection scanner

```
PS C:\> Get-AIPScannerConfiguration

ScanMode             : Discover
OverrideLabel        : AppliedByScanner
PreserveFileDetails  : On
ReportLevel          : Info
Schedule             : OneTime
JustificationMessage : Reclassified by Azure Information Protection Scanner
DefaultOwner         :

```

This command gets the current configuration settings for the Azure Information Protection scanner. In this example, the output shows that the scanner is using the installation default values. The one exception is the justification message, which has been specified.

- The scanner is in discovery mode for reporting purposes only. Labels are not applied to files.

- The scanner will apply a different label to a file that is already labeled only when these files have been labeled by the current scanner account.

- The scanner will not overwrite file attributes when a file is labeled.

- The reports contains details of files that were successfully labeled.
 
- The scanner will run one time and then stop the service, rather than run continuously.

- The string "Reclassified by Azure Information Protection Scanner" is supplied and logged when the scanner applies a label that requires justification.

- No specific account is specified for the Owner custom property or the Rights Management owner. Instead, default values are used when a file is classified, and protected.

## PARAMETERS

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)
