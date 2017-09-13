---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=858207
schema: 2.0.0
---

# Uninstall-AIPScanner

## SYNOPSIS
Uninstalls Azure Information Protection Scanner service.

## SYNTAX

```
Uninstall-AIPScanner
```

## DESCRIPTION
The Uninstall-AIPScanner cmdlet uninstalls Azure Information Protection Scanner service. The command removes Windows service, but doesn't remove the DB created by Install-AIPScanner service. Manual cleanup of the DB should be performed if required. 

In order to complete the command local administrator rights are required.

Note: Azure Information Protection Scanner is a preview feature. Scope of the feature and command syntax might change.

## EXAMPLES

### Example 1: Uninstall Azure Information Protection Scanner service
```
PS C:\> Uninstall-AIPScanner
```
Azure Information Protection Scanner service was removed successfully. Azure Information Protection Scanner DB was not removed and should be removed manually if needed.
Please restart the comouter in order to complete service removal.

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

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)