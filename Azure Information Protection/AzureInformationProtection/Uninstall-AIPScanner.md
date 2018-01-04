---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=858207
schema: 2.0.0
---

# Uninstall-AIPScanner

## SYNOPSIS
Uninstalls the Windows Server service for the Azure Information Protection scanner.

## SYNTAX

```
Uninstall-AIPScanner
```

## DESCRIPTION
The Uninstall-AIPScanner cmdlet uninstalls the Windows Server service, Azure Information Protection Scanner. This command does not remove the SQL Server database that was created by running the [Install-AIPScanner](./Install-AIPScanner.md) cmdlet when the Azure Information Protection scanner was installed. If this database is no longer required, you must manually remove it.

This command also does not remove the scanner reports located in %localappdata%\Microsoft\MSIP\Scanner\Reports.

To run this command, you must have local Administrator rights for the Windows Server computer and you must restart the computer after running the command to complete the removal process.


## EXAMPLES

### Example 1: Uninstall the Azure Information Protection Scanner service
```
PS C:\> Uninstall-AIPScanner

```

This command removes the service for the Azure Information Protection scanner.

## PARAMETERS

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)
