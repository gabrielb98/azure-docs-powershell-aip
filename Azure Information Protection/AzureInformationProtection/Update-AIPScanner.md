---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=841550
schema: 2.0.0
---

# Update-AIPScanner

## SYNOPSIS
Updates the scanner to the latest DB schema

## SYNTAX

```
Update-AIPScanner [<CommonParameters>]
```

## DESCRIPTION
The Update-AIPScanner updates the scanner's DB schema after the package upgrade. This command must be executed once after the package upgrade in order to enable the scanner to run. The command must be executed using an account with dbowner rights on the AzInfoProtectionScanner DB.

## EXAMPLES

### Example 1: Update AIPscanner after the package upgrade
```powershell
PS C:\> Update-AIPScanner
```

AzInfoProtectionScanner is updated with the new schema.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.
For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS
