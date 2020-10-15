---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2137527
schema: 2.0.0
---

# Set-MIPNetworkDiscoveryConfiguration

## SYNOPSIS
Sets optional configurations for the Network Discovery service.

## SYNTAX

```
Set-MIPNetworkDiscoveryConfiguration [-OnlineConfiguration <OnlineConfiguration>] [<CommonParameters>]
```

## DESCRIPTION
The **Set-MIPNetworkDiscoveryConfiguration** cmdlet sets local configuration settings for the Network Discovery service.

The Network Discovery service manages network scan jobs, and enables Azure Information Protection administrators to scan specific IP addresses or ranges for risky repositories. Administrators may want to add these repositories to content scan jobs and scan their content further.

While most of the network scan job settings are configured in the Azure portal, you must use this cmdlet if you need to import configuration settings from a file because the deployment cannot support online configuration.

Any changes will be used the next time the network scan jobs run. If you need the changes to take effect immediately, restart the Network Discovery service on the Windows server computer.

## EXAMPLES

### Example 1: Set the Network Discovery service to use online configuration

``` powershell
PS C:\> Set-AIPScannerConfiguration -OnlineConfiguration On

Configuration was set successfully.
```

This command sets the Network Discovery service to get its configuration directly from the settings configured online in the Azure portal.


## PARAMETERS

### -OnlineConfiguration
Specifies whether the scanner gets its configuration settings directly from the Azure portal, or uses an offline configuration file.

- **On:** The default setting. The scanner gets its configuration settings directly from the Azure portal.

- **Off:** The Network Discovery service is prevented from getting its configuration settings directly from the Azure portal. Instead, the scanner is configured by settings that you import from a file. 

If the scanner cannot support online configuration, you must still configure the network scan jobs in the Azure portal. Then, export the network scan job configuration from the portal to a **.json** file and import this file by using the [Import-**Import-MIPNetworkDiscoveryConfiguration**](./Import-MIPNetworkDiscoveryConfiguration.md) cmdlet.

```yaml
Type: OnlineConfiguration
Parameter Sets: (All)
Aliases:
Accepted values: On, Off

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

### None

## OUTPUTS

### System.Object
## NOTES

## RELATED LINKS
[Get-MIPNetworkDiscoveryConfiguration](Get-MIPNetworkDiscoveryConfiguration.md)

[Get-MIPNetworkDiscoveryJobs](Get-MIPNetworkDiscoveryJobs.md)

[Get-MIPNetworkDiscoveryStatus](Get-MIPNetworkDiscoveryStatus.md)

[Import-MIPNetworkDiscoveryConfiguration](Import-MIPNetworkDiscoveryConfiguration.md)

[Install-MIPNetworkDiscovery](Install-MIPNetworkDiscovery.md)

[Start-MIPNetworkDiscovery](Start-MIPNetworkDiscovery.md)

[Uninstall-MIPNetworkDiscovery](Uninstall-MIPNetworkDiscovery.md)