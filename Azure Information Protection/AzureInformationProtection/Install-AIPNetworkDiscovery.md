---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2053104
schema: 2.0.0
---

# Install-AIPNetworkDiscovery

## SYNOPSIS
Installs the Azure Information Protection (AIP) Network Discovery service.

## SYNTAX

```
Install-AIPNetworkDiscovery 
```

## DESCRIPTION
The Install-AIPNetworkDiscovery cmdlet installs the Network Discovery service, which enables AIP administrators to scan a specified IP address or range for possibly risky repositories, using a network scan job.

Use network scan job results to identify additional repositories in your network to further scan using a content scan job.

## EXAMPLES

```powershell
PS C:\> Install-AIPNetworkDiscovery 
Configuration was imported successfully.

```

## PARAMETERS

### None

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
