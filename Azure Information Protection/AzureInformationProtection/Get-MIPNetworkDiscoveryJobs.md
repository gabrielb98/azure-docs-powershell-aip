---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2137526
schema: 2.0.0
---

# Get-MIPNetworkDiscoveryJobs

## SYNOPSIS
Gets a list of Azure Information Protection network scan job configured in your tenant.

## SYNTAX

```
Get-MIPNetworkDiscoveryJobs [<CommonParameters>]
```

## DESCRIPTION

The **Get-MIPNetworkDiscoveryJobs** cmdlet gets a list of Azure Information Protection network scan job configured in your tenant.

Network Discovery network scan jobs enable Azure Information Protection administrators to scan specific IP addresses or ranges for risky repositories to add to scan further with content scan jobs.

## EXAMPLES

### Example 1
```powershell
PS C:\> Get-MIPNetworkDiscoveryJobs
```

This command gets a list of all Azure Information Protection network discovery jobs configured in the Azure portal.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object
## NOTES

## RELATED LINKS

[Get-MIPNetworkDiscoveryConfiguration](Get-MIPNetworkDiscoveryConfiguration.md)

[Get-MIPNetworkDiscoveryStatus](Get-MIPNetworkDiscoveryStatus.md)

[Import-MIPNetworkDiscoveryConfiguration](Import-MIPNetworkDiscoveryConfiguration.md)

[Install-MIPNetworkDiscovery](Install-MIPNetworkDiscovery.md)

[Set-MIPNetworkDiscoveryConfiguration](Set-MIPNetworkDiscoveryConfiguration.md)

[Start-MIPNetworkDiscovery](Start-MIPNetworkDiscovery.md)

[Uninstall-MIPNetworkDiscovery](Uninstall-MIPNetworkDiscovery.md)