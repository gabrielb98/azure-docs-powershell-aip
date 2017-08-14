---
Module Name: RMSProtection
Module Guid: XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
Download Help Link: {{Please enter FwLink manually}}
Help Version: {{Please enter version of help manually (X.X.X.X) format}}
Locale: en-US
ms.assetid: 35D99F89-BD73-457E-95C7-73857656FB59
---

# RMSProtection Module
## Description
The following list contains links to the help topics for the Microsoft Rights Management services (RMS) Protection cmdlets, which are installed with the [RMS Protection Tool](https://www.microsoft.com/en-us/download/details.aspx?id=47256). The RMS Protection tool is now replaced by the [Azure Information Protection client](/information-protection/rms-client/aip-client), which includes a new PowerShell module, [AzureInformationProtection](/powershell/azureinformationprotection/vlatest/aip).

In turn, the RMS Protection Tool replaced the AD RMS Bulk Protection Tool. Support for the AD RMS Bulk Protection Tool will stop March 1, 2017.

These RMS Protection cmdlets can be used with Azure Rights Management (Azure RMS) data protection from Azure Information Protection, or with Active Directory Rights Management Services (AD RMS) and these cmdlets supplement other PowerShell modules for these Rights Management deployments. Use these RMS Protection cmdlets to bulk protect and unprotect files for any file type.

The current version of the RMS Protection PowerShell module is **2.2.0.0**. If you have previously downloaded the tool and installed this module, run the following command to check the version: `(Get-Module RMSProtection -ListAvailable).Version`.

>**Tip**
>
>If you want to automatically protect files on a file share by using Windows Server File Resource Manager and File Classification Infrastructure, see the step-by-step instructions in [RMS Protection with Windows Server File Classification Infrastructure (FCI)](https://docs.microsoft.com/information-protection/rms-client/configure-fci).

The current release of the RMS Protection module has the following limitations:

- You can unprotect Outlook personal folders (.pst files), but you cannot currently natively protect these files or other container files by using the RMS Protection Tool.

- You can unprotect Outlook protected email messages (.rpmsg files) when they are in a Outlook personal folder (.pst), but you cannot unprotect .rpmsg files outside a personal folder.

- For Azure Rights Management only:

 - By default, the cmdlets are not supported outside North America. As a workaround, you can edit the registry, as documented in [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/en-us/library/mt433202.aspx). Without this registry change, authentication to the Azure Rights Management service fails outside the Azure North America region.

- For Windows 7 SP1 and Windows Server 2012:

 - The RMS Protection module does not automatically import when you first run the cmdlets in a Windows PowerShell session. For these operating system versions, you must manually import the module before you run the cmdlets: `Import-Module "%ProgramFiles%\WindowsPowerShell\Modules\RMSProtection\RMSProtection.dll"`

 - If the %*ProgramFiles*% environment variable does not work for you, specify the full path. For example, `Import-Module "C:\Program Files\WindowsPowerShell\Modules\RMSProtection\RMSProtection.dll"`.

To unprotect container files (.msf, .pst, .rar, .pst, .zip, and .7z), and to use multi-factor authentication with Azure Rights Management, you must have at least version **2.1.0.0** of the RMS Protection module. To unprotect .eml files requires a minimum version of **2.2.0.0**.

**Breaking change in version 2.2.0.0**: If you are upgrading from a previous version of the RMS Protection module, version 2.2.0.0 introduces the new *InPlace* parameter, which overwrites the existing file if you do not specify an output folder. In previous versions, this was the default behavior. To retain the same behavior as before, you might need to add the *InPlace* parameter to commands and scripts.

>**Important**
>
>To use these cmdlets, you must have the following installed on your computer. The RMS Protection Tool does not check for all these prerequisites:
>
>- One of the client or server operating system versions listed on the [RMS Protection Tool download page](https://www.microsoft.com/en-us/download/details.aspx?id=47256), in the System Requirements section.
>
>- A minimum version of the Microsoft .NET Framework 4.5. This version of the Microsoft .NET Framework is included with the later operating systems but if the RMS Protection Tool installer detects that this minimum version is not installed, it will tell you so that you can [download](https://www.microsoft.com/download/details.aspx?id=30653) and install it, and then rerun the installation.
>
>- Windows PowerShell version 4.0, which might need to be installed on older operating systems. For more information, see [How to Install Windows PowerShell 4.0](http://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx). To confirm the version of Windows PowerShell that you are running, type **$PSVersionTable** in a Windows PowerShell session.
>
>- The Rights Management Client 2.1, which you can [install by itself](https://www.microsoft.com/en-us/download/details.aspx?id=38396), or install with the [Rights Management sharing application](https://www.microsoft.com/en-us/download/details.aspx?id=40857). The setup program does not check that this client is installed and if necessary, you can install it after you have installed the RMS Protection Tool.

Before you start to use these cmdlets, see the documentation that corresponds to your deployment of Rights Management for additional prerequisites and instructions:

- Azure RMS: [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/en-us/library/mt433202.aspx)

- AD RMS: [about_RMSProtection_ADRMS](https://msdn.microsoft.com/en-us/library/mt433203.aspx)

The .dll file for this module is *RMSProtection.dll*.

## RightsProtection Cmdlets
### [Clear-RMSAuthentication](./Clear-RMSAuthentication.md)
Clears credentials for a user who is authenticated to the Azure RMS service.


### [Get-RMSFileStatus](./Get-RMSFileStatus.md)
Gets the RMS protection status of a specified file.


### [Get-RMSServerAuthentication](./Get-RMSServerAuthentication.md)
Gets the status of your service principal authentication to Azure RMS.


### [Get-RMSServer](./Get-RMSServer.md)
Gets a list of RMS servers that can issue templates.


### [Get-RMSTemplate](./Get-RMSTemplate.md)
Gets a list of RMS templates.


### [New-RMSProtectionLicense](./New-RMSProtectionLicense.md)
Creates an ad-hoc rights policy for RMS protection.


### [Protect-RMSFile](./Protect-RMSFile.md)
Protects a specified file or the files in a specified folder by using RMS.


### [Set-RMSServerAuthentication](./Set-RMSServerAuthentication.md)
Sets the service principal authentication credentials for Azure RMS.


### [Unprotect-RMSFile](./Unprotect-RMSFile.md)
Unprotects a file that is currently protected by RMS.
