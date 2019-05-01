---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 3875D0F4-EAB2-43B3-945E-46FD86810E9B
online version: https://go.microsoft.com/fwlink/?linkid=2045170
schema: 2.0.0
---

# Get-AipServiceIPCv3

## SYNOPSIS
Displays whether the MSIPC v3 service is enabled or disabled for Azure Information Protection.

## SYNTAX

```
Get-AipServiceIPCv3 [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceIPCv3** cmdlets displays the status of the MSIPC v3 platform on mobile devices such as iOS and Android. This platform must be enabled to support protection from Azure Information Protection.

You must use PowerShell to view this configuration; you cannot view this configuration by using a management portal.

## EXAMPLES

### Example1: Display whether the MSIPC v3 platform for iOS and Android devices is enabled
```
PS C:\>Get-AipServiceIPCv3
```

This command displays whether the MSIPC v3 platform is enabled or disabled. This platform must be enabled on iOS and Android mobile devices to support protection from Azure Information Protection.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AipServiceIPCv3](./Disable-AipServiceIPCv3.md)

[Enable-AipServiceIPCv3](./Enable-AipServiceIPCv3.md)
