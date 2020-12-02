---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2137526
schema: 2.0.0
---

# Get-MIPNetworkDiscoveryJobs

## SYNOPSIS
**Relevant for:** AIP unified labeling client only

Gets a list of Azure Information Protection network scan jobs configured in your tenant.

## SYNTAX

```
Get-MIPNetworkDiscoveryJobs [<CommonParameters>]
```

## DESCRIPTION
The **Get-MIPNetworkDiscoveryJobs** cmdlet gets a list of the Network Discovery network scan jobs configured in your tenant.

Network Discovery network scan jobs enable Azure Information Protection administrators to scan specific IP addresses or ranges for risky repositories to add to scan further with content scan jobs.

## EXAMPLES

### Example 1
```PowerShell
PS C:\> Get-MIPNetworkDiscoveryJobs

JobID       : 496ca93c-ba49-497b-a527-62ffd980891ea
IpRanges    : [{"Start":"10.90.208.62", "End":"10.90.208.62"}]
LastScanned : 8/2/2020 1:13:16 PM
NodeName    : msanchez-7060-emea.corp.contoso.com
StartTime   : 
Status      : Idle
Schedule    : Weekly Mon,Wed 

JobID       : 40zaw385-o28c-398k-i482-43o2xcggsejsz
IpRanges    : [{"Start":"88.205.56.230", "End":"88.205.56.230"}]
LastScanned : 9/4/2020 1:13:16 PM
NodeName    : 
StartTime   : 
Status      : Idle
Schedule    : Monthly 4

JobID       : v7r05qqh-eb2z-2enz-3o2n-a85w1eji3vagv
IpRanges    : [{"Start":"183.118.20.113", "End":"183.118.20.113"}]
LastScanned : 10/13/2020 1:13:16 PM
NodeName    : msanchez-7060-emea.corp.contoso.com
StartTime   : 
Status      : Idle
Schedule    : Weekly Sun 
```

This command gets the list of the three Network Discovery network scan jobs, as configured in the Azure portal.

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

[Get-MIPNetworkDiscoveryConfiguration](Get-MIPNetworkDiscoveryConfiguration.md)

[Get-MIPNetworkDiscoveryStatus](Get-MIPNetworkDiscoveryStatus.md)

[Import-MIPNetworkDiscoveryConfiguration](Import-MIPNetworkDiscoveryConfiguration.md)

[Install-MIPNetworkDiscovery](Install-MIPNetworkDiscovery.md)

[Set-MIPNetworkDiscovery](Set-MIPNetworkDiscovery.md)

[Set-MIPNetworkDiscoveryConfiguration](Set-MIPNetworkDiscoveryConfiguration.md)

[Start-MIPNetworkDiscovery](Start-MIPNetworkDiscovery.md)

[Uninstall-MIPNetworkDiscovery](Uninstall-MIPNetworkDiscovery.md)