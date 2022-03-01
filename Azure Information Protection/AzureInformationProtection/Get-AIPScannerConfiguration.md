---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=858206
schema: 2.0.0
---

# Get-AIPScannerConfiguration

## SYNOPSIS
**Relevant for:** AIP unified labeling and classic clients

Gets the configuration settings for the Azure Information Protection scanner.

## SYNTAX

```
Get-AIPScannerConfiguration [<CommonParameters>]
```

## DESCRIPTION
This cmdlet is supported by both the Azure Information Protection classic and unified labeling clients, with different usage, as described below.

The **Get-AIPScannerConfiguration** cmdlet gets the configuration settings for the Azure Information Protection scanner. 

If you run [Import-AIPScannerConfiguration](./Import-AIPScannerConfiguration.md), this action automatically configures the scanner to get its configuration offline. As a result, when you run this Get-AIPScannerConfiguration cmdlet after importing settings from a file, **OnlineConfiguration** displays **Off**. 

[!INCLUDE [The AIP classic client is sunset](../includes/classic-client-sunset.md)]


## EXAMPLES

### Example 1: Gets the configuration for the Azure Information Protection scanner (unified labeling client)
```
PS C:\> Get-AIPScannerConfiguration
OnlineConfiguration : On
ReportLevel         : Info
LogLevel            : Trace
Cluster             : contoso-test
SqlInstance         : localhost\sqlexpress
DatabaseName        : AIPScannerUL_contoso-test
Cloud               : Commercial
```

This command gets the current PowerShell configuration settings for the Azure Information Protection unified labeling scanner. 

In this example, the output shows that the scanner is using the default configuration for online configuration, the report level of **Info**, and a logging level of **Trace**. The cluster name, SQL instance, and database names are listed, and the cloud type is **Commercial**.

### Example 2: Gets the configuration for the Azure Information Protection scanner (classic client)
```
PS C:\> Get-AIPScannerConfiguration

OnlineConfiguration      : On
ReportLevel              : Info
```

This command gets the current PowerShell configuration settings for the Azure Information Protection scanner. In this example, the output shows that the scanner is using the default configuration for online configuration and the report level of information.


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

[Get-AIPScannerStatus](./Get-AIPScannerStatus.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Start-AIPScan](./Start-AIPScan.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Update-AIPScanner](./Update-AIPScanner.md)