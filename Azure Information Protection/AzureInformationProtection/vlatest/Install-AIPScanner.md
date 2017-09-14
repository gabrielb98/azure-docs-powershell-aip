---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=858203
schema: 2.0.0
---

# Install-AIPScanner

## SYNOPSIS
Installs the Windows Server service for the Azure Information Protection scanner.

## SYNTAX

```
Install-AIPScanner [-ServiceUserCredentials] <PSCredential> [-SqlServerInstance] <String>
```

## DESCRIPTION
The Install-AIPScanner cmdlet installs and configures the Azure Information Protection Scanner service on a computer running Windows Server 2016 or Windows Server 2012 R2. The Azure Information Protection scanner uses this service to scan files on data stores that use the Common Internet File System (CIFS) protocol, and on SharePoint Server 2016 and SharePoint Server 2013. By using the conditions that you configure for automatic classification in the Azure Information Protection policy, files that this scanner discovers can then be labeled. Labels apply classification, and optionally, apply protection or remove protection.

For more information about how to configure the Azure Information Protection policy, see [Configuring the Azure Information Protection policy](https://docs.microsoft.com/information-protection/deploy-use/configure-policy).

You must run this cmdlet before you run any other cmdlet for the Azure Information Protection scanner.

The command creates a Windows service named Azure Information Protection Scanner, creates and configures a database on SQL Server, and grants the required rights to an account that you specify to run the scanner service.

To run this command, you must have local Administrator rights for the Windows Server computer, and Sysadmin rights on the instance of SQL Server that you will use for the scanner.

Note: If you later need to change the account and database that you specified when you ran this cmdlet, you can do so by using the [Set-AIPScanner](./Set-AIPScanner.md) cmdlet.

After you have run this command, specify the data repositories to scan by using the [Add-AIPScannerRepository](./Add-AIPScannerRepository.md) cmdlet. Then check whether you need to change any of the default configuration options that can be set by using the [Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md) cmdlet. Before you run the scanner, you must run the [Set-AIPAuthentication](./Set-AIPAuthentication.md) cmdlet one time to sign in to Azure AD for authentication and authorization. 

For step-by-step instructions to install, configure, and use the scanner, see [Deploying the Azure Information Protection scanner to automatically classify and protect files](https://docs.microsoft.com/information-protection/deploy-use/deploy-aip-scanner).

## EXAMPLES

### Example 1:Install the Azure Information Protection Scanner service by using a SQL Server instance
```
PS C:\> Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER

cmdlet Install-AIPScanner at command pipeline position 1
Supply values for the following parameters:
ServiceUserCredentials

Running a transacted installation.

Beginning the Install phase of the installation.
See the contents of the log file for the C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe
The file is located at C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.InstallLog.
Installing assembly 'C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe'.
Affected parameters are:
   logtoconsole =
   assemblypath = C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe
   logfile = C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.InstallLog
   user = res\aipscannersvc
   password = ********
Installing service Azure Information Protection Scanner...
Service Azure Information Protection Scanner has been successfully installed.
Creating EventLog source Azure Information Protection Scanner in log Application...

The Install phase completed successfully, and the Commit phase is beginning.
See the contents of the log file for the C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe
The file is located at C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.InstallLog.
Committing assembly 'C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe'.
Affected parameters are:
   logtoconsole =
   assemblypath = C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe
   logfile = C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.InstallLog
   user = res\aipscannersvc
   password = ********

The Commit phase completed successfully.

The transacted install has completed.

```

This command installs the Azure Information Protection Scanner service by using a SQL Server instance named AIPSCANNER, which runs on the server named SQLSERVER1. It prompts for credentials, and then displays the progress, where the install log is located, and the creation of the new Windows Application event log named Azure Information Protection Scanner.

### Example 2: Install the Azure Information Protection Scanner service by using the SQL Server default instance
```
PS C:\> Install-AIPScanner -SqlServerInstance SQLSERVER1

cmdlet Install-AIPScanner at command pipeline position 1
Supply values for the following parameters:
ServiceUserCredentials

Running a transacted installation.

Beginning the Install phase of the installation.
See the contents of the log file for the C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe
The file is located at C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.InstallLog.
Installing assembly 'C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe'.
Affected parameters are:
   logtoconsole =
   assemblypath = C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe
   logfile = C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.InstallLog
   user = res\aipscannersvc
   password = ********
Installing service Azure Information Protection Scanner...
Service Azure Information Protection Scanner has been successfully installed.
Creating EventLog source Azure Information Protection Scanner in log Application...

The Install phase completed successfully, and the Commit phase is beginning.
See the contents of the log file for the C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe
The file is located at C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.InstallLog.
Committing assembly 'C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe'.
Affected parameters are:
   logtoconsole =
   assemblypath = C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe
   logfile = C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.InstallLog
   user = res\aipscannersvc
   password = ********

The Commit phase completed successfully.

The transacted install has completed.
```

This command installs the Azure Information Protection Scanner service by using the SQL Server default instance that runs on the server named SQLSERVER1. As with the previous example, you are prompted for credentials, and then the command displays the progress, where the install log is located, and the creation of the new Windows Application event log.


### Example 3: Install the Azure Information Protection Scanner service by using SQL Express 
```
PS C:\> Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS

cmdlet Install-AIPScanner at command pipeline position 1
Supply values for the following parameters:
ServiceUserCredentials

Running a transacted installation.

Beginning the Install phase of the installation.
See the contents of the log file for the C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe
The file is located at C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.InstallLog.
Installing assembly 'C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe'.
Affected parameters are:
   logtoconsole =
   assemblypath = C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe
   logfile = C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.InstallLog
   user = res\aipscannersvc
   password = ********
Installing service Azure Information Protection Scanner...
Service Azure Information Protection Scanner has been successfully installed.
Creating EventLog source Azure Information Protection Scanner in log Application...

The Install phase completed successfully, and the Commit phase is beginning.
See the contents of the log file for the C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe
The file is located at C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.InstallLog.
Committing assembly 'C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe'.
Affected parameters are:
   logtoconsole =
   assemblypath = C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.exe
   logfile = C:\Program Files (x86)\Microsoft Azure Information Protection\MSIP.Scanner.InstallLog
   user = res\aipscannersvc
   password = ********

The Commit phase completed successfully.

The transacted install has completed.
```

This command installs the Azure Information Protection Scanner service by using SQL Server Express that runs on the server named SQLSERVER1. As with the previous examples, you are prompted for credentials, and then the command displays the progress, where the install log is located, and the creation of the new Windows Application event log.

## PARAMETERS

### -ServiceUserCredentials
Specifies a **PSCredential** object for the account to run the Azure Information Protection Scanner service. For the user name, use the following format: Domain\Username. You are prompted for a password. 

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
Specifies the SQL Server instance on which to create a database for the Azure Information Protection scanner. 

The account that runs the Azure Information Protection scanner is automatically granted permissions to read and write to this database.

You can use a local or remote SQL Server instance when SQL Server 2012 R2 is the minimum version on the following editions:

- SQL Server Express

- SQL Server Standard

- SQL Server Enterprise

For the default instance, specify the server name. For example: SQLSERVER1. 

For a named instance, specify the server name and instance name. For example: SQLSERVER1\AIPSCANNER. 

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

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)

