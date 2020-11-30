---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2137624
schema: 2.0.0
---

# Get-MIPNetworkDiscoveryConfiguration

## SYNOPSIS
Gets configuration settings for the Network Discovery service. 

## SYNTAX

```
Get-MIPNetworkDiscoveryConfiguration [<CommonParameters>]
```

## DESCRIPTION

The **Get-MIPNetworkDiscoveryConfiguration** cmdlet gets configuration settings for the Network Discovery service.

The Network Discovery service manages network scan jobs, and enable Azure Information Protection administrators to scan specific IP addresses or ranges for risky repositories. Administrators may want to add these repositories to content scan jobs to scan their content further.

The **Get-MIPNetworkDiscoveryConfiguration** cmdlet displays only the settings and values that you can configure with [**Set-MIPNetworkDiscoveryConfiguration**](./Set-MIPNetworkDiscoveryConfiguration.md) cmdlet. This includes only whether the Network Discovery service settings are taken from the online configuration currently in the Azure portal, or from a file that was exported from the Azure portal.

> [!TIP]
> Run [Import-MIPNetworkDiscoveryConfiguration](./Import-MIPNetworkDiscoveryConfiguration.md) to configure the scanner to get Network Discovery service settings from an offline file. When you run **Get-MIPNetworkDiscoveryConfiguration** after importing settings from a file, the **OnlineConfiguration** is displayed as **Off**.

## EXAMPLES

### Example 1
```powershell
PS C:\> Get-MIPNetworkDiscoveryConfiguration

OnlineConfiguration      : On
```

This command gets the current PowerShell configuration settings for the Network Discovery service. In this example, the output shows that the scanner is using the default configuration of using the online configuration from the Azure portal.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS


[Get-MIPNetworkDiscoveryJobs](Get-MIPNetworkDiscoveryJobs.md)

[Get-MIPNetworkDiscoveryStatus](Get-MIPNetworkDiscoveryStatus.md)

[Import-MIPNetworkDiscoveryConfiguration](Import-MIPNetworkDiscoveryConfiguration.md)

[Install-MIPNetworkDiscovery](Install-MIPNetworkDiscovery.md)

[Set-MIPNetworkDiscovery](Set-MIPNetworkDiscovery.md)

[Set-MIPNetworkDiscoveryConfiguration](Set-MIPNetworkDiscoveryConfiguration.md)

[Start-MIPNetworkDiscovery](Start-MIPNetworkDiscovery.md)

[Uninstall-MIPNetworkDiscovery](Uninstall-MIPNetworkDiscovery.md)