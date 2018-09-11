---
external help file: AIPService.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=521418
schema: 2.0.0
ms.assetid: A5384868-65D1-46A8-A1E0-7050F607131C
---

# Get-AipServiceOnboardingControlPolicy

## SYNOPSIS
Gets user on-boarding control policy for Information Protection service.

## SYNTAX

```
Get-AipServiceOnboardingControlPolicy [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceOnboardingControlPolicy** cmdlet obtains your Azure Information Protection service user on-boarding control policy to support a gradual deployment by controlling which users in your organization can protect content by using Azure Information Protection service.

You must use PowerShell to view this configuration; you cannot view this configuration by using a management portal.

This control can be based on assigned user licenses for the service or membership in a designated security group.
You can also define whether the policy applies to just mobile devices, just Windows clients, or mobile devices and Windows clients. For more information, see [Set-AipServiceOnboardingControlPolicy](./Set-AipServiceOnboardingControlPolicy.md).

## EXAMPLES

### Example 1: Get the user on-boarding control policy
```
PS C:\> Get-AipServiceOnboardingControlPolicy
```

This command displays the user on-boarding control policy for Azure Information Protection service for your organization.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Set-AipServiceOnboardingControlPolicy](./Set-AipServiceOnboardingControlPolicy.md)
