---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=858210
schema: 2.0.0
---

# Get-AIPScannerRepository

## SYNOPSIS
Gets a list of repositores scanned by Azure Information Protection Scanner

## SYNTAX

```
Get-AIPScannerRepository
```

## DESCRIPTION
The Get-AIPScannerRepository gets a list of repositores scanned by Azure Information Protection Scanner. You can use the command as a pipe for Remove-AIPScannerRepository in order to cleanup the list of the repositores

## EXAMPLES

### Example 1: Get list of current repositores
```
PS C:\> Get-AIPScannerRepository
```
http://sp2016.res.local/Shared Documents/Folder
http://sp2013/Documents
\\server1\HR
d:\data\Finance


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
