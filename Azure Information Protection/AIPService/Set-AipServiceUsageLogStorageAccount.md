---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400623
schema: 2.0.0
ms.assetid: D4615C3C-F6B3-42EF-BE69-C4CD4B6BD5A2
---

# Set-AipServiceUsageLogStorageAccount

## SYNOPSIS
Sets the location for Information Protection service usage logs.

## SYNTAX

```
Set-AipServiceUsageLogStorageAccount -StorageAccount <String> -AccessKey <SecureString> [<CommonParameters>]
```

## DESCRIPTION
The **Set-AipServiceUsageLogStorageAccount** cmdlet sets the Azure storage location for usage logs for Azure Information Protection service.

You must use PowerShell to set this information; you cannot do this action by using a management portal.

This cmdlet should be used only if you have usage logs prior to the usage logging change in February 2016. After this date, the only Windows PowerShell cmdlet that you need for AIP Service usage logging is Get-AipServiceUserLog.

For more information about usage logging, see [Logging and analyzing usage of the Azure Information Protection service](https://docs.microsoft.com/information-protection/deploy-use/log-analyze-usage).

## EXAMPLES

### Example 1: Set the log location
```
PS C:\>$AccessKey = ConvertTo-SecureString "aeDpsMswiYNGNwOaCkOrfPiDtIpjRREosiXNLKrG" -AsPlainText -Force
PS C:\> Set-AipServiceUsageLogStorageAccount -AccessKey $AccessKey -StorageAccount "AIPServiceStorageAccount"
```

The first command uses the [ConvertTo-SecureString](http://go.microsoft.com/fwlink/?LinkID=113291) cmdlet to convert your access key to a secure string, and then stores it in the **$AccessKey** variable.
For more information, type `Get-Help ConvertTo-SecureString`.

The second command specifies the location for your usage logs.

## PARAMETERS

### -AccessKey
Specifies your access key as a secure string.

To view your access key, connect to the Azure portal.

```yaml
Type: SecureString
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -StorageAccount
Specifies a storage account.

To obtain the name of this account, use the Azure portal.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-AipServiceUsageLogStorageAccount](./Get-AipServiceUsageLogStorageAccount.md)

[ConvertTo-SecureString](http://go.microsoft.com/fwlink/?LinkID=113291)

[Logging and analyzing usage of the Azure Information Protection service](https://docs.microsoft.com/information-protection/deploy-use/log-analyze-usage)
