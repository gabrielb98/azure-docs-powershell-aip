---
external help file: AIPService.dll-Help.xml
online version:
schema: 2.0.0
ms.assetid: 847B715B-0951-40BC-A1CA-8BD6E8AD8148
---

# Enable-AipServiceIPCv3

## SYNOPSIS
Enables the MSIPC v3 platform for Azure Information Protection.

## SYNTAX

```
Enable-AipServiceIPCv3 [<CommonParameters>]
```

## DESCRIPTION
The **Enable-AipServiceIPCv3** cmdlets enables the MSIPC v3 platform on mobile devices such as iOS and Android. This platform must be enabled to support the protection service from Azure Information Protection.

You must use PowerShell to do this configuration; you cannot do this configuration by using a management portal.

## EXAMPLES

### Example1: Enable the MSIPC v3 platform for iOS and Android devices
```
PS C:\>Enable-AipServiceIPCv3
```

This command enables the MSIPC v3 platform so that iOS and Android mobile devices can use the protection service from Azure Information Protection.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AipServiceIPCv3](./Disable-AipServiceIPCv3.md)

[Get-AipServiceIPCv3](./Get-AipServiceIPCv3.md)
