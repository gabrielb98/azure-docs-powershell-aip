---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
ms.assetid: 83B4D09E-ADAE-4DF9-9924-132A9FE47DFF
online version: https://go.microsoft.com/fwlink/?linkid=841549
schema: 2.0.0
---

# Set-RMSServerAuthentication

## SYNOPSIS
**Relevant for:** AIP classic client only

Sets the server mode, which is required for non-interactive sessions.

## SYNTAX

```
Set-RMSServerAuthentication [-Key <String>] [-AppPrincipalId <String>] [-BposTenantId <String>]
 [-IntegratedAuth] [<CommonParameters>]
```

## DESCRIPTION
The **Set-RMSServerAuthentication** cmdlet sets the server mode so that commands can be run non-interactively. Use server mode when you need to protect or unprotect files without interaction. For example, if you protect files by using Windows Server and File Classification Infrastructure (FCI), or a scheduled script that automatically protects files on a computer or network share. You need run this command just one time for your PowerShell session.

This cmdlet does not apply if you use your user account to protect or unprotect files. 

- **For Azure RMS:** Server mode requires you to specify credentials for a service principal account that authenticates to the Azure Rights Management service. 

- **For AD RMS:** Server mode requires you to specify Windows integrated authentication so that the computer account can be authenticated with the AD RMS service. The computer account must be granted permissions to ServerCertification.asmx.
    
    Server mode for AD RMS requires the current GA version of the Azure Information Protection client.

For information how to get the identifiers that the service principal requires for Azure RMS, and how to grant the permissions for AD RMS, see [Using PowerShell with the AIP classic client](/information-protection/rms-client/client-admin-guide-powershell).

[!INCLUDE [The AIP classic client is sunset](../includes/classic-client-sunset.md)]


## EXAMPLES

### Example 1: Set the server mode for Azure RMS by specifying the credentials for a service principal account
```
PS C:\>Set-RMSServerAuthentication -BposTenantId "23976bc6-dcd4-4173-9d96-dad1f48efd42" -Key "zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=" -AppPrincipalId "b5e3f76a-b5c2-4c96-a594-a0807f65bba4"
```

This command sets credentials that lets a service principle account authenticate to Azure RMS, by specifying the required three identifiers.

### Example 2: Set the server mode for AD RMS by specifying Windows integrated authentication
```
PS C:\>Set-RMSServerAuthentication -IntegratedAuth
Integrated authentication is enabled
```

This command sets the server mode for Windows integrated authentication, which lets a computer account authenticate to AD RMS.

## PARAMETERS

### -AppPrincipalId
Specifies the AppPrincipalId value of a service principal account in Azure AD. 

Applies to Azure RMS only. Specify this parameter with the *BposTenantId* parameter and the *Key* parameter.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BposTenantId
Specifies the BposTenantId value (the tenant ID) to which the service principal account belongs.

Applies to Azure RMS only. Specify this parameter with the *AppPrincipalId* parameter and the *Key* parameter.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Key
Specifies the symmetric key value for the service principal account in Azure AD.

Applies to Azure RMS only. Specify this parameter with the *AppPrincipalId* parameter and the *BposTenantId* parameter.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IntegratedAuth
Specifies server mode for AD RMS so that cmdlets can run non-interactively by using Windows integrated authentication for the computer account.

Applies to AD RMS only.


```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. 

For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-RMSServerAuthentication](./Get-RMSServerAuthentication.md)