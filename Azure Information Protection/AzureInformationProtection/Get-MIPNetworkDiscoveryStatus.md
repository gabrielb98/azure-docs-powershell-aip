---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2137917
schema: 2.0.0
---

# Get-MIPNetworkDiscoveryStatus

## SYNOPSIS
Gets the current status of the Network Discovery service.

## SYNTAX

```
Get-MIPNetworkDiscoveryStatus [<CommonParameters>]
```

## DESCRIPTION

The **Get-MIPNetworkDiscoveryStatus** cmdlet returns the current status of the Network Discovery service.

Network Discovery network scan jobs enable Azure Information Protection administrators to scan specific IP addresses or ranges for risky repositories to add to scan further with content scan jobs.

Possible statuses include:

- **Offline:** The service is not started.
- **Idle:** The service is running but not currently scanning. 
- **Scanning:** The service is running and currently scanning the network.
- **Error:** The service is running but it has encountered an error that prevents it from scanning files. For example, the service cannot access the database for the scanner configuration.

## EXAMPLES

### Example 1: Service idle
```powershell
PS C:\> Get-MIPNetworkDiscoveryStatus

NodeName                              Status           Jobs
--------                              -------------    -------------
msanchez-3384.emea.corp.contoso.com   Idle    

```

This command gets the current status of the Network Discovery service.

The output shows that the Network Discovery scanner service is running, but not currently scanning. 

### Example 1: Service scanning
```powershell
PS C:\> Get-MIPNetworkDiscoveryStatus

NodeName                              Status           Jobs
--------                              -------------    -------------
msanchez-3384.emea.corp.contoso.com   Scanning         39gsneaoz-d944-4fns-9b2f-ej6g350cd74    

```

This command gets the current status of the Network Discovery service.

The output shows that the Network Discovery scanner service is currently running, and performing job ID **39gsneaoz-d944-4fns-9b2f-ej6g350cd74.**

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

[Get-MIPNetworkDiscoveryJobs](Get-MIPNetworkDiscoveryJobs.md)

[Import-MIPNetworkDiscoveryConfiguration](Import-MIPNetworkDiscoveryConfiguration.md)

[Install-MIPNetworkDiscovery](Install-MIPNetworkDiscovery.md)

[Set-MIPNetworkDiscovery](Set-MIPNetworkDiscovery.md)

[Set-MIPNetworkDiscoveryConfiguration](Set-MIPNetworkDiscoveryConfiguration.md)

[Start-MIPNetworkDiscovery](Start-MIPNetworkDiscovery.md)

[Uninstall-MIPNetworkDiscovery](Uninstall-MIPNetworkDiscovery.md)