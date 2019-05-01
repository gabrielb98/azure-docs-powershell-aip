---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: CDD8C715-6C63-40BC-AF75-F842FDFD5E62
online version: http://go.microsoft.com/fwlink/?LinkID=529558https://go.microsoft.com/fwlink/?linkid=2045179
schema: 2.0.0
---

# Get-AipServiceMaxUseLicenseValidityTime

## SYNOPSIS
Gets the maximum validity time for Rights Management use licenses from Azure Information Protection.

## SYNTAX

```
Get-AipServiceMaxUseLicenseValidityTime [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceMaxUseLicenseValidityTime** cmdlet gets the maximum validity time for your tenant, in days, for Azure Rights Management use licenses from Azure Information Protection. The default value is 30 days.

You must use PowerShell to view this configuration at the organization level; you cannot view this configuration by using a management portal.

## EXAMPLES

### Example 1: Get the maximum validity time
```
PS C:\>Get-AipServiceMaxUseLicenseValidityTime
30
```

This command gets the maximum validity time for use licenses for your tenant.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Set-AipServiceMaxUseLicenseValidityTime](./Set-AipServiceMaxUseLicenseValidityTime.md)


