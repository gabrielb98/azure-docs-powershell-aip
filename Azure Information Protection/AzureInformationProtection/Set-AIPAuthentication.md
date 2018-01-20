---
assetid: ED096DBB-1B3B-43DA-B0DE-C7BACC54D18B
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=851286
schema: 2.0.0
---

# Set-AIPAuthentication

## SYNOPSIS
Sets the authentication credentials for the Azure Information Protection client.

## SYNTAX

```
Set-AIPAuthentication [[-WebAppId] <String>] [[-WebAppKey] <String>] [[-NativeAppId] <String>]
 [-Token <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Set-AIPAuthentication** cmdlet sets credentials by using an access token so that you can then use the labeling cmdlets non-interactively. For example, you want to use the Azure Information Protection scanner to continually discover and automatically label and protect files in multiple data stores. Or, you want to run a scheduled PowerShell script that automatically labels and protects files on a file server by using the [Set-AIPFileClassification](./Set-AIPFileClassification.md) or [Set-AIPFileLabel](./Set-AIPFileLabel.md) cmdlets. Or, you have a data loss prevention (DLP) solution that that you want to augment by automatically labeling and protecting files that this solution identifies. 

If you run this cmdlet without parameters, the account acquires an access token that is valid for 90 days or until your password expires. 

If you run this command with **webAppId** the acquired access token is valid for the time period configured for the WebAapp.

To control when the access token expires, run this cmdlet with parameters. This lets you configure the access token for 1 year, 2 years, or to never expire. This configuration requires you to have two applications registered in Azure Active Directory: **A web app / API** application and a **native application**. Use these applications to supply the parameters for the Set-AIPAuthentication cmdlet. For instructions, see [How to label files non-interactively for Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection) from the admin guide.

This cmdlet includes a *Token* parameter that you cannot specify the first time you run this cmdlet, but can specify subsequently. The first time that you run this cmdlet, it generates an access token that you can copy to the clipboard and then specify when you run the cmdlet again. By specifying the access token with this cmdlet, you are not prompted to sign in the first time you run one of the labeling cmdlets. 

When the access token expires, you must rerun the cmdlet to acquire a new token.


## EXAMPLES

### Example 1: Set the authentication credentials without using applications that are registered in Azure Active Directory
```
PS C:\> Set-AIPAuthentication 
Acquired access token
```

This command prompts you for your Azure AD credentials that are used to acquire an access token that is valid for 90 days or until your password expires.

### Example 2: Set the authentication credentials by using applications that are registered in Azure Active Directory, and you must sign in the first time
```
PS C:\> Set-AIPAuthentication -webAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -webAppKey "sc9qxh4lmv31GbIBCy36TxEEuM1VmKex5sAdBzABH+M=" -nativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f"
Acquired application access token on behalf of the user
```

This command prompts you for your Azure AD credentials that are used to acquire an access token. This token is then combined with the web application details so that the token becomes valid for 1 year, 2 years, or never expires, according to your configuration of the web app /API in Azure AD. 

Because the *Token* parameter is not specified, you are prompted to sign in the first time you use a labeling cmdlet.

### Example 3: Step 1 of 2 to set the authentication credentials so that labeling cmdlets run without the need to sign in the first time 
```
PS C:\> (Set-AIPAuthentication -webAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -webAppKey "sc9qxh4lmv31GbIBCy36TxEEuM1VmKex5sAdBzABH+M=" -nativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f").token | clip
Acquired application access token on behalf of the user
```

This command prompts you for your Azure AD credentials that are used to acquire an access token. This token is then combined with the web application details so that the token becomes valid for 1 year, 2 years, or never expires, according to your configuration of the web app /API in Azure AD. 

The access token is copied to the clipboard so that you can run this cmdlet again in a different security context (a new PowerShell session), and this time, specify the *Token* parameter with the value from the clipboard.


### Example 4: Step 2 of 2 to set the authentication credentials so that labeling cmdlets run without the need to sign in the first time
```
PS C:\> Set-AIPAuthentication -webAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -webAppKey "sc9qxh4lmv31GbIBCy36TxEEuM1VmKex5sAdBzABH+M=" -nativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f" -token AwAAAAEAAACDAWh0dHBzOi8vbG9naW4u...
Acquired application access token on behalf of the user
```

This command should be run only after first running the command without the *Token* parameter, and you have the token value that is generated. For example, see the preceding example, which copies the token value to the clipboard. Treat the token value as you would a password and for security reasons, do not save it to a file. Typically, you will run this second command in a separate PowerShell session to the first command (in a different security context), so saving the token to the clipboard is a good solution. 

The token value is a very long string and to conserve space, a complete value is not included in this example. When you paste your token value, make sure the complete string is specified. 

By running this command with a token, you are not prompted to sign in. 


## PARAMETERS

### -WebAppId
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
Specifies the key value generated in the "Web app / API" application in Azure AD.

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

### -Token
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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

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
