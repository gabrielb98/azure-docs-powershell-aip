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
Set-AIPScanner [[-SqlServerInstance] <String>] [-ServiceUserCredentials] <PSCredential> [<CommonParameters>]
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
Specifies a PSCredential object for the new service account to run the Azure Information Protection Scanner service. For the user name, use the following format: Domain\Username. You are prompted for a password.

To obtain a PSCredential object, use the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential) cmdlet. For more information, type `Get-Help Get-Cmdlet`.

If you do not specify this parameter, you are prompted for the user name and password.

This account must be an Active Directory account. For additional requirements, see [Prerequisites for the Azure Information Protection scanner](https://docs.microsoft.com/information-protection/deploy-use/deploy-aip-scannerpPrerequisites-for-the-azure-information-protection-scanner). 

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

For information about the SQL Server requirements, see [Prerequisites for the Azure Information Protection scanner](https://docs.microsoft.com/information-protection/deploy-use/deploy-aip-scannerpPrerequisites-for-the-azure-information-protection-canner).

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.
For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md) 

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md) 

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md) 

[Install-AIPScanner](./Install-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Set-AIPScannerConfiguration]()

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

