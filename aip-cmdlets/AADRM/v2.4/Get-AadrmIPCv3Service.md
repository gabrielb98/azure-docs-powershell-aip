---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400610
schema: 2.0.0
---

# Get-AadrmIPCv3Service

## SYNOPSIS
Displays whether the MSIPC v3 service is enabled or disabled for Rights Management.

## SYNTAX

```
Get-AadrmIPCv3Service [<CommonParameters>]
```

## DESCRIPTION
The Get-AadrmIPCv3Service cmdlets displays the status of the MSIPC v3 platform on mobile devices such as iOS and Android.
This platform must be enabled to support Rights Management.

## EXAMPLES

### Example1: Display whether the MSIPC v3 platform for iOS and Android devices is enabled
```
PS C:\>Get-AadrmIPCv3Service
```

This command displays whether the MSIPC v3 platform is enabled or disabled.
This platform must be enabled on iOS and Android mobile devices to support Azure Rights Management.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AadrmIPCv3Service]()

[Enable-AadrmIPCv3Service]()

