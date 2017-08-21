---
external help file: AIP.dll-Help.xml
ms.assetid: FAA0CC7D-4004-41A2-9147-3A0C33F6ACF7
online version: https://go.microsoft.com/fwlink/?linkid=841545
schema: 2.0.0
---

# Get-RMSServerAuthentication

## SYNOPSIS
Gets the status of your server mode for authentication to RMS.

## SYNTAX

```
Get-RMSServerAuthentication [<CommonParameters>]
```

## DESCRIPTION
The **Get-RMSServerAuthentication** cmdlet gets the status and details of the server mode that was previous set by using [Set-RMSServerAuthentication](./Set-RMSServerAuthentication.md). Server mode must be set to protect or unprotect files non-interactively. This status remains on for the duration of your PowerShell session.

This cmdlet does not apply if you protect or unprotect files by using your user account. 

To use server mode with the Azure Rights Management service, you must use a service principal account. For more information about this requirement, see [Using PowerShell with the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-powershell) from the Azure Information Protection client admin guide.

## EXAMPLES

### Example 1: Get the server mode status when you are using Azure RMS
```
PS C:\>Get-RMSServerAuthentication
The RmsServerAuthentication is ON

Base64Key                                         AppPrincipalId                          BposTenantId
---------                                         --------------                          ------------
zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=      b5e3f76a-b5c2-4c96-a594-a0807f65bba4    23976bc6-dcd4-4173-9d96-dad1f48efd42
```

This command gets the server mode status and the output indicates that a service principal account is being used to authenticate to the Azure Rights Management service. The outputs includes the currently used identifiers, if authentication is successful.

### Example 2: Get the serer mode status when you are using AD RMS
```
PS C:\>Get-RMSServerAuthentication
The RmsServerAuthentication is ON
```

This command gets the server mode status and because there are no identifiers, the output indicates that you are using integrated authentication for AD RMS. 

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Set-RMSServerAuthentication](./Set-RMSServerAuthentication.md)
