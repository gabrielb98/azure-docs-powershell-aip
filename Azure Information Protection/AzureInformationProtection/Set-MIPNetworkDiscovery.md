---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2144638
schema: 2.0.0
---

# Set-MIPNetworkDiscovery

## SYNOPSIS
Updates the installation settings for the Network Discovery service.

## SYNTAX

```
Set-MIPNetworkDiscovery [[-SqlServerInstance] <String>] [-ServiceUserCredentials] <PSCredential>
 [-StandardDomainsUserAccount <PSCredential>] [-ShareAdminUserAccount <PSCredential>] -Cluster <String> [-Force] 
 [<CommonParameters>]
```

## DESCRIPTION
The **Set-MIPNetworkDiscovery** cmdlet updates installation settings for the Network Discovery service. 

The Network Discovery service enables AIP administrators to scan a specified IP address or range for possibly risky repositories, using a network scan job.

Use network scan job results to identify additional repositories in your network to further scan using a content scan job. For more information, see [Create a network scan job](/azure/information-protection/deploy-aip-scanner-configure-install#create-a-network-scan-job-public-preview).

## EXAMPLES

### Example 1: Update the Network Discovery service settings by using a SQL Server instance

```PS
PS C:\> $serviceacct= Get-Credential -UserName domain\scannersvc -Message ScannerAccount
PS C:\> $shareadminacct= Get-Credential -UserName domain\adminacct -Message ShareAdminAccount
PS C:\> $publicaccount= Get-Credential -UserName domain\publicuser -Message PublicUser
PS C:\> Set-MIPNetworkDiscovery -SqlServerInstance SQLSERVER1\AIPSCANNER -Cluster EU -ServiceUserCredentials $serviceacct  -ShareAdminUserAccount $shareadminacct -StandardDomainsUserAccount $publicaccount 
```

This command updates the settings for the Network Discovery service by using a SQL Server instance named **AIPSCANNER**, which runs on the server named **SQLSERVER1**. 

- You are prompted to provide the Active Directory account details for the scanner service account. 
- If an existing database named **AIPScannerUL_EU** isn't found on the specified SQL Server instance, a new database with this name is created to store the scanner configuration. 
- The command displays the update progress, where the install log is located, and the creation of the new Windows Application event log, named **Azure Information Protection Scanner**.
- At the end of the output, you see **The transacted install has completed**.

**Accounts used in this example**

The following table lists the accounts used in this example for activity:

|Activity  |Account description  |
|---------|---------|
|**Running the service**     |  The service is run using the **domain\scannersvc** account.       |
|**Checking permissions**     |  The service checks the permissions of the discovered shares using the **domain\adminacct** account. </br></br>This account should be the admin account on your shares.       |
|**Checking public exposure**    |    The service will check the share's public exposure using the **domain\publicuser** account. </br></br>This user should be a standard Domain user, and a member of the **Domain Users** group only.     |


### Example 2: Update the Network Discovery service settings by using the SQL Server default instance
```PS
PS C:\> $serviceacct= Get-Credential -UserName domain\scannersvc -Message ScannerAccount
PS C:\> $shareadminacct= Get-Credential -UserName domain\adminacct -Message ShareAdminAccount
PS C:\> $publicaccount= Get-Credential -UserName domain\publicuser -Message PublicUser
PS C:\> Set-MIPNetworkDiscovery -SqlServerInstance SQLSERVER1 -Cluster EU -ServiceUserCredentials $serviceacct  -ShareAdminUserAccount $shareadminacct -StandardDomainsUserAccount $publicaccount

```

This command updates the settings for the the Network Discovery service by using the SQL Server default instance that runs on the server, named **SQLSERVER1**, as well as the settings for the ShareAdminUserAccount and the StandardDomainsUserAccount.  


As with the previous example, you are prompted for credentials, and then the command displays the progress, where the install log is located, and the creation of the new Windows Application event log.

### Example 3: Update the settings for the Network Discovery service by using SQL Server Express
```PS
PS C:\> $serviceacct= Get-Credential -UserName domain\scannersvc -Message ScannerAccount
PS C:\> $shareadminacct= Get-Credential -UserName domain\adminacct -Message ShareAdminAccount
PS C:\> $publicaccount= Get-Credential -UserName domain\publicuser -Message PublicUser
PS C:\> Set-MIPNetworkDiscovery -SqlServerInstance SQLSERVER1\SQLEXPRESS -Cluster EU -ServiceUserCredentials $serviceacct  -ShareAdminUserAccount $shareadminacct -StandardDomainsUserAccount $publicaccount
 
```

This command updates the settings for the Network Discovery service by using SQL Server Express that runs on the server named **SQLSERVER1**. 

As with the previous examples, you are prompted for credentials, and then the command displays the progress, where the install log is located, and the creation of the new Windows Application event log.

## PARAMETERS

### -Cluster
The name of your scanner instance, as defined by your scanner cluster name.

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
Specifies the SQL Server instance on which to create a database for the Network Discovery service.

For information about the SQL Server requirements, see [Prerequisites for the Azure Information Protection scanner](/azure/information-protection/deploy-aip-scanner#prerequisites-for-the-azure-information-protection-scanner).

- For the default instance, specify the server name. For example: `SQLSERVER1`. 
- For a named instance, specify the server name and instance name. For example: `SQLSERVER1\AIPSCANNER`.
- For SQL Server Express, specify the server name and SQLEXPRESS. For example: `SQLSERVER1\SQLEXPRESS`.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

### None

## OUTPUTS

### System.Object
## NOTES

## RELATED LINKS

[Get-MIPNetworkDiscoveryConfiguration](Get-MIPNetworkDiscoveryConfiguration.md)

[Get-MIPNetworkDiscoveryJobs](Get-MIPNetworkDiscoveryJobs.md)

[Get-MIPNetworkDiscoveryStatus](Get-MIPNetworkDiscoveryStatus.md)

[Import-MIPNetworkDiscoveryConfiguration](Import-MIPNetworkDiscoveryConfiguration.md)

[Set-MIPNetworkDiscovery](Set-MIPNetworkDiscovery.md)

[Set-MIPNetworkDiscoveryConfiguration](Set-MIPNetworkDiscoveryConfiguration.md)

[Start-MIPNetworkDiscovery](Start-MIPNetworkDiscovery.md)

[Uninstall-MIPNetworkDiscovery](Uninstall-MIPNetworkDiscovery.md)