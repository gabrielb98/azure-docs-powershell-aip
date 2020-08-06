---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2137317
schema: 2.0.0
---

# Install-MIPNetworkDiscovery

## SYNOPSIS
Installs the Azure Information Protection Network Discovery service.

## SYNTAX

```
Install-MIPNetworkDiscovery [-ServiceUserCredentials] <PSCredential>
 [[-StandardDomainsUserAccount] <PSCredential>] [[-ShareAdminUserAccount] <PSCredential>]
 [-SqlServerInstance] <String> -Cluster <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Install-MIPNetworkDiscovery** cmdlet installs the Network Discovery service, which enables AIP administrators to scan a specified IP address or range for possibly risky repositories, using a network scan job.

Use network scan job results to identify additional repositories in your network to further scan using a content scan job. For more information, see [Create a network scan job](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner-configure-install#create-a-network-scan-job-public-preview).

> [!IMPORTANT]
> You must run this cmdlet before you run any other cmdlet for the Azure Information Protection Network Discovery service.
> 

After you have run this command, use the Azure portal to configure the settings in the scanner's network scan jobs. Before you run the scanner, you must run the [Set-MIPNetworkDiscoveryConfiguration](./Set-MIPNetworkDiscoveryConfiguration.md) cmdlet one time to sign in to Azure AD for authentication and authorization. 


## EXAMPLES

### Example 1: Install the Network Discovery service by using a SQL Server instance
```
PS C:\> Install-MIPNetworkDiscovery -SqlServerInstance SQLSERVER1\AIPSCANNER
```

This command installs the Azure Information Protection Network Discovery service by using a SQL Server instance named **AIPSCANNER,** which runs on the server named SQLSERVER1. 

- You are prompted to provide the Active Directory account details for the scanner service account. 
- If an existing database AIPScannerUL_EU isn't found on the specified SQL Server instance, a new database with this name is created to store the scanner configuration. 
- The command displays the installation progress, where the install log is located, and the creation of the new Windows Application event log, named Azure Information Protection Scanner.
- At the end of the output, you see **The transacted install has completed**.

### Example 2: Install the Network Discovery service by using the SQL Server default instance
```
PS C:\> Install-MIPNetworkDiscovery -SqlServerInstance SQLSERVER1
```

This command installs the Azure Information Protection Network Discovery service by using the SQL Server default instance that runs on the server, named **SQLSERVER1.** 

As with the previous example, you are prompted for credentials, and then the command displays the progress, where the install log is located, and the creation of the new Windows Application event log.

### Example 3: Install the Network Discovery service by using SQL Server Express
```
PS C:\> Install-MIPNetworkDiscovery -SqlServerInstance SQLSERVER1\SQLEXPRESS 
```

This command installs the Network Discovery service by using SQL Server Express that runs on the server named **SQLSERVER1.** 

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

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ServiceUserCredentials
Specifies a **PSCredential** object for the service account to run the Azure Information Protection Scanner service. For the user name, use the following format: Domain\Username. You are prompted for a password. 

To obtain a PSCredential object, use the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential) cmdlet. For more information, type `Get-Help Get-Cmdlet`. 

If you do not specify this parameter, you are prompted for the user name and password.

This account must be an Active Directory account. For additional requirements, see [Prerequisites for the Azure Information Protection scanner](https://docs.microsoft.com/information-protection/deploy-aip-scanner#prerequisites-for-the-azure-information-protection-scanner).

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

The user impersonated by the Network Discovery service when scanning the configured network locations to understand whether admin access is available on each location.

The value for this parameter is a **PSCredential** object for the admin account, usually the domain administrator account. The PSCredential object is used to get full access, with NTFS permissions, to the network locations you want to scan with your network scan jobs.

- Use the following syntax for the username: `Domain\Username`. 
- When prompted, enter the password for the account.
- If you do not specify this parameter, you are prompted for both your user name and password.

> [!TIP]
> To obtain a PSCredential object, use the [**Get-Credential**](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential) cmdlet. For more information, type `Get-Help Get-Cmdlet`.
> 

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SqlServerInstance

Specifies the SQL Server instance on which to create a database for the Azure Information Protection scanner.

For information about the SQL Server requirements, see [Prerequisites for the Azure Information Protection scanner](https://docs.microsoft.com/information-protection/deploy-aip-scanner#prerequisites-for-the-azure-information-protection-scanner).

- For the default instance, specify the server name. For example: `SQLSERVER1`. 
- For a named instance, specify the server name and instance name. For example: `SQLSERVER1\AIPSCANNER`.
- For SQL Server Express, specify the server name and SQLEXPRESS. For example: `SQLSERVER1\SQLEXPRESS`.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StandardDomainsUserAccount

The user impersonated by the Network Discovery service when scanning the configured network locations to understand whether public access is available on each location.

The value for this parameter is a **PSCredential** object for a weak domain account, usually a domain user or a domain guest account. The PSCredential object is used to get public access to the network locations you want to scan with your network scan jobs.

- Use the following syntax for the username: `Domain\Username`. 
- When prompted, enter the password for the account.
- If you do not specify this parameter, you are prompted for both your user name and password.

> [!TIP]
> To obtain a PSCredential object, use the [**Get-Credential**](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential) cmdlet. For more information, type `Get-Help Get-Cmdlet`.
> 

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
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

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Get-AIPScannerStatus](./Get-AIPScannerStatus.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Start-AIPScan](./Start-AIPScan.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Update-AIPScanner](./Update-AIPScanner.md)
