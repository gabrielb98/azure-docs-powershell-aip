---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2137918
schema: 2.0.0
---

# Import-MIPNetworkDiscoveryConfiguration

## SYNOPSIS
Imports a local configuration for Network Discovery network scan jobs.

## SYNTAX

```
Import-MIPNetworkDiscoveryConfiguration -FileName <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

The **Import-MIPNetworkDiscoveryConfiguration** cmdlet imports local configuration settings for the Azure Information Protection network scan jobs, and automatically configures the scanner to use the offline configuration. 

Network Discovery network scan jobs enable Azure Information Protection administrators to scan specific IP addresses or ranges for risky repositories to add to scan further with content scan jobs.

- Use this cmdlet only after you have configured a cluster and a network scan job in the Azure portal, and exported those settings to a file. 

- If you need to make configuration changes to the network scan jobs after you have run this cmdlet, make those changes in the Azure portal, export the network scan job again, and rerun this cmdlet.

If you want to change the scanner to use the online configuration directly after you have run this cmdlet, use the [Set-MIPNetworkDiscoveryConfiguration](./Set-MIPNetworkDiscoveryConfiguration.md) and set the *OnlineConfiguration* parameter to **On**.

Any changes will be used the next time the scanner runs. If you need the changes to take effect immediately, restart the Azure Information Protection Scanner service on the Windows server computer.


## EXAMPLES

### Example 1: Import a locally configured Azure Information Protection network scan job

```powershell
PS C:\> Import-MIPNetworkDiscoveryConfiguration -FileName "C:/configuration.json"

Configuration was imported successfully.
```

In this example, the scanner is configured to prevent getting network scan job settings directly from the Azure portal. Instead, the network scan job is imported from a file named C:/configuration.json.

## PARAMETERS

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FileName
Specifies a file that contains network scan job configuration settings. To create this file, export your network scan job from the Azure portal.

The file is used to do a one-time import of network scan job settings into the scanner configuration database.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

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

[Install-MIPNetworkDiscovery](Install-MIPNetworkDiscovery.md)

[Set-MIPNetworkDiscovery](Set-MIPNetworkDiscovery.md)

[Set-MIPNetworkDiscoveryConfiguration](Set-MIPNetworkDiscoveryConfiguration.md)

[Start-MIPNetworkDiscovery](Start-MIPNetworkDiscovery.md)

[Uninstall-MIPNetworkDiscovery](Uninstall-MIPNetworkDiscovery.md)