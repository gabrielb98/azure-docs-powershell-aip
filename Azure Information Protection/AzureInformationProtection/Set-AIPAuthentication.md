---
assetid: ED096DBB-1B3B-43DA-B0DE-C7BACC54D18B
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=851286
schema: 2.0.0
---

# Set-AIPAuthentication

## SYNOPSIS
**Relevant for:** AIP unified labeling and classic clients

Sets the authentication credentials for the Azure Information Protection client.

## SYNTAX

### Unified labeling client

```
Set-AIPAuthentication [-AppId <Guid>] [-AppSecret <String>] [-TenantId <String>] [-DelegatedUser <String>] [-OnBehalfOf <PSCredential>] [<CommonParameters>]
```

### Classic client

```
Set-AIPAuthentication [[-WebAppId] <String>] [[-WebAppKey] <String>] [[-NativeAppId] <String>] [-Token <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Set-AIPAuthentication** cmdlet sets credentials by using an access token so that you can sign in as a different user and also use the labeling cmdlets non-interactively. 

For example:

- You want to use the Azure Information Protection scanner to continually discover and automatically label and protect files in multiple data stores. 
- You want to run a scheduled PowerShell script that automatically labels and protects files on a file server by using the [Set-AIPFileClassification](./Set-AIPFileClassification.md) or [Set-AIPFileLabel](./Set-AIPFileLabel.md) cmdlets. 
- You have a data loss prevention (DLP) solution that that you want to augment by automatically labeling and protecting files that this solution identifies. 

**Running with or without parameters**

If you run this cmdlet without parameters, the account acquires an Azure AD access token that is valid for 90 days or until your password expires. 

To control when the access token expires, run this cmdlet with parameters. This lets you configure the access token for 1 year, 2 years, or to never expire. This configuration requires you to have one or more applications registered in Azure Active Directory. 

|Client  |Description  |
|---------|---------|
|**Unified labeling client**   | For more information see [labeling files non-interactively for the AIP unified labeling client](/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).   </br></br>- The unified labeling client supports the *OnBehalfOf* parameter, which accepts a stored variable that contains your specified Windows user name and password. Use this parameter instead of the *Token* parameter supported by the classic client. </br></br>- Use the *DelegatedUser* parameter to specify a user account in Azure Active Directory that is assigned one or more label policies from your labeling management center.|
|**Classic client**    |  For more information see [labeling files non-interactively for the AIP classic client](/information-protection/rms-client/client-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection). </br></br>The classic client supports a *Token* parameter that you cannot specify the first time you run this cmdlet, but can specify subsequently. </br></br>The first time that you run this cmdlet, it generates an access token that you can copy to the clipboard and then specify when you run the cmdlet again. By specifying the access token with this cmdlet, you are not prompted to sign in. </br></br>**Tip**: Use this method for service accounts that cannot be granted the right to log on locally. For full instructions, see [Specify and use the Token parameter for Set-AIPAuthentication](/information-protection/rms-client/client-admin-guide-powershell#specify-and-use-the-token-parameter-for-set-aipauthentication) from the admin guide. </br></br>**Note:** When the Azure AD access token expires, you must rerun the cmdlet to acquire a new token.|
| | |

> [!NOTE]
> To provide a unified and streamlined customer experience, the **Azure Information Protection classic client** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021.** 
> 
> This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).

## EXAMPLES

### Example 1: Set the authentication credentials without using applications that are registered in Azure Active Directory
```
PS C:\> Set-AIPAuthentication 
Acquired access token
```

This command prompts you for your Azure AD credentials that are used to acquire an access token that is valid for 90 days or until your password expires.

### Example 2: (Unified labeling client only) Set the authentication credentials by using an application that is registered in Azure Active Directory

```
PS C:\>$pscreds = Get-Credential CONTOSO\scanner
PS C:\> Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -DelegatedUser scanner@contoso.com -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -OnBehalfOf $pscreds
Acquired application access token on behalf of CONTOSO\scanner.
```

Run the commands in this PowerShell session with the **Run as Administrator** option, which is required for the *OnBehalfOf* parameter.

The first command creates a **PSCredential** object and stores the specified Windows user name and password in the **$pscreds** variable. When you run this command, you are prompted for the password for the user name that you specified.

The second command acquires an access token that is combined with the application so that the token becomes valid for 1 year, 2 years, or never expires, according to your configuration of the registered app in Azure AD. The user name of scanner@contoso.com sets the user context to download labels and label policies from your labeling management center, such as the Office 365 Security & Compliance Center.

### Example 3: (Classic client only) Set the authentication credentials by using applications that are registered in Azure Active Directory and when prompted, sign in
```
PS C:\> Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "+LBkMvddz?WrlNCK5v0e6_=meM59sSAn" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f"
Acquired application access token on behalf of the user
```

This command prompts you for your Azure AD credentials that are used to acquire an access token. This token is then combined with the web application details so that the token becomes valid for 1 year, 2 years, or never expires, according to your configuration of the web app /API in Azure AD. 

### Example 4: (Classic client only) Step 1 of 2 to set the authentication credentials for a service account that can't interactively sign in
```
PS C:\> (Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "+LBkMvddz?WrlNCK5v0e6_=meM59sSAn" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f").token | clip
Acquired application access token on behalf of the user
```

This command prompts you for your Azure AD credentials that are used to acquire an access token. This token is then combined with the web application details so that the token becomes valid for 1 year, 2 years, or never expires, according to your configuration of the web app /API in Azure AD. 

The access token is copied to the clipboard so that you can run this cmdlet again in a new PowerShell session that runs in the security context of a service account. In this new PowerShell session, you can now run this cmdlet with the *Token* parameter by pasting the value from the clipboard.

### Example 5: (Classic client only) Step 2 of 2 to set the authentication credentials for a service account that can't interactively sign in
```
PS C:\> Set-AIPAuthentication -webAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "+LBkMvddz?WrlNCK5v0e6_=meM59sSAn" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f" -Token AwAAAAEAAACDAWh0dHBzOi8vbG9naW4u...
Acquired application access token on behalf of the user
```

This command should be run only after first running the command without the *Token* parameter, and you have the token value that is generated. For example, see the preceding example, which copies the token value to the clipboard. Treat the token value as you would a password and for security reasons, do not save it to a file. Typically, you will run this second command in a separate PowerShell session to the first command (in a different security context), so saving the token to the clipboard is a good solution. 

The token value is a very long string and to conserve space, a complete value is not included in this example. When you paste your token value, make sure the complete string is specified.

By running this command with a token, you are not prompted to sign in. 

## PARAMETERS

### -WebAppId
**Relevant for:** AIP classic client only

Specifies the application ID of the "Web app / API" application in Azure AD.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WebAppKey
**Relevant for:** AIP classic client only

Specifies the secret value generated in the "Web app / API" application in Azure AD.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NativeAppId
**Relevant for:** AIP classic client only

Specifies the application ID of the "Native" application in Azure AD.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### -DelegatedUser
**Relevant for:** AIP unified labeling client only

Specifies the user account credentials to use when downloading label policies with sensitivity labels from your labeling management center.

- The credentials used must be an Azure Active Directory account that can be used to get the policy and online configuration. 

    - It can be the same account that is used for the **ServiceUserCredentials** if this account is synched to Azure Active Directory, or a different account. 

    - If this account needs to reprotect files, remove protection from files, or inspect protected files, make it a [super user](/azure/information-protection/configure-super-users) for Azure Information Protection.

- Set the value of this parameter using the UPN. For example: `scannerservice@contoso.com`

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


### -OnBehalfOf
**Relevant for:** AIP unified labeling client only

Specifies the variable that includes the credentials object used by the AIP unified labeling client. 

This parameter is used when login rights cannot be granted to scheduled PowerShell commands.

- Use the same credentials for this parameter as used to run the scanner, defined by the **ServiceUserCredentials** parameter.

- To use this parameter, you must run your PowerShell session with the **Run as Administrator** option.

Use the [Get-Credential](/powershell/module/microsoft.powershell.security/get-credential) cmdlet to create the variable that stores the credentials. For more information, type `Get-Help Get-Cmdlet`. 

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Token
**Relevant for:** AIP classic client only

Specifies the access token value to eliminate the initial sign-in prompt for Azure Information Protection.

Run the cmdlet first without this parameter to generate the token and copy the token value. Then run this cmdlet again with this parameter and the copied token value.

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


### -AppId
**Relevant for:** AIP unified labeling client only

Specifies the "Application (client) ID" for app registered in Azure AD.

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

### -AppSecret
**Relevant for:** AIP unified labeling client only

Specifies the client secret value generated at the time your app was registered in Azure AD.


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

### -TenantId
**Relevant for:** AIP unified labeling client only

Specifies the tenant GUID that contains your registered app in Azure AD.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. 

For more information, see [about_CommonParameters ](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Clear-AIPAuthentication](./Clear-AIPAuthentication.md)

[Get-AIPFileStatus](./Get-AIPFileStatus.md)

[Set-AIPFileClassification](./Set-AIPFileClassification.md)

[Set-AIPFileLabel](./Set-AIPFileLabel.md)