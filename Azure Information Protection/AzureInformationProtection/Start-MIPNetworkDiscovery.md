---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2137919
schema: 2.0.0
---

# Start-MIPNetworkDiscovery

## SYNOPSIS
Instructs the Azure Information Protection scanner to start a network scan job.

## SYNTAX

```
Start-MIPNetworkDiscovery -JobId <Guid> [<CommonParameters>]
```

## DESCRIPTION
The **Start-MIPNetworkDiscovery** cmdlet instructs the Azure Information Protection scanner to immediately start a specified network scan job. 

Network scan jobs enables AIP administrators to scan a specified IP address or range for possibly risky repositories. Administrators may want to add these repositories to a content scan job to further scan their contents.

The scanner's Network Discovery service must be started before you can run this cmdlet.

## EXAMPLES

### Example 1
```powershell
PS C:\> 
Start-MIPNetworkDiscovery -JobId f7715158-dc9e-40d5-b78e-9c93a8c30577
```
This example runs the network scan job with a job GUID of **f7715158-dc9e-40d5-b78e-9c93a8c30577.** 

## PARAMETERS

### -Force
Forces the command to run without asking for user confirmation.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```
### -JobId
The network scan job GUID. 

This parameter is mandatory. Get the network scan job GUID by using the [Get-MIPNetworkDiscoveryJobs](Get-MIPNetworkDiscoveryJobs.md) cmdlet.

```yaml
Type: Guid
Parameter Sets: (All)
Aliases:

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

[Set-MIPNetworkDiscovery](Set-MIPNetworkDiscovery.md)

[Set-MIPNetworkDiscoveryConfiguration](Set-MIPNetworkDiscoveryConfiguration.md)

[Uninstall-MIPNetworkDiscovery](Uninstall-MIPNetworkDiscovery.md)