---
external help file: AIP.dll-Help.xml
ms.assetid: 83B4D09E-ADAE-4DF9-9924-132A9FE47DFF
online version: https://go.microsoft.com/fwlink/?linkid=841549
schema: 2.0.0
---

# Set-RMSServerAuthentication

## SYNOPSIS
Sets the mode for server mode, which is required for non-interactive sessions.

## SYNTAX

```
Set-RMSServerAuthentication [-Key <String>] [-AppPrincipalId <String>] [-BposTenantId <String>]
 [-IntegratedAuth] [<CommonParameters>]
```

## DESCRIPTION
The **Set-RMSServerAuthentication** cmdlet sets the server mode so that commands can be run non-interactively. For Azure RMS, server mode requires you to specify credentials for a service principal to authenticate with the Azure Rights Management service. For AD RMS, server mode requires you to specify integrated authentication. Use server mode when you need to protect or unprotect files without interaction, for example, a script that automatically protects files on a file server. You need run this command just one time for your PowerShell session.

This cmdlet does not apply if you use your user account to protect or unprotect files. 

For more information about how to get the identifiers that the service principal requires for Azure RMS, see [Using PowerShell with the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-powershell) from the Azure Information Protection client admin guide.

## EXAMPLES

### Example 1: Set the server mode for Azure RMS and specify the service principal credentials
```
PS C:\>Set-RMSServerAuthentication -BposTenantId "23976bc6-dcd4-4173-9d96-dad1f48efd42" -Key "zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=" -AppPrincipalId "b5e3f76a-b5c2-4c96-a594-a0807f65bba4"
```

This command sets the service principle authentication credentials for Azure RMS, by specifying the required three identifiers for a previously created service principal.

### Example 2: Set the server mode for AD RMS
```
PS C:\>Set-RMSServerAuthentication -IntegratedAuth
Integrated authentication is enabled
```

This command sets the server mode for AD RMS.


## PARAMETERS

### -AppPrincipalId
Specifies the AppPrincipalId value of the service principal. 

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
Specifies the BposTenantId value (the tenant ID) to which the service principal belongs.

Applies to Azure RMS only. Specify this parameter with the *AppPrincipal* parameter and the *Key* parameter.

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
Specifies the symmetric key value for the service principal.

Applies to Azure RMS only. Specify this parameter with the *AppPrincipal* parameter and the *BposTenantId* parameter.

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
Specifies server mode for AD RMS so that cmdlets can run non-interactively.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-RMSServerAuthentication](./Get-RMSServerAuthentication.md)

