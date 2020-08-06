---
Module Name: AzureInformationProtection
Module Guid: NA
Download Help Link: NA
Help Version: NA
Locale: en-US
---

# AzureInformationProtection Module
## Description

The following lists links to documentation for the Microsoft Azure Information Protection (AIP) cmdlets. These cmdlets are installed with both the Azure Information Protection classic client and the Azure Information Protection unified labeling client. [Not sure of the differences between these two clients?](https://docs.microsoft.com/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)


|Client  |cmdlet descriptions  |
|---------|---------|
|**Classic client cmdlets**   | Classic client cmdlets enable you to protect and unprotect files, label files, and get information about files that are protected and labeled. </br></br>These cmdlets are installed with the [Azure Information Protection classic client](https://docs.microsoft.com/azure/information-protection/rms-client/aip-client) and are supported for:</br>- Azure Information Protection</br>The Azure Rights Management service for Azure Information Protection</br>- Active Directory Rights Management Services (AD RMS) </br></br>The current general availability version of the AzureInformationProtection module for this client is **1.54.59.0**. <!--You might have a later version if you have installed a preview version.--></br>For release details, see the [classic client version release history](https://docs.microsoft.com/azure/information-protection/rms-client/client-version-release-history).     |
|**Unified labeling cmdlets**     | Unified labeling cmdlets enable you to label files and get information about files that labeled. </br>These cmdlets are installed with the [Azure Information Protection unified labeling client](https://docs.microsoft.com/azure/information-protection/rms-client/aip-clientv2) and are supported for Azure Information Protection only. </br></br>The current general availability version of the AzureInformationProtection module for this client is **2.6.111.0**. You may have a later version if you've installed a preview version. For release details, see the [unified client version release history](https://docs.microsoft.com/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history). |

> [!TIP]
> Check the version that you have installed by running the following command: `(Get-Module AzureInformationProtection -ListAvailable).Version`.

For more information, see:

- [Using PowerShell with the Azure Information Protection classic client](https://docs.microsoft.com/azure/information-protection/rms-client/client-admin-guide-powershell)

- [Using PowerShell with the Azure Information Protection unified labeling client](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-powershell)


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

### [Export-AIPLogs](Export-AIPLogs.md)
Gathers and exports Azure Information Protection client and scanner log files to a compressed file.

Supported only by the preview version of the Azure Information Protection unified labeling client.

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

### [Install-MIPNetworkDiscovery](Install-AIPNetworkDiscovery.md)
Installs the Network Discovery service.

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

### [Start-AIPScannerDiagnostics](start-aipscannerdiagnostics.md)
Starts a series of health checks for a locally installed AIP scanner service.

### [Start-AIPScan](Start-AIPScan.md)
Instructs the Azure Information Protection scanner to start a one time scan cycle. 

### [Stop-AIPScan](stop-aipscan.md)
Instructs the Azure Information Protection scanner to immediately stop the currently running scan cycle.

### [Uninstall-AIPScanner](Uninstall-AIPScanner.md)
Uninstalls the Windows Server service for the Azure Information Protection scanner.

### [Unprotect-RMSFile](Unprotect-RMSFile.md)
Unprotects a file that is currently protected by RMS.

Not supported by the Azure Information Protection unified labeling client. Instead, use Set-AIPFileLabel

### [Update-AIPScanner](Update-AIPScanner.md)
Updates the database schema for the Azure Information Protection scanner.
