---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=841549
schema: 2.0.0
ms.assetid: 83B4D09E-ADAE-4DF9-9924-132A9FE47DFF
---

# Set-RMSServerAuthentication

## SYNOPSIS
Sets the service principal authentication credentials for Azure RMS.

## SYNTAX

```
Set-RMSServerAuthentication -Key <String> -AppPrincipalId <String> -BposTenantId <String> [<CommonParameters>]
```

## DESCRIPTION
The **Set-RMSServerAuthentication** cmdlet specifies identifiers for a service principal to authenticate with the Azure Rights Management service, so that you can then protect or unprotect files by using Azure RMS. Use a service principal when you need to protect or unprotect files without interaction, for example, a script that automatically protects files on a file server. You need run this command just one time for your PowerShell session.

This cmdlet is for Azure RMS only and is not used for AD RMS. This cmdlet also does not apply if you are authenticating to Azure RMS by using your user account. For more information about this cmdlet and how to get the identifiers that it requires, see [Using PowerShell with the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-powershell) from the Azure Information Protection client admin guide.

## EXAMPLES

### Example 1: Set the service principal authentication credentials for Azure RMS
```
PS C:\>Set-RMSServerAuthentication -BposTenantId "23976bc6-dcd4-4173-9d96-dad1f48efd42" -Key "zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=" -AppPrincipalId "b5e3f76a-b5c2-4c96-a594-a0807f65bba4"
The RmsServerAuthentication is set to ON
```

This command sets the service principle authentication credentials for Azure RMS, by specifying the required three identifiers for a previously created service principal.

## PARAMETERS

### -AppPrincipalId
Specifies the AppPrincipalId value of the service principal.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BposTenantId
Specifies the BposTenantId value (the tenant ID) to which the service principal belongs.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Key
Specifies the symmetric key value for the service principal.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
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

[Using PowerShell with the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-powershell)
