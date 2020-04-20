---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=858203
schema: 2.0.0
---

# Install-AIPScanner

## SYNOPSIS
Installs the Azure Information Protection scanner.

## SYNTAX

```
Install-AIPScanner [-ServiceUserCredentials] <PSCredential> [-SqlServerInstance] <String> [-Profile <String>] [<CommonParameters>]
```

## DESCRIPTION
The Install-AIPScanner cmdlet installs and configures the Azure Information Protection Scanner service on a computer running Windows Server 2019, Windows Server 2016, or Windows Server 2012 R2. The Azure Information Protection scanner uses this service to scan files on data stores that use the Server Message Block (SMB) protocol, and on SharePoint on premises. Files that this scanner discovers can then be labeled to apply classification, and optionally, apply protection or remove protection.

For more information about how to configure the labels and policy settings, see the following information:

For the scanner from the classic client: [Configuring the Azure Information Protection policy](https://docs.microsoft.com/information-protection/configure-policy)

For the scanner from the unified labeling client: [Overview of sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels)

You must run this cmdlet before you run any other cmdlet for the Azure Information Protection scanner.

The command creates a Windows service named Azure Information Protection Scanner. It also creates and configures a database on SQL Server to store configuration and operational information for the scanner. The service that you specify to run the scanner is automatically granted the required rights to read and write to the database that is created.

To run this command, you must have local administrator rights for the Windows Server computer, and Sysadmin rights on the instance of SQL Server that you will use for the scanner.

After you have run this command, use the Azure portal to configure the settings in the scanner profile and specify the data repositories to scan. Before you run the scanner, you must run the [Set-AIPAuthentication](./Set-AIPAuthentication.md) cmdlet one time to sign in to Azure AD for authentication and authorization. 

For step-by-step instructions to install, configure, and use the scanner, see [Deploying the Azure Information Protection scanner to automatically classify and protect files](https://docs.microsoft.com/information-protection/deploy-aip-scanner).

Note: If you have the Azure Information Protection unified labeling client, this version includes a preview version of the scanner that you can install for testing. For more information, see [Installing the Azure Information Protection scanner](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide#installing-the-azure-information-protection-scanner.md) from the admin guide for the unified labeling client.

## EXAMPLES

### Example 1: Install the Azure Information Protection Scanner service by using a SQL Server instance and a profile
```
PS C:\> Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER -Profile EU
```

This command installs the Azure Information Protection Scanner service by using a SQL Server instance named AIPSCANNER, which runs on the server named SQLSERVER1. In addition, the installation creates a database name of AIPScanner_EU (for the classic client) or AIPScannerUL_\<profile_name> (for the unified labeling client) to store the scanner configuration.

You are prompted to provide the Active Directory account details for the scanner service account. If an existing database named AIPScanner_EU (classic client) or AIPScannerUL_EU (unified labeling client) isn't found on the specified SQL Server instance, a new database with this name is created to store the scanner configuration. The command displays the installation progress, where the install log is located, and the creation of the new Windows Application event log named Azure Information Protection Scanner

At the end of the output, you see **The transacted install has completed**.


### Example 2: Install the Azure Information Protection Scanner service by using the SQL Server default instance
```
PS C:\> Install-AIPScanner -SqlServerInstance SQLSERVER1 -Profile EU
```

This command installs the Azure Information Protection Scanner service by using the SQL Server default instance that runs on the server named SQLSERVER1. As with the previous example, you are prompted for credentials, and then the command displays the progress, where the install log is located, and the creation of the new Windows Application event log.

### Example 3: Install the Azure Information Protection Scanner service by using SQL Server Express
```
PS C:\> Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS -Profile EU
```

This command installs the Azure Information Protection Scanner service by using SQL Server Express that runs on the server named SQLSERVER1. As with the previous examples, you are prompted for credentials, and then the command displays the progress, where the install log is located, and the creation of the new Windows Application event log.

### Example 4: Install the Azure Information Protection Scanner service by using a SQL Server IP, port and profile

```
PS C:\> Install-AIPScanner -SqlServerInstance 10.0.0.4,1433 -Profile EU
```
This command installs the Azure Information Protection Scanner service by using a SQL Server instance, which runs on the server with **IP 10.0.0.4** and SQL service listening on **Port 1433**. In addition, the installation creates a database name of **AIPScanner_EU** (for the classic client) and/or **AIPScannerUL_<profile_name>** (for the unified labeling client) to store the scanner configuration.

During installation, you'll be prompted to provide the Active Directory account details for the scanner service account. If an existing database named **AIPScanner_EU** (classic client) or **AIPScannerUL_EU** (unified labeling client) isn't found on the specified SQL Server instance, a new database with the relevant name  is created to store the scanner configuration. The command displays the installation progress, where the install log is located, and the creation of the new Windows Application event log named Azure Information Protection Scanner. At the end of the output, you'll see when the installation is completed. 

## PARAMETERS

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

### -SqlServerInstance
Specifies the SQL Server instance on which to create a database for the Azure Information Protection scanner. 

For information about the SQL Server requirements, see [Prerequisites for the Azure Information Protection scanner](https://docs.microsoft.com/information-protection/deploy-aip-scanner#prerequisites-for-the-azure-information-protection-scanner).

For the default instance, specify the server name. For example: SQLSERVER1. 
For a named instance, specify the server name and instance name. For example: SQLSERVER1\AIPSCANNER. You can use IP, port to use SQL instance listening on a specific IP and port.

For SQL Server Express, specify the server name and SQLEXPRESS. For example: SQLSERVER1\SQLEXPRESS.


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

### -Profile 
Note: This parameter is required for the scanner from the unified labeling client.

Specifies the scanner's database name for its configuration. 

For the Azure Information Protection client (classic), this parameter is optional and if you don't specify it, the default database name for the scanner is AIPScanner_\<computer_name>. When you specify a profile name with this parameter, the database name for the scanner is AIPScanner_\<profile_name>.

For the Azure Information Protection unified labeling client, this parameter isn't optional and you must specify a profile name. The database name for the scanner is AIPScannerUL_\<profile_name>.

If the database doesn't exist when the scanner is installed, the Install-AIPScanner command creates it. 

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

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Start-AIPScan](./Start-AIPScan.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Update-AIPScanner](./Update-AIPScanner.md)
