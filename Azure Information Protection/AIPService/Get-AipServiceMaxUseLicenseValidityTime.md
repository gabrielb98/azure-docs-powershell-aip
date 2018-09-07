---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkID=529558
schema: 2.0.0
ms.assetid: CDD8C715-6C63-40BC-AF75-F842FDFD5E62
---

# Get-AipServiceMaxUseLicenseValidityTime

## SYNOPSIS
Gets the maximum validity time for Information Protection service use licenses.

## SYNTAX

```
Get-AipServiceMaxUseLicenseValidityTime [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceMaxUseLicenseValidityTime** cmdlet gets the maximum validity time, in days, for Azure Information Protection service use licenses in your organization. The default value is 30 days.

You must use PowerShell to view this configuration at the organization level; you cannot view this configuration by using a management portal.

## EXAMPLES

### Example 1: Get the maximum validity time
```
PS C:\>Get-AipServiceMaxUseLicenseValidityTime
30
```

This command gets the maximum validity time for use licenses in your organization.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Set-AipServiceMaxUseLicenseValidityTime](./Set-AipServiceMaxUseLicenseValidityTime.md)


