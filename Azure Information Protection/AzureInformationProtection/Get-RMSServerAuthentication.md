---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
ms.assetid: FAA0CC7D-4004-41A2-9147-3A0C33F6ACF7
online version: https://go.microsoft.com/fwlink/?linkid=841545
schema: 2.0.0
---

# Get-RMSServerAuthentication

## SYNOPSIS
**Relevant for:** AIP classic client only

Gets the server mode status that is used for authentication to RMS.

## SYNTAX

```
Get-RMSServerAuthentication [<CommonParameters>]
```

## DESCRIPTION
The **Get-RMSServerAuthentication** cmdlet gets the server mode status and details that are set by using [Set-RMSServerAuthentication](./Set-RMSServerAuthentication.md). Server mode must be set to protect or unprotect files non-interactively. For example, if you protect files by using Windows Server and File Classification Infrastructure (FCI). This status remains on for the duration of your PowerShell session.

This cmdlet does not apply if you protect or unprotect files by using your user account. 

To use server mode with the Azure Rights Management service, you must use a service principal account in Azure AD. To use server mode with AD RMS, the computer account must be granted permissions. For more information, see [Using PowerShell with the Azure Information Protection client](/information-protection/rms-client/client-admin-guide-powershell) from the Azure Information Protection client admin guide.

> [!NOTE]
> To provide a unified and streamlined customer experience, the **Azure Information Protection classic client** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021.** 
> 
> This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).

## EXAMPLES

### Example 1: Get the server mode status when you are using Azure RMS
```
PS C:\>Get-RMSServerAuthentication
The RmsServerAuthentication is ON

Base64Key                                         AppPrincipalId                          BposTenantId
---------                                         --------------                          ------------
zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=      b5e3f76a-b5c2-4c96-a594-a0807f65bba4    23976bc6-dcd4-4173-9d96-dad1f48efd42
```

This command gets the server mode status and the output indicates that a service principal account is being used to authenticate to the Azure Rights Management service. The outputs includes the currently used identifiers.

### Example 2: Get the serer mode status when you are using AD RMS
```
PS C:\>Get-RMSServerAuthentication
The RmsServerAuthentication is ON
```

This command gets the server mode status and because there are no identifiers, the output indicates that you are using Windows integrated authentication for AD RMS. 

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Set-RMSServerAuthentication](./Set-RMSServerAuthentication.md)