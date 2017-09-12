---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=xxxx
schema: 2.0.0
---

# Install-AIPScanner

## SYNOPSIS
Installs the Azure Information Protection Scanner service.

## SYNTAX

```
Install-AIPScanner [-ServiceUserCredentials] <PSCredential> [-SqlServerInstance] <String>
```

## DESCRIPTION
The Install-AIPScanner cmdlet installs and configures the Azure Information Protection Scanner service on a computer running Windows Server 2016 or Windows Server 2012 R2. This service can scan files on data stores that use the Common Internet File System (CIFS) protocol, and on SharePoint Server 2016 and SharePoint Server 2013. By using the conditions that you configure in the Azure Information Protection policy, files that this service discovers can then be labeled, and optionally, protected. 

You must run this cmdlet before you run any other cmdlet for the Azure Information Protection Scanner service.

The command creates a Windows service named Azure Information Protection Scanner, creates and configures a database on SQL Server, and grants the required rights to an account that you specify to run this scanner service.

To run this command, you must have local Administrator rights for the Windows Server computer, and Sysadmin rights on the instance of SQL Server that you will use for the scanner.

Note: This cmdlet and the Azure Information Protection Scanner feature is currently in preview and subject to change.

## EXAMPLES

### Example 1:Install the Azure Information Protection Scanner service by using a SQL Server instance named AIPSCANNER that runs on the server named SQLSERVER1
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

### Example 2: Install the Azure Information Protection Scanner service by using the SQL Server default instance that runs on the server named SQLSERVER1
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

### Example 3: Install the Azure Information Protection Scanner service by using SQL Express that runs on a server named SQLSERVER1
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
## PARAMETERS

### -ServiceUserCredentials
Specifies a **PSCredential** object for the account to run the Azure Information Protection Scanner service. For the user name, use the following format: Domain\Username. You are prompted for a password. 

To obtain a PSCredential object, use the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential) cmdlet. For more information, type `Get-Help Get-Cmdlet`. 

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
Specifies the SQL Server instance on which to create a database for the Azure Information Protection Scanner service. 

You can use a local or remote SQL Server instance when SQL Server 2012 R2 is the minimum version on the following editions:

- SQL Server Express

- SQL Server Standard

- SQL Server Enterprise

For local default instance, specify the server name. For example: SQLSERVER1. 

For a named instance, specify the server name and instance name. For exmaple: SQLSERVER1\AIPSCANNER. 

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

[Get-​AI​PFile​Status](./Get-AIPFileStatus.md)

