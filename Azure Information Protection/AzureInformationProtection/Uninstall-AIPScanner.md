---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=858207
schema: 2.0.0
---

# Uninstall-AIPScanner

## SYNOPSIS
**Relevant for:** AIP unified labeling and classic clients

Uninstalls the Windows Server service for the Azure Information Protection scanner.

## SYNTAX

```
Uninstall-AIPScanner [<CommonParameters>]
```

## DESCRIPTION
The **Uninstall-AIPScanner** cmdlet uninstalls the Azure Information Protection Scanner Windows Server service. 

To run this command, you must have local Administrator rights for the Windows Server computer and you must restart the computer after running the command to complete the removal process.

This command does *not* remove the following:

- **Scanner reports**, located in **%localappdata%\Microsoft\MSIP\Scanner\Reports**.

- **The SQL Server database** that was created by running the [Install-AIPScanner](./Install-AIPScanner.md) cmdlet when the Azure Information Protection scanner was installed. If this database is no longer required, you must manually remove it. 

    This database is named as follows:

    |Client  |Instructions  |
    |---------|---------|
    |**Unified labeling client**     |  For the AIP unified labeling client, the database name for the scanner is **AIPScannerUL_\<cluster_name>**.       |
    |**Classic client**     |  For the AIP classic client, the default database name for the scanner is **AIPScanner_\<computer_name>** but when you specify a profile name, the database name for the scanner changes to **AIPScanner_\<profile_name)>**.       |
    | | |


[!INCLUDE [The AIP classic client is sunset](../includes/classic-client-sunset.md)]


## EXAMPLES

### Example 1: Uninstall the Azure Information Protection Scanner service
```
PS C:\> Uninstall-AIPScanner
```

This command removes the service for the Azure Information Protection scanner.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. 

For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

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

[Update-AIPScanner](./Update-AIPScanner.md)