---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=838765
schema: 2.0.0
---

# Get-AIPScannerConfiguration

## SYNOPSIS
Gets Azure Information Protection Scanner service configuration

## SYNTAX

```
Get-AIPScannerConfiguration
```

## DESCRIPTION
The Set-AIPScanner cmdlet gets Azure Information Protection Scanner service configuration. Azure Information Protection Scanner includes settings for scan mode, report level, schedule etc.

## EXAMPLES

### Example 1: Gets current Azure Information Protection Scanner configuration
```
PS C:\> Get-AIPScannerConfiguration
```

ScanMode             : Discover
OverrideLabel        : AppliedByScanner
PreserveFileDetails  : On
ReportLevel          : Info
Schedule             : OneTime
JustificationMessage : Reclassified by Azure Information Protection Scanner
DefaultOwner         :


## PARAMETERS

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

