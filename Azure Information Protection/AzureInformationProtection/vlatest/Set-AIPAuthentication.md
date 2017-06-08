---
external help file: AIP.dll-Help.xml
ms.assetid: ED096DBB-1B3B-43DA-B0DE-C7BACC54D18B
schema: 2.0.0
---

# Set-AIPAuthentication

## SYNOPSIS
Sets the authentication credentials for the AIP applications.

## SYNTAX

```
Set-AIPAuthentication [[-WebAppId] <String>] [[-WebAppKey] <String>] [[-NativeAppId] <String>]
```

## DESCRIPTION
The Set-AIPAuthentication cmdlet can be use in 2 ways:
1. When called without parameters, command will perform user token acquisition via ADAL with UI – token will be valid for 90 days or until the used user password would expire or change.
2. When called with parameters, command will perform user token acquisition via ADAL with UI, then acquire application token on-behalf of the user that logged in – token validation will be determined by the expiration chosen upon generation of the web application key (1 year, 2 years, unlimited).

## EXAMPLES

### Example 1
```
PS C:\> Set-AIPAuthentication 
Acquired access token
```

This command prompts the user for AAD credentials which are used to acquire a user access token.

### Example 2
```
PS C:\> Set-AIPAuthentication -webAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -webAppKey "sc9qxh4lmv31GbIBCy36TxEEuM1VmKex5sAdBzABH+M=" -nativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f"
Acquired application access token on behalf of the user
```

This command prompts the user for AAD credentials which are used to acquire a user access token to be combined with the web application details to acquire an application access token on behalf of the user.

## PARAMETERS

### -WebAppId
Application ID of the “Web app / API” application created for the OnBehalfOf flow in AAD.

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
Secret key generated in the “Web app / API” application created for the OnBehalfOf flow in AAD.

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
Application ID of the “Native” application created for the OnBehalfOf flow in AAD.

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