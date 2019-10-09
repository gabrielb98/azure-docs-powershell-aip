---
assetid: ED096DBB-1B3B-43DA-B0DE-C7BACC54D18B
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=851286
schema: 2.0.0
---

# Set-AIPAuthentication

## SYNOPSIS
Sets the authentication credentials for the Azure Information Protection client.

## SYNTAX

### Classic client

```
Set-AIPAuthentication [[-WebAppId] <String>] [[-WebAppKey] <String>] [[-NativeAppId] <String>] [-Token <String>] [<CommonParameters>]
```

### Unified labeling client

```
Set-AIPAuthentication [-AppId <Guid>] [-AppSecret <String>] [-TenantId <String>] [-DelegatedUser <String>] [-OnBehalfOf <PSCredential>] [<CommonParameters>]
```

## DESCRIPTION
The Set-AIPAuthentication cmdlet sets credentials by using an access token so that you can sign in as a different user and also use the labeling cmdlets non-interactively. For example, you want to use the Azure Information Protection scanner to continually discover and automatically label and protect files in multiple data stores. Or, you want to run a scheduled PowerShell script that automatically labels and protects files on a file server by using the [Set-AIPFileClassification](./Set-AIPFileClassification.md) or [Set-AIPFileLabel](./Set-AIPFileLabel.md) cmdlets. Or, you have a data loss prevention (DLP) solution that that you want to augment by automatically labeling and protecting files that this solution identifies. 

If you run this cmdlet without parameters, the account acquires an Azure AD access token that is valid for 90 days or until your password expires. 

To control when the access token expires, run this cmdlet with parameters. This lets you configure the access token for 1 year, 2 years, or to never expire. This configuration requires you to have one or more applications registered in Azure Active Directory. For instructions, see the following sections from the admin guides:

- For the classic client: [How to label files non-interactively for Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection)

- For the unified labeling client: [How to label files non-interactively for Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection)

The classic client supports a *Token* parameter that you cannot specify the first time you run this cmdlet, but can specify subsequently. The first time that you run this cmdlet, it generates an access token that you can copy to the clipboard and then specify when you run the cmdlet again. By specifying the access token with this cmdlet, you are not prompted to sign in. Use this method for service accounts that cannot be granted the right to log on locally. For full instructions, see [Specify and use the Token parameter for Set-AIPAuthentication](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-powershell#specify-and-use-the-token-parameter-for-set-aipauthentication) from the admin guide.

When the Azure AD access token expires, you must rerun the cmdlet to acquire a new token.

The Azure Information Protection unified labeling client supports a new parameter, *OnBehalfOf*, which accepts a stored variable that contains your specified user name and password. Use this parameter instead of the *Token* parameter. 

## EXAMPLES

### Example 1: Set the authentication credentials without using applications that are registered in Azure Active Directory
```
PS C:\> Set-AIPAuthentication 
Acquired access token
```

This command prompts you for your Azure AD credentials that are used to acquire an access token that is valid for 90 days or until your password expires.

### Example 2: Set the authentication credentials by using applications that are registered in Azure Active Directory and when prompted, sign in - Azure Information Protection client (classic) only
```
PS C:\> Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "+LBkMvddz?WrlNCK5v0e6_=meM59sSAn" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f"
Acquired application access token on behalf of the user
```

This command prompts you for your Azure AD credentials that are used to acquire an access token. This token is then combined with the web application details so that the token becomes valid for 1 year, 2 years, or never expires, according to your configuration of the web app /API in Azure AD. 

### Example 3: Step 1 of 2 to set the authentication credentials for a service account that can't interactively sign in - Azure Information Protection client (classic) only
```
PS C:\> (Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "+LBkMvddz?WrlNCK5v0e6_=meM59sSAn" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f").token | clip
Acquired application access token on behalf of the user
```

This command prompts you for your Azure AD credentials that are used to acquire an access token. This token is then combined with the web application details so that the token becomes valid for 1 year, 2 years, or never expires, according to your configuration of the web app /API in Azure AD. 

The access token is copied to the clipboard so that you can run this cmdlet again in a new PowerShell session that runs in the security context of a service account. In this new PowerShell session, you can now run this cmdlet with the *Token* parameter by pasting the value from the clipboard.

### Example 4: Step 2 of 2 to set the authentication credentials for a service account that can't interactively sign in - Azure Information Protection client (classic) only
```
PS C:\> Set-AIPAuthentication -webAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "+LBkMvddz?WrlNCK5v0e6_=meM59sSAn" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f" -Token AwAAAAEAAACDAWh0dHBzOi8vbG9naW4u...
Acquired application access token on behalf of the user
```

This command should be run only after first running the command without the *Token* parameter, and you have the token value that is generated. For example, see the preceding example, which copies the token value to the clipboard. Treat the token value as you would a password and for security reasons, do not save it to a file. Typically, you will run this second command in a separate PowerShell session to the first command (in a different security context), so saving the token to the clipboard is a good solution. 

The token value is a very long string and to conserve space, a complete value is not included in this example. When you paste your token value, make sure the complete string is specified.

By running this command with a token, you are not prompted to sign in. 

### Example 5: Set the authentication credentials by using an application that is registered in Azure Active Directory and when prompted, sign in - Azure Information Protection unified labeling client only

```
PS C:\>$pscreds = Get-Credential CONTOSO\admin
PS C:\> Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -OnBehalfOf $pscreds
Acquired application access token on behalf of CONTOSO\admin.
```

Run the commands in this PowerShell session with the **Run as Administrator** option, which is required for the *OnBehalfOf* parameter.

The first command creates a **PSCredential** object and stores the specified Windows user name and password in the **$pscreds** variable. When you run this command, you are prompted for the password for the user name that you specified.

The second command acquires an access token that is combined with the application so that the token becomes valid for 1 year, 2 years, or never expires, according to your configuration of the registered app in Azure AD.

## PARAMETERS

### -WebAppId
Note: Applies to the classic client only.

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
Note: Applies to the classic client only.

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
Note: Applies to the classic client only.

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
Note: Applies to the unified labeling client only.

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
Note: Applies to the unified labeling client only. Use it instead of the *Token* parameter.

To use this parameter, you must run your PowerShell session with the **Run as Administrator** option.

Specifies the variable that includes the credentials object for the Azure Information Protection unified labeling client to use when the account running the Azure Information Protection scanner or scheduled PowerShell commands cannot be granted the user right assignment to log on locally.

Use the Get-Credentials cmdlet to create the variable that stores the credentials.

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
Note: Applies to the classic client only.

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
Note: Applies to the unified labeling client only.

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
Note: Applies to the unified labeling client only.

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
Note: Applies to the unified labeling client only.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters ](https://go.microsoft.com/fwlink/?LinkID=113216).

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
