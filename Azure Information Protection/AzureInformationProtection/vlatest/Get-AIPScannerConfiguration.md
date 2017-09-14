---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=858206
schema: 2.0.0
---

# Get-AIPScannerConfiguration

## SYNOPSIS
Gets the optional configuration for the Azure Information Protection scanner.

## SYNTAX

```
Get-AIPScannerConfiguration
```

## DESCRIPTION
The Get-AIPScannerConfiguration cmdlet gets the optional configuration for the Azure Information Protection scanner, which was configured by using the [Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md) cmdlet. The optional configuration that you can set is the scan mode, the schedule, label override settings, the justification message, preserve file details, the report level, and the default owner.

## EXAMPLES

### Example 1: Gets the optional configuration for the Azure Information Protection scanner

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

This command gets the the optional configuration for the Azure Information Protection scanner. The configuration displayed includes the scan mode of discovery, file details are preserved, and successfully labeled files are reported. 

## PARAMETERS

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)