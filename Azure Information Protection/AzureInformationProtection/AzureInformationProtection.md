---
Module Name: AzureInformationProtection
Module Guid: NA
Download Help Link: NA
Help Version: NA
Locale: en-US
---

# AzureInformationProtection Module
## Description

The following list contains links to the help for the Microsoft Azure Information Protection (AIP) cmdlets, which are installed with the Azure Information Protection client and the Azure Information Protection unified labeling client. [Not sure of the differences between these two clients?](https://docs.microsoft.com/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)

- **For the Azure Information Protection client**: The cmdlets let you protect and unprotect files, label files, and get information about files that are protected and labeled. These cmdlets are installed with the [Azure Information Protection client](/information-protection/rms-client/aip-client) and can be used with Azure Information Protection, the protection service (Azure Rights Management) for Azure Information Protection, and Active Directory Rights Management Services (AD RMS).
    
    The current general availability version of the AzureInformationProtection module for this client is **1.53.10.0**. You might have a later version if you have installed a preview version. For release details, see the [client version release history](/information-protection/rms-client/client-version-release-history).
     

- **For the Azure Information Protection unified labeling client**: The cmdlets let you label files and get information about files that are labeled. These cmdlets are installed with the [Azure Information Protection unified labeling client](/information-protection/rms-client/aip-clientv2) and can be used with Azure Information Protection only.
    
    The current general availability version of the AzureInformationProtection module for this client is **2.2.14.0**. You might have a later version if you have installed a preview version. For release details, see the [unified client version release history](/information-protection/rms-client/unifiedlabelingclient-version-release-history). 

To check the version that you have installed, run the following command: `(Get-Module AzureInformationProtection -ListAvailable).Version`.

For instructions to use these cmdlets, any current limitations, prerequisites, and scenario examples, see the following documentation from the administrator guides:

- The Azure Information Protection client:
    - [Using PowerShell with the Azure Information Protection client](/information-protection/rms-client/client-admin-guide-powershell)

- The Azure Information Protection unified labeling client:
    - [Using PowerShell with the Azure Information Protection unified labeling client](/information-protection/rms-client/clientv2-admin-guide-powershell)


The .dll file for this module is *AIP.dll*.

## AzureInformationProtection Cmdlets
### [Add-AIPScannerRepository](Add-AIPScannerRepository.md)
Deprecated: Adds a data repository to be scanned by the Azure Information Protection scanner. 

### [Add-AIPScannerScannedFileTypes](Add-AIPScannerScannedFileTypes.md)
Deprecated: Adds new file types to a configured list of file types to scan or exclude from scanning by the Azure Information Protection scanner

### [Clear-AIPAuthentication](Clear-AIPAuthentication.md)
Clears the user settings and RMS templates for the current user.

Not supported by the Azure Information Protection unified labeling client.

### [Clear-RMSAuthentication](Clear-RMSAuthentication.md)
Clears credentials for a user who is authenticated to the Azure RMS service.

Not supported by the Azure Information Protection unified labeling client.

### [Get-AIPFileStatus](Get-AIPFileStatus.md)
Gets the Azure Information Protection label and protection information for a specified file or files.

### [Get-AIPScannerConfiguration](Get-AIPScannerConfiguration.md)
Gets the configuration settings for the Azure Information Protection scanner.

### [Get-AIPScannerRepository](Get-AIPScannerRepository.md)
Deprecated: Gets a list of data repositories that the Azure Information Protection scanner is configured to scan.

### [Get-AIPScannerStatus](Get-AIPScannerStatus.md)
Gets the current status of the service for the Azure Information Protection scanner.

### [Get-RMSFileStatus](Get-RMSFileStatus.md)
Gets the RMS protection status of a specified file.

Not supported by the Azure Information Protection unified labeling client.

### [Get-RMSServer](Get-RMSServer.md)
Gets a list of RMS servers that can issue templates.

Not supported by the Azure Information Protection unified labeling client.

### [Get-RMSServerAuthentication](Get-RMSServerAuthentication.md)
Gets the server mode status that is used for authentication to RMS.

Not supported by the Azure Information Protection unified labeling client. 

### [Get-RMSTemplate](Get-RMSTemplate.md)
Gets a list of RMS templates.

Not supported by the Azure Information Protection unified labeling client. Instead, use Get-RMSFileStatus.

### [Install-AIPScanner](Install-AIPScanner.md)
Installs the Azure Information Protection scanner.

### [New-AIPCustomPermissions](New-AIPCustomPermissions.md)
Creates an ad-hoc protection policy for custom permissions.

Supported only by the Azure Information Protection unified labeling client.

### [New-RMSProtectionLicense](New-RMSProtectionLicense.md)
Creates an ad-hoc protection policy for RMS protection.

Not supported by the Azure Information Protection unified labeling client. Instead, use New-AIPCustomPermissions.

### [Protect-RMSFile](Protect-RMSFile.md)
Protects a specified file or the files in a specified folder by using RMS.

Not supported by the Azure Information Protection unified labeling client. Instead, use Set-AIPFileLabel.

### [Remove-AIPScannerRepository](Remove-AIPScannerRepository.md)
Deprecated: Removes a data repository for the Azure Information Protection scanner. 

### [Remove-AIPScannerScannedFileTypes](Remove-AIPScannerScannedFileTypes.md)
Deprecated: Removes file types from a configured list of file types to scan or exclude from scanning by the Azure Information Protection scanner.

### [Set-AIPAuthentication](Set-AIPAuthentication.md)
Sets the authentication credentials for the Azure Information Protection client.

### [Set-AIPFileClassification](Set-AIPFileClassification.md)
Scans a file to automatically set an Azure Information Protection label for a file, according to conditions that are configured in the policy.

### [Set-AIPFileLabel](Set-AIPFileLabel.md)
Sets or removes an Azure Information Protection label for a file, and sets or removes the protection according to the label configuration or custom permissions.

### [Set-AIPScanner](Set-AIPScanner.md)
Sets the service account and database for the Azure Information Protection scanner.

### [Set-AIPScannerConfiguration](Set-AIPScannerConfiguration.md)
Sets optional configuration for the Azure Information Protection scanner.

### [Set-AIPScannerRepository](Set-AIPScannerRepository.md)
Deprecated: Updates a profile of configuration settings for a data repository to be scanned by the Azure Information Protection scanner. 

### [Set-AIPScannerScannedFileTypes](Set-AIPScannerScannedFileTypes.md)
Deprecated: Sets a list of file types to scan or exclude from scanning by the Azure Information Protection scanner.

### [Set-RMSServerAuthentication](Set-RMSServerAuthentication.md)
Sets the server mode, which is required for non-interactive sessions.

Not supported by the Azure Information Protection unified labeling client. Instead, use Set-AIPAuthentication.

### [Start-AIPScan](Start-AIPScan.md)
Instructs the Azure Information Protection scanner to start a one time scan cycle. 

### [Uninstall-AIPScanner](Uninstall-AIPScanner.md)
Uninstalls the Windows Server service for the Azure Information Protection scanner.

### [Unprotect-RMSFile](Unprotect-RMSFile.md)
Unprotects a file that is currently protected by RMS.

Not supported by the Azure Information Protection unified labeling client. Instead, use Set-AIPFileLabel

### [Update-AIPScanner](Update-AIPScanner.md)
Updates the database schema for the Azure Information Protection scanner.
