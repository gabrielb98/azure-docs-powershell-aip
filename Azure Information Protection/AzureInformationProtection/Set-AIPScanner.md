---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=858209
schema: 2.0.0
---

# Set-AIPScanner

## SYNOPSIS
Sets the service account and database for the Azure Information Protection scanner.

## SYNTAX

```
Set-AIPScanner [[-SqlServerInstance] <String>] [-ServiceUserCredentials] <PSCredential> [-Profile <String>] [<CommonParameters>]
```

## DESCRIPTION
The Set-AIPScanner cmdlet updates the service account and SQL Server database instance for the Azure Information Protection scanner. Use this command when you want to change the account or database details that was previously specified, for example, when you installed the scanner by running the [Install-AIPScanner](./Install-AIPScanner.md) cmdlet.

The new configuration takes effects when the Azure Information Protection Scanner service is next started. This cmdlet does not automatically restart this service.

## EXAMPLES

### Example 1: Change the database and profile for the Azure Information Protection scanner
```
PS C:\> Set-AIPScanner -SqlServerInstance SERVER1\AIPSCANNER -Profile EU

Azure Information Protection Scanner service configuration change completed successfully.
```

This command configures the Azure Information Protection scanner to use the SQL Server database instance named AIPSCANNER on the server named SERVER1, using the scanner configuration database named AIPScanner_EU.


## PARAMETERS

### -ServiceUserCredentials
Specifies a **PSCredential** object for the new service account to run the Azure Information Protection Scanner service. For the user name, use the following format: Domain\Username. You are prompted for a password.

To obtain a PSCredential object, use the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential) cmdlet. For more information, type `Get-Help Get-Cmdlet`.

If you do not specify this parameter, you are prompted for the user name and password.

This account must be an Active Directory account. For additional requirements, see [Prerequisites for the Azure Information Protection scanner](https://docs.microsoft.com/en-us/azure/information-protection/deploy-aip-scanner#prerequisites-for-the-azure-information-protection-scanner). 

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SqlServerInstance
Specifies the new SQL Server instance on which to create a database for the Azure Information Protection scanner.

For information about the SQL Server requirements, see [Prerequisites for the Azure Information Protection scanner](https://docs.microsoft.com/en-us/azure/information-protection/deploy-aip-scanner#prerequisites-for-the-azure-information-protection-scanner).

For the default instance, specify the server name. For example: SQLSERVER1.

For a named instance, specify the server name and instance name. For example: SQLSERVER1\AIPSCANNER.

For SQL Server Express, specify the server name and SQLEXPRESS. For example: SQLSERVER1\SQLEXPRESS.

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

### -Profile 
Note: For the scanner from the unified labeling client, this parameter is required.

Specifies that the scanner uses a named database name for its configuration. If this parameter is not specified for the scanner from the classic client, the default database name for the scanner is AIPScanner_\<computer_name>. When you specify a profile name, this database name changes to AIPScanner_\<profile_name>.

For the scanner from the unified labeling client, which must be installed with a profile name, the database name created is AIPScannerUL_\<profile_name>.

If the database doesn't exist when the scanner is installed, the Install-AIIPScanner command creates it. 

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Get-AIPScannerStatus](./Get-AIPScannerStatus.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Start-AIPScan](./Start-AIPScan.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Update-AIPScanner](./Update-AIPScanner.md)

