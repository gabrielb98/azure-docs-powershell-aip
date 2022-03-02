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
Set-AIPScanner [[-SqlServerInstance] <String>] [-ServiceUserCredentials] <PSCredential>
 [-StandardDomainsUserAccount <PSCredential>] [-ShareAdminUserAccount <PSCredential>] [-Cluster | -Profile <String>] [-Force] 
 [<CommonParameters>]
```

## DESCRIPTION
The **Set-AIPScanner** cmdlet updates the service account and SQL Server database instance for the Azure Information Protection scanner. 

Use this command when you want to change the account or database details that was previously specified, for example, when you installed the scanner by running the [Install-AIPScanner](./Install-AIPScanner.md) cmdlet.

The new configuration takes effects when the Azure Information Protection Scanner service is next started. This cmdlet does not automatically restart this service.


## EXAMPLES

### Example 1: Change the database and cluster for the Azure Information Protection scanner
```
PS C:\> Set-AIPScanner -SqlServerInstance SERVER1\AIPSCANNER -Cluster EU

Azure Information Protection Scanner service configuration change completed successfully.
```

This command configures the Azure Information Protection scanner to use the SQL Server database instance named **AIPSCANNER** on the server named **SERVER1**, using the scanner configuration database named **AIPScanner_EU**.

## PARAMETERS

### -Cluster
**Relevant for:** Unified labeling client only.

Specifies the configured name of the scanner's database, used to identify the scanner you want to set details for.

Use the following syntax: **AIPScannerUL_<cluster_name>**. 

Using either this parameter or the **Profile** parameter is mandatory. Starting in version 2.7.0.0 of the unified labeling client, we recommend using this parameter instead of the **Profile** parameter.


```yaml
Type: String
Parameter Sets: (All)
Aliases: Profile

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
Forces the command to run without asking for user confirmation.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Profile
Specifies the configured name of the scanner's database, used to identify the scanner you want to set details for.

Using either this parameter or the **Cluster** parameter is mandatory. Starting in version 2.7.0.0 of the unified labeling client, we recommend using the **Cluster** parameter instead of the this parameter.

The database name for the scanner is **AIPScannerUL_\<profile_name>**. 


### -ServiceUserCredentials
Specifies the account credentials used to run the Azure Information Protection service. 

- The credentials used must be an Active Directory account. 

- Set the value of this parameter using the following syntax: `Domain\Username`. 

    For example: `contoso\scanneraccount`

- If you do not specify this parameter, you are prompted for the username and password.

For more information, see [Prerequisites for the Azure Information Protection scanner](/information-protection/deploy-aip-scanner#prerequisites-for-the-azure-information-protection-scanner). 

> [!TIP]
> Use a **PSCredential** object by using the [Get-Credential](/powershell/module/microsoft.powershell.security/get-credential) cmdlet. In this case, you are prompted for the password only.
>
> For more information, type `Get-Help Get-Cmdlet`. 

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

### -ShareAdminUserAccount
Specifies the credentials for a strong account in an on-premises network, used to get a full list of file share and NTFS permissions.

- The credentials used must be an Active Directory account with Administrator/FC rights on your network shares. This will usually be a Server Admin or Domain Admin.

- Set the value of this parameter using the following syntax: `Domain\Username`

    For example: `contoso\admin`

- If you do not specify this parameter, you are prompted for both the username and password.

> [!TIP]
> Use a **PSCredential** object by using the [**Get-Credential**](/powershell/module/microsoft.powershell.security/get-credential) cmdlet. In this case, you are prompted for the password only.
> 
>For more information, type `Get-Help Get-Cmdlet`.

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

### -SqlServerInstance
Specifies the new SQL Server instance on which to create a database for the Azure Information Protection scanner.

For information about the SQL Server requirements, see [Prerequisites for the Azure Information Protection scanner](/azure/information-protection/deploy-aip-scanner#prerequisites-for-the-azure-information-protection-scanner).

For the default instance, specify the server name. For example: **SQLSERVER1**.

For a named instance, specify the server name and instance name. For example: **SQLSERVER1\AIPSCANNER**.

For SQL Server Express, specify the server name and SQLEXPRESS. For example: **SQLSERVER1\SQLEXPRESS**.

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

### -StandardDomainsUserAccount
Specifies the credentials for a weak account in an on-premises network, used to check access for weak users on the network and expose discovered network shares.

- The credentials used must be an Active Directory account, and a user of the **Domain Users** group only.

- Set the value of this parameter using the following syntax: `Domain\Username`

    For example: `contoso\stduser`

- If you do not specify this parameter, you are prompted for both the username and password.

> [!TIP]
> Use a **PSCredential** object by using the [**Get-Credential**](/powershell/module/microsoft.powershell.security/get-credential) cmdlet. In this case, you are prompted for the password only.
> 
>For more information, type `Get-Help Get-Cmdlet`.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. 

For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

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