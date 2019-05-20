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

```
Set-AIPAuthentication [[-WebAppId] <String>] [[-WebAppKey] <String>] [[-NativeAppId] <String>]
 [-Token <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Set-AIPAuthentication** cmdlet sets credentials by using an access token so that you can sign in as a different user and also use the labeling cmdlets non-interactively. For example, you want to use the Azure Information Protection scanner to continually discover and automatically label and protect files in multiple data stores. Or, you want to run a scheduled PowerShell script that automatically labels and protects files on a file server by using the [Set-AIPFileClassification](./Set-AIPFileClassification.md) or [Set-AIPFileLabel](./Set-AIPFileLabel.md) cmdlets. Or, you have a data loss prevention (DLP) solution that that you want to augment by automatically labeling and protecting files that this solution identifies. 

If you run this cmdlet without parameters, the account acquires an Azure AD access token that is valid for 90 days or until your password expires. 

To control when the access token expires, run this cmdlet with parameters. This lets you configure the access token for 1 year, 2 years, or to never expire. This configuration requires you to have two applications registered in Azure Active Directory: **A web app / API** application and a **native application**. Use these applications to supply the parameters for the Set-AIPAuthentication cmdlet. For instructions, see [How to label files non-interactively for Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection) from the admin guide.

This cmdlet includes a *Token* parameter that you cannot specify the first time you run this cmdlet, but can specify subsequently. The first time that you run this cmdlet, it generates an access token that you can copy to the clipboard and then specify when you run the cmdlet again. By specifying the access token with this cmdlet, you are not prompted to sign in. Use this method for service accounts that cannot be granted the right to log on locally. For full instructions, see [Specify and use the Token parameter for Set-AIPAuthentication](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-powershell#specify-and-use-the-token-parameter-for-set-aipauthentication) from the admin guide.

When the Azure AD access token expires, you must rerun the cmdlet to acquire a new token.

Note: The Azure Information Protection unified labeling client supports this cmdlet without parameters only, which lets you sign in by using a different user account. This client currently does not support non-interactive scenarios.

## EXAMPLES

### Example 1: Set the authentication credentials without using applications that are registered in Azure Active Directory
```
PS C:\> Set-AIPAuthentication 
Acquired access token
```

This command prompts you for your Azure AD credentials that are used to acquire an access token that is valid for 90 days or until your password expires.

### Example 2: Set the authentication credentials by using applications that are registered in Azure Active Directory and when prompted, sign in - Azure Information Protection client only
```
PS C:\> Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "+LBkMvddz?WrlNCK5v0e6_=meM59sSAn" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f"
Acquired application access token on behalf of the user
```

This command prompts you for your Azure AD credentials that are used to acquire an access token. This token is then combined with the web application details so that the token becomes valid for 1 year, 2 years, or never expires, according to your configuration of the web app /API in Azure AD. 

### Example 3: Step 1 of 2 to set the authentication credentials for a service account that can't interactively sign in - Azure Information Protection client only
```
PS C:\> (Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "+LBkMvddz?WrlNCK5v0e6_=meM59sSAn" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f").token | clip
Acquired application access token on behalf of the user
```

This command prompts you for your Azure AD credentials that are used to acquire an access token. This token is then combined with the web application details so that the token becomes valid for 1 year, 2 years, or never expires, according to your configuration of the web app /API in Azure AD. 

The access token is copied to the clipboard so that you can run this cmdlet again in a new PowerShell session that runs in the security context of a service account. In this new PowerShell session, you can now run this cmdlet with the *Token* parameter by pasting the value from the clipboard.

### Example 4: Step 2 of 2 to set the authentication credentials for a service account that can't interactively sign in - Azure Information Protection client only
```
PS C:\> Set-AIPAuthentication -webAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "+LBkMvddz?WrlNCK5v0e6_=meM59sSAn" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f" -Token AwAAAAEAAACDAWh0dHBzOi8vbG9naW4u...
Acquired application access token on behalf of the user
```

This command should be run only after first running the command without the *Token* parameter, and you have the token value that is generated. For example, see the preceding example, which copies the token value to the clipboard. Treat the token value as you would a password and for security reasons, do not save it to a file. Typically, you will run this second command in a separate PowerShell session to the first command (in a different security context), so saving the token to the clipboard is a good solution. 

The token value is a very long string and to conserve space, a complete value is not included in this example. When you paste your token value, make sure the complete string is specified. 

By running this command with a token, you are not prompted to sign in. 

## PARAMETERS

### -WebAppId
Note: This parameter is not supported with the Azure Information Protection unified labeling client.

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
Note: This parameter is not supported with the Azure Information Protection unified labeling client.

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
Note: This parameter is not supported with the Azure Information Protection unified labeling client.

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
Note: This parameter is not supported with the Azure Information Protection unified labeling client.

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
