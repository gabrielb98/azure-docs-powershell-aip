---
Module Name: AzureInformationProtection
Module Guid: NA
Download Help Link: NA
Help Version: NA
Locale: en-US
ms.assetid: 35D99F89-BD73-457E-95C7-73857656FB59
---

# AzureInformationProtection Module
## Description
The following list contains links to the help topics for the Microsoft Azure Information Protection (AIP) cmdlets, which are installed with the [Azure Information Protection client](/information-protection/rms-client/aip-client). This PowerShell module replaces the RMS Protection Tool and the AD RMS Bulk Protection Tool. 

These cmdlets can be used with the Azure Information Protection service, the Azure Rights Management service (Azure RMS), and Active Directory Rights Management Services (AD RMS). 

The current general availability version of the AzureInformationProtection module is **1.10.56.0**. You might have a later version if you have installed a preview version. To check the version that you have installed, run the following command: `(Get-Module AzureInformationProtection -ListAvailable).Version`.

For instructions to use these cmdlets, any current limitations, prerequisites, and scenario examples, see the following documentation from the Azure Information Protection client administrator guide: 

- [Using PowerShell with the Azure Information Protection client](/information-protection/rms-client/client-admin-guide-powershell)


The .dll file for this module is *AIP.dll*.

## AzureInformationProtection cmdlets

### Add-AIPScannerRepository
Supported only for customers in the private preview program for the Azure Information Protection scanner.


### [Clear-AIPAuthentication](./Clear-AIPAuthentication.md )
Clears the authentication token and RMS templates for the current user.


### [Clear-RMSAuthentication](./Clear-RMSAuthentication.md)
Clears credentials for a user who is authenticated to the Azure RMS service.

### [Get-AIPFileStatus](./Get-AIPFileStatus.md)
Gets the Azure Information Protection label and protection information for a specified file or files.

### Get-AIPScannerConfiguration
Supported only for customers in the private preview program for the Azure Information Protection scanner.

### Get-AIPScannerRepository
Supported only for customers in the private preview program for the Azure Information Protection scanner.


### [Get-RMSFileStatus](./Get-RMSFileStatus.md)
Gets the RMS protection status of a specified file.


### [Get-RMSServerAuthentication](./Get-RMSServerAuthentication.md)
Gets the server mode status that is used for authentication to RMS.


### [Get-RMSServer](./Get-RMSServer.md)
Gets a list of RMS servers that can issue templates.


### [Get-RMSTemplate](./Get-RMSTemplate.md)
Gets a list of RMS templates.


## Install-AIPScanner
Supported only for customers in the private preview program for the Azure Information Protection scanner.


### [New-RMSProtectionLicense](./New-RMSProtectionLicense.md)
Creates an ad-hoc rights policy for RMS protection.


### [Protect-RMSFile](./Protect-RMSFile.md)
Protects a specified file or the files in a specified folder by using RMS.


## Remove-AIPScannerRepository
Supported only for customers in the private preview program for the Azure Information Protection scanner.


### [Set-AIPAuthentication](./Set-AIPAuthentication.md)
Sets the authentication credentials for the Azure Information Protection client.


### [Set-AIPFileClassification](./Set-AIPFileClassification)
Scans a file to automatically set an Azure Information Protection label for a file, according to conditions that are configured in the policy.


### [Set-AIPFileLabel](./Set-AIPFileLabel)
Sets or removes an Azure Information Protection label for a file, and sets the protection according to the label configuration.


### Set-AIPScanner
Supported only for customers in the private preview program for the Azure Information Protection scanner.


## Set-AIPScannerConfiguration
Supported only for customers in the private preview program for the Azure Information Protection scanner.


### [Set-RMSServerAuthentication](./Set-RMSServerAuthentication.md)
Sets the server mode, which is required for non-interactive sessions.


## Uninstall-AIPScanner
Supported only for customers in the private preview program for the Azure Information Protection scanner.


### [Unprotect-RMSFile](./Unprotect-RMSFile.md)
Unprotects a file that is currently protected by RMS.
