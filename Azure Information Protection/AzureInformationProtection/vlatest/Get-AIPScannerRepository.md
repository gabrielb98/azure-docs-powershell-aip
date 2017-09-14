---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=858210
schema: 2.0.0
---

# Get-AIPScannerRepository

## SYNOPSIS
Gets a list of data repositories that the Azure Information Protection scanner is configured to scan.

## SYNTAX

```
Get-AIPScannerRepository
```

## DESCRIPTION
The Get-AIPScannerRepository cmdlet gets the list of data repositories that the Azure Information Protection scanner is configured to scan. These data repositories are specified by using the [Add-AIPScannerRepository](./Add-AIPScannerRepository) cmdlet. 

Tip: You can use the output of this cmdlet with [Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md) to clean up the list of the data repositories for the scanner. For example: Add-AIPScannerRepository | Remove-AIPScannerRepository

## EXAMPLES

### Example 1: Get the list of the current data repositories
```
PS C:\> Get-AIPScannerRepository

http://sp2016.res.local/Shared Documents/Folder
http://sp2013/Documents
\\server1\HR
d:\Data\Finance
```

This command gets the list of the data repositories that the Azure Information Protection scanner is currently configured to scan. The list displays two paths from SharePoint Server, a file server share, and a local disk and folder.

## PARAMETERS

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Set-AIPScanner](./Set-AIPScanner.md)
