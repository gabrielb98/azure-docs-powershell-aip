---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400602
schema: 2.0.0
---

# Enable-Aadrm

## SYNOPSIS
Activates Rights Management for your organization.

## SYNTAX

```
Enable-Aadrm [<CommonParameters>]
```

## DESCRIPTION
The Enable-Aadrm cmdlet enables the capabilities of Azure Rights Management for your organization and offers an alternative method of doing this rather than using the management portals.
You must activate Rights Management before you can begin to use information rights management (IRM) features in Office applications and before you can protect documents and emails by using other applications that use Azure Rights Management.
When you activate Rights Management, you turn on this service for all rights-enabled applications and services, but some applications and services and might need further configuration before you can use Azure Rights Management in your organization.

For more information about activating Rights Management, see Activating Azure Rights Management (https://docs.microsoft.com/rights-management/deploy-use/activate-service) on the Microsoft documentation site.
For more information about other deployment steps that might be needed, see the deployment roadmap (https://docs.microsoft.com/rights-management/plan-design/deployment-roadmap).

## EXAMPLES

### Example 1: Enable Rights Management
```
PS C:\>Enable-Aadrm
```

This command activates Rights Management for your organization.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-Aadrm]()

[Get-Aadrm]()

