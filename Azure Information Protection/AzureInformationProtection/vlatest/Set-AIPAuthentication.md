---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=851286
assetid: ED096DBB-1B3B-43DA-B0DE-C7BACC54D18B
schema: 2.0.0
---

# Set-AIPAuthentication

## SYNOPSIS
Sets the authentication credentials for the Azure Information Protection client.

## SYNTAX

```
Set-AIPAuthentication [[-WebAppId] <String>] [[-WebAppKey] <String>] [[-NativeAppId] <String>]
```

## DESCRIPTION
The **Set-AIPAuthentication** cmdlet sets credentials by using an access token so that you can then use the labeling cmdlets non-interactively. For example, you want to run a scheduled PowerShell script that automatically labels and protects files on a file server by using the [Set-AIPFileClassification](./Set-AIPFileClassification.md) or [Set-AIPFileLabel](./Set-AIPFileLabel.md) cmdlets. Or, you have a data loss prevention (DLP) solution that that you want to augment by automatically labeling and protecting files that this solution identifies. 

The first time you run this cmdlet, you are prompted to sign in for Azure Information Protection. After that, you can then run the labeling cmdlets non-interactively until your authentication token expires. When the token expires, run the cmdlet again to acquire a new token.

If you run this cmdlet without parameters, the account acquires an access token that is valid for 90 days or until your password expires.  

To control when the access token expires, run this cmdlet with parameters. This lets you configure the access token for 1 year, 2 years, or to never expire. This configuration requires you to have two applications registered in Azure Active Directory: **A web app / API** application and a **native application**. Use these applications to supply the parameters for the Set-AIPAuthentication cmdlet. For instructions, see [How to label files non-interactively for Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection) from the admin guide.

Note: This cmdlet requires the preview version of the Azure Information Protection client.

## EXAMPLES

### Example 1
```
PS C:\> Set-AIPAuthentication 
Acquired access token
```

This command prompts you for your Azure AD credentials that are used to acquire a user access token that is valid for 90 days or until your password expires.

### Example 2
```
PS C:\> Set-AIPAuthentication -webAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -webAppKey "sc9qxh4lmv31GbIBCy36TxEEuM1VmKex5sAdBzABH+M=" -nativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f"
Acquired application access token on behalf of the user
```

This command prompts you for your Azure AD credentials that are used to acquire a user access token. This token is then combined with the web application details to acquire an application access token on behalf of the user. This token is then valid for 1 year, 2 years, or never expires, according to your configuration of the web app /API in Azure AD.

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

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Clear-AIPAuthentication](./Clear-AIPAuthentication.md)

[Set-AIPFileLabel](./Set-AIPFileLabel.md)

[Set-AIPFileLabel](./Set-AIPFileLabel.md)
