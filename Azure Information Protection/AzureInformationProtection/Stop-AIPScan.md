---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2132508
schema: 2.0.0
---

# Stop-AIPScan

## SYNOPSIS
**Relevant for:** Unified labeling client only

Instructs the Azure Information Protection scanner to stop the currently running scan cycle.

## SYNTAX
```
Stop-AIPScan
```

## DESCRIPTION
The **Stop-AIPScan** cmdlet stops an active scan for the current profile.

Stopping an active scan does not pause the scan cycle. Instead, it completely stops and cancels the scan, and shifts all scanners to idle mode until a new scan is requested.

When the new scan starts, it does not continue from the previous scan state, although the new scan does skip all files already scanned.

> [!NOTE]
> It may take up to five minutes until all scanners receive the stop command.

> [!TIP]
> If you want to pause a scan and have it start again from the same point, stop the Azure Information Protection Scanner service on the scanner machine instead.
> 
## EXAMPLES

### Example 1: Stop the currently running scan cycle
```PowerShell
PS C:\> Stop-AIPScan
```

## INPUTS

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS
[Start-AIPScan](Start-AIPScan.md)