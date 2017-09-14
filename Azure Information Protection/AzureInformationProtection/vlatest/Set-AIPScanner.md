---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=858209
schema: 2.0.0
---

# Set-AIPScanner

## SYNOPSIS
Sets the Azure Information Protection Scanner service account and database instance.

## SYNTAX

```
Set-AIPScanner [[-SqlServerInstance] <String>] [-ServiceUserCredentials] <PSCredential>
```

## DESCRIPTION
The Set-AIPScanner cmdlet updates the service account and SQL Server database instance for the Azure Information Protection scanner. Use this command when you want to change the account or database details that was previously specified, for example, when you installed the scanner by running the [Install-AIPScanner](./Install-AIPScanner.md) cmdlet.

The new configuration takes effects when the Azure Information Protection Scanner service is next started. This cmdlet does not automatically restart this service.


## EXAMPLES

### Example 1: Change the database for the Azure Information Protection scanner
```
PS C:\> Set-AIPScanner -SqlServerInstance SERVER1\AIPSCANNER

Azure Information Protection Scanner service configuration change completed successfully.
```

This command configures the Azure Information Protection scanner to start using the SQL Server database instance named AIPSCANNER on the server named SERVER1. 

## PARAMETERS

### -ServiceUserCredentials
Specifies a **PSCredential** object for the new account to run the Azure Information Protection Scanner service. For the user name, use the following format: Domain\Username. You are prompted for a password. 

To obtain a PSCredential object, use the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential) cmdlet. For more information, type `Get-Help Get-Cmdlet`. 

This account must be an Active Directory account that requires the following:

- **Log on locally** right. This right is required for the installation and configuration of the scanner, but not for operation. You can remove this right after you have confirmed that the scanner can discover, classify, and protect files.

- **Log on as a service** right. This right is required for the installation, configuration, and operation of the scanner.

- For labels that apply or remove protection: The account must be synchronized to Azure AD and have an email account. In addition, this account must be a super user for the Azure Rights Management service. For more information about super users, see [Configuring super users for Azure Rights Management and discovery services or data recovery](https://docs.microsoft.com/information-protection/deploy-use/configure-super-users).

- Access to the data repositories to scan: Read permissions for discovery mode only (files are not classified or protected). Read and Write permissions for applying labels that meet the conditions in the Azure Information Protection policy. 


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

The account that runs the Azure Information Protection scanner is automatically granted permissions to read and write to this database.

You can use a local or remote SQL Server instance when SQL Server 2012 R2 is the minimum version on the following editions:

- SQL Server Express

- SQL Server Standard

- SQL Server Enterprise

For the default instance, specify the server name. For example: SQLSERVER1. 

For a named instance, specify the server name and instance name. For exmaple: SQLSERVER1\AIPSCANNER. 

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

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)
