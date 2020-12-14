---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=858203
schema: 2.0.0
---

# Install-AIPScanner

## SYNOPSIS
**Relevant for:** AIP unified labeling and classic clients

Installs the Azure Information Protection scanner.

## SYNTAX

```
Install-AIPScanner [-ServiceUserCredentials] <PSCredential> [-StandardDomainsUserAccount <PSCredential>]
 [-ShareAdminUserAccount <PSCredential>] [-SqlServerInstance] [-Cluster | -Profile <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Install-AIPScanner** cmdlet installs and configures the Azure Information Protection Scanner service on a computer running Windows Server 2019, Windows Server 2016, or Windows Server 2012 R2. 

The Azure Information Protection scanner uses this service to scan files on data stores that use the Server Message Block (SMB) protocol, and on SharePoint on premises. Files that this scanner discovers can then be labeled to apply classification, and optionally, apply protection or remove protection.

For more information about how to configure the labels and policy settings, see: 

- **Unified labeling client:** [Overview of sensitivity labels](/microsoft-365/compliance/sensitivity-labels)

- **Classic client:** [Configuring the Azure Information Protection policy](/information-protection/configure-policy)

> [!IMPORTANT]
> You must run this cmdlet before you run any other cmdlet for the Azure Information Protection scanner.
> 
The command creates a Windows service named Azure Information Protection Scanner. It also creates and configures a database on SQL Server to store configuration and operational information for the scanner. The service that you specify to run the scanner is automatically granted the required rights to read and write to the database that is created.

To run this command, you must have local administrator rights for the Windows Server computer, and Sysadmin rights on the instance of SQL Server that you will use for the scanner.

After you have run this command, use the Azure portal to configure the settings in the scanner cluster and specify the data repositories to scan. Before you run the scanner, you must run the [Set-AIPAuthentication](./Set-AIPAuthentication.md) cmdlet one time to sign in to Azure AD for authentication and authorization. 

For step-by-step instructions to install, configure, and use the scanner, see:

- [Unified labeling client instructions for deploying the AIP scanner](/information-protection/deploy-aip-scanner)
- [Classic client instructions for deploying the AIP scanner](/information-protection/deploy-aip-scanner)

> [!NOTE]
> To provide a unified and streamlined customer experience, the **Azure Information Protection classic client** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021**. 
> 
> This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).
>

## EXAMPLES

### Example 1: Install the Azure Information Protection Scanner service by using a SQL Server instance and a cluster
```
PS C:\> Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER -Cluster EU
```

This command installs the Azure Information Protection Scanner service by using a SQL Server instance named **AIPSCANNER**, which runs on the server named **SQLSERVER1**. 

In addition, the installation creates one of the following database names to store the scanner configuration, unless an existing database with the same name is already found.

- Unified labeling client: **AIPScannerUL_\<cluster name>**
- Classic client: **AIPScanner_EU**

You are prompted to provide the Active Directory account details for the scanner service account. 

The command displays the installation progress, where the install log is located, and the creation of the new Windows Application event log named Azure Information Protection Scanner

At the end of the output, you see **The transacted install has completed**.

> [!NOTE]
> The cluster parameter is only supported in the unified labeling client, version 2.7.0.0 and above. For other versions, use the **Profile** parameter instead.

### Example 2: Install the Azure Information Protection Scanner service by using the SQL Server default instance
```
PS C:\> Install-AIPScanner -SqlServerInstance SQLSERVER1 -Cluster EU
```

This command installs the Azure Information Protection Scanner service by using the SQL Server default instance that runs on the server named **SQLSERVER1**. 

As with the previous example, you are prompted for credentials, and then the command displays the progress, where the install log is located, and the creation of the new Windows Application event log.

> [!NOTE]
> The cluster parameter is only supported in the unified labeling client, version 2.7.0.0 and above. For other versions, use the **Profile** parameter instead.
### Example 3: Install the Azure Information Protection Scanner service by using SQL Server Express
```
PS C:\> Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS -Cluster EU
```

This command installs the Azure Information Protection Scanner service by using SQL Server Express that runs on the server named **SQLSERVER1**. 

As with the previous examples, you are prompted for credentials, and then the command displays the progress, where the install log is located, and the creation of the new Windows Application event log.

> [!NOTE]
> The cluster parameter is only supported in the unified labeling client, version 2.7.0.0 and above. For other versions, use the **Profile** parameter instead.
## PARAMETERS

### -Cluster
**Relevant for:** Unified labeling client only.

Specifies the name of the scanner's database for the scanner configuration, using the following syntax: **AIPScannerUL_<cluster_name>**. 

If the database that you name doesn't exist when the scanner is installed, this command creates it.

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

### -Profile
Specifies the name of the scanner's database for the scanner configuration.

- **Unified labeling client:**  Using either this parameter or the **Cluster** parameter is mandatory. Starting in version 2.7.0.0 of the unified labeling client, we recommend using the **Cluster** parameter instead of the this parameter.

    The database name for the scanner is **AIPScannerUL_\<profile_name>**. 

    If the database that you name doesn't exist when the scanner is installed, this command creates it.

- **Classic client:** This parameter is optional. 

    - If you don't specify it, the default database name for the scanner is **AIPScanner_\<computer_name>**. 

    - If you do specify it, the database name for the scanner is **AIPScanner_\<profile_name>**.


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
Specifies the SQL Server instance on which to create a database for the Azure Information Protection scanner. 

For information about the SQL Server requirements, see [Prerequisites for the Azure Information Protection scanner](/information-protection/deploy-aip-scanner#prerequisites-for-the-azure-information-protection-scanner).

- **For the default instance**, specify the server name. For example: **SQLSERVER1**. 

- **For a named instance**, specify the server name and instance name. For example: **SQLSERVER1\AIPSCANNER**. 

- **For SQL Server Express**, specify the server name and **SQLEXPRESS**. For example: **SQLSERVER1\SQLEXPRESS**.


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

### -WhatIf
Shows what would happen if the cmdlet runs. The cmdlet is not run.

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

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Start-AIPScan](./Start-AIPScan.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Update-AIPScanner](./Update-AIPScanner.md)
