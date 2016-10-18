---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?LinkId=400595
schema: 2.0.0
---

# Connect-AadrmService

## SYNOPSIS
Connects to Rights Management.

## SYNTAX

### Credential (Default)
```
Connect-AadrmService [-Credential <PSCredential>] [-TenantId <Guid>] [<CommonParameters>]
```

### AccessToken
```
Connect-AadrmService [-AccessToken <String>] [-TenantId <Guid>] [<CommonParameters>]
```

## DESCRIPTION
The Connect-AadrmService cmdlet connects you to the Azure Rights Management service.
This cmdlet can also be used by a partner company that manages your tenant.

Connect by using this cmdlet before you configure Rights Management by using other cmdlets in this module.

When you are prompted for credentials, use an account that is one of the following: 

-- A global admin for your Office 365 tenant. 

-- A global administrator for your Azure tenant.
However, this account cannot be a Microsoft account (MSA) or from another Azure tenant.

-- A user account that has been granted administrative rights to Azure RMS by using the Add-AadrmRoleBasedAdministrator cmdlet.

Tip: If you are not prompted for your credentials, and you see an error message such as Cannot use this feature without credentials, verify that Internet Explorer is configured to use Windows integrated authentication.
If this setting is not enabled, enable it, restart Internet Explorer, and then retry authentication to the Rights Management service.

## EXAMPLES

### Example 1: Connect to Rights Management
```
PS C:\>$AdminCredentials = Get-Credential "Admin@aadrm.contoso.com" PS C:\>Connect-AadrmService -Credential $AdminCredentials
```

The first command creates a PSCredential object, and then stores it in the $AdminCredentials variable.
The command prompts you for a password.

The second command connects to the Rights Management service by using the credentials stored in $AdminCredentials.

## PARAMETERS

### -AccessToken
Use this parameter if your account must use multi-factor authentication (MFA) and you cannot connect to Azure RMS interactively to provide your alternative method of authentication.
For example, you have an organization-wide policy that all accounts must use MFA and you have a script that connects to Azure RMS to administer your tenant.
In this scenario, you can connect to Azure RMS by first registering your script in your tenant ¢â‚¬â"¢s Azure Active Directory as a native client app.
When you do this, provide a unique redirect URI and do not configure the permissions.
Then, get an app-only access token from Azure Active Directory, using the client ID generated for the registered native client app, the app ¢â‚¬â"¢s URI that you registered, and https://api.aadrm.com as the resource ID.
To get the access token, make sure that you authenticate to Azure Active Directory by using a global admin account.

```yaml
Type: String
Parameter Sets: AccessToken
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Specifies a PSCredential object.
To obtain a PSCredential object, use the Get-Credential cmdlet.
For more information, type Get-Help Get-Cmdlet.
Alternatively, provide a user name.
The cmdlet prompts you for a password.

```yaml
Type: PSCredential
Parameter Sets: Credential
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TenantId
Specifies the tenant GUID.
The cmdlet connects to Rights Management for the tenant that you specify by GUID.
If you do not specify this parameter, the cmdlet connects to the tenant the user belongs to.

```yaml
Type: Guid
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

[Get-Credential]()

[Disconnect-AadrmService]()

