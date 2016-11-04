---
external help file: RMSProtection.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkID=623202
schema: 2.0.0
ms.assetid: 3E2190DA-3B41-4107-8F45-9EEA7A3DF3AA
---

# Get-RMSServer

## SYNOPSIS
Gets a list of RMS servers that can issue templates.

## SYNTAX

```
Get-RMSServer [<CommonParameters>]
```

## DESCRIPTION
The **Get-RMSServer** cmdlet returns a list of RMS servers that can issue rights policy templates to apply Rights Management protection.
This cmdlet is not relevant to Azure RMS and not necessary if you have a single Active Directory Rights Management Services (AD RMS) deployment.
Use this cmdlet when you have multiple deployments of AD RMS, so that you can identify the server (or cluster) name to specify when you use the [Get-RMSTemplate](./Get-RMSTemplate.md) cmdlet to identify the template that you want to use.

## EXAMPLES

### Example 1: Get a list of AD RMS servers that have templates
```
PS C:\>Get-RMSServer
Number of RMS Servers that can provide templates: 2


ConnectionInfo            DisplayName     AllowFromScratch


--------------            -----------     ----------------


Microsoft.Information     Contoso                     True
Microsoft.Information     Fabrikam                    True
```

This command gets a list of AD RMS servers by name that can provide templates.
When the servers are configured in an AD RMS cluster, the cluster name only is displayed.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-RMSTemplate](./Get-RMSTemplate.md)
