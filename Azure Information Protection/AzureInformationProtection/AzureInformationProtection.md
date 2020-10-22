---
Module Name: AzureInformationProtection
Module Guid: NA
Download Help Link: NA
Help Version: NA
Locale: en-US
---

# AzureInformationProtection Module
## Description

The following lists links to documentation for the Microsoft Azure Information Protection (AIP) cmdlets. 

- These cmdlets are installed with the AIP unified labeling client or the AIP classic client. 

- The .dll file for this module is *AIP.dll*.

> [!TIP]
Not sure of the differences between these two clients? See this [FAQ](/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client).
>
> Check the version that you have installed by running the following command: `(Get-Module AzureInformationProtection -ListAvailable).Version`.

### Unified labeling cmdlets

Unified labeling cmdlets enable you to label files and get information about files that labeled. 

These cmdlets are installed with the [AIP unified labeling client](/azure/information-protection/rms-client/aip-clientv2) and are supported for Azure Information Protection only. 

For more information, see: 
- [Unified client version release history](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)
- [Using PowerShell with the AIP unified labeling client](/azure/information-protection/rms-client/clientv2-admin-guide-powershell)

### Classic client cmdlets

> [!NOTE]
> To provide a unified and streamlined customer experience, the **Azure Information Protection classic client** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021.** 
> 
> This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).
>

Classic client cmdlets enable you to protect and unprotect files, label files, and get information about files that are protected and labeled. 

These cmdlets are installed with the [AIP classic client](/azure/information-protection/rms-client/aip-client) and are supported for:

- Azure Information Protection
- The Azure Rights Management service for Azure Information Protection
- Active Directory Rights Management Services (AD RMS)

For more information, see:

- [Classic client version release history](/azure/information-protection/rms-client/client-version-release-history).     
- [Using PowerShell with the AIP classic client](/azure/information-protection/rms-client/client-admin-guide-powershell)

## AzureInformationProtection Cmdlets
### [Add-AIPScannerRepository](Add-AIPScannerRepository.md)
Deprecated: Adds a data repository to be scanned by the Azure Information Protection scanner. 

### [Add-AIPScannerScannedFileTypes](Add-AIPScannerScannedFileTypes.md)
Deprecated: Adds new file types to a configured list of file types to scan or exclude from scanning by the Azure Information Protection scanner

### [Clear-AIPAuthentication](Clear-AIPAuthentication.md)
Classic client only: Clears the user settings and RMS templates for the current user.

### [Clear-RMSAuthentication](Clear-RMSAuthentication.md)
Classic client only: Clears credentials for a user who is authenticated to the Azure RMS service.

### [Export-AIPLogs](Export-AIPLogs.md)
Unified labeling client only: Gathers and exports Azure Information Protection client and scanner log files to a compressed file.

### [Get-AIPFileStatus](Get-AIPFileStatus.md)
Gets the Azure Information Protection label and protection information for a specified file or files. 

Relevant for both the unified labeling and classic clients.

### [Get-AIPScannerConfiguration](Get-AIPScannerConfiguration.md)
Gets the configuration settings for the Azure Information Protection scanner.

Relevant for both the unified labeling and classic clients.

### [Get-AIPScannerRepository](Get-AIPScannerRepository.md)
Deprecated: Gets a list of data repositories that the Azure Information Protection scanner is configured to scan.

### [Get-AIPScannerStatus](Get-AIPScannerStatus.md)
Gets the current status of the service for the Azure Information Protection scanner.

Relevant for both the unified labeling and classic clients.

### [Get-MIPNetworkDiscoveryConfiguration](Get-MIPNetworkDiscoveryConfiguration.md)
Unified labeling client only: Gets configuration settings for the Network Discovery service.

### [Get-MIPNetworkDiscoveryJobs](Get-MIPNetworkDiscoveryJobs.md)
Unified labeling client only: Gets a list of Azure Information Protection network scan jobs configured in your tenant.

### [Get-MIPNetworkDiscoveryStatus](Get-MIPNetworkDiscoveryStatus.md)
Unified labeling client only: Gets the current status of the Network Discovery service.

### [Get-RMSFileStatus](Get-RMSFileStatus.md)
Classic client only: Gets the RMS protection status of a specified file.

### [Get-RMSServer](Get-RMSServer.md)
Classic client only: Gets a list of RMS servers that can issue templates.

### [Get-RMSServerAuthentication](Get-RMSServerAuthentication.md)
Classic client only: Gets the server mode status that is used for authentication to RMS.

### [Get-RMSTemplate](Get-RMSTemplate.md)
Classic client only: Gets a list of RMS templates.

For the unified labeling client, use **Get-RMSFileStatus** instead.

### [Import-AIPScannerConfiguration](Import-AIPScannerConfiguration)
Imports a local configuration for the Azure Information Protection scanner.

Relevant for both the unified labeling and classic clients.

### [Import-MIPNetworkDiscoveryConfiguration](Import-MIPNetworkDiscoveryConfiguration.md)
Unified labeling client only: Imports a local configuration for Network Discovery network scan jobs.

### [Install-AIPScanner](Install-AIPScanner.md)
Unified labeling and classic clients: Installs the Azure Information Protection scanner.

### [Install-MIPNetworkDiscovery](Install-MIPNetworkDiscovery.md)
Unified labeling client only: Installs the Network Discovery service.

### [New-AIPCustomPermissions](New-AIPCustomPermissions.md)
Unified labeling client only: Creates an ad-hoc protection policy for custom permissions.

### [New-RMSProtectionLicense](New-RMSProtectionLicense.md)
Classic client only: Creates an ad-hoc protection policy for RMS protection.

For the unified labeling client, use **New-AIPCustomPermissions** instead. 

### [Protect-RMSFile](Protect-RMSFile.md)
Classic client only: Protects a specified file or the files in a specified folder by using RMS.

For the unified labeling client, use **Set-AIPFileLabel** instead.

### [Remove-AIPScannerRepository](Remove-AIPScannerRepository.md)
Deprecated: Removes a data repository for the Azure Information Protection scanner. 

### [Remove-AIPScannerScannedFileTypes](Remove-AIPScannerScannedFileTypes.md)
Deprecated: Removes file types from a configured list of file types to scan or exclude from scanning by the Azure Information Protection scanner.

### [Set-AIPAuthentication](Set-AIPAuthentication.md)
Sets the authentication credentials for the Azure Information Protection client.

Relevant for both the unified labeling and classic clients.

### [Set-AIPFileClassification](Set-AIPFileClassification.md)
Scans a file to automatically set an Azure Information Protection label for a file, according to conditions that are configured in the policy.

Relevant for both the unified labeling and classic clients.

### [Set-AIPFileLabel](Set-AIPFileLabel.md)
Sets or removes an Azure Information Protection label for a file, and sets or removes the protection according to the label configuration or custom permissions.

Relevant for both the unified labeling and classic clients.

### [Set-AIPScanner](Set-AIPScanner.md)
Sets the service account and database for the Azure Information Protection scanner.

Relevant for both the unified labeling and classic clients.

### [Set-AIPScannerConfiguration](Set-AIPScannerConfiguration.md)
Sets optional configuration for the Azure Information Protection scanner.

Relevant for both the unified labeling and classic clients.

### [Set-AIPScannerRepository](Set-AIPScannerRepository.md)
Deprecated: Updates a profile of configuration settings for a data repository to be scanned by the Azure Information Protection scanner. 

### [Set-AIPScannerScannedFileTypes](Set-AIPScannerScannedFileTypes.md)
Deprecated: Sets a list of file types to scan or exclude from scanning by the Azure Information Protection scanner.

### [Set-MIPNetworkDiscoveryConfiguration](Set-MIPNetworkDiscoveryConfiguration.md)
Unified labeling client only: Sets optional configurations for the Network Discovery service.

### [Set-RMSServerAuthentication](Set-RMSServerAuthentication.md)
Classic client only: Sets the server mode, which is required for non-interactive sessions.

For the unified labeling client, use **Set-AIPAuthentication** instead.

### [Start-AIPScan](Start-AIPScan.md)
Unified labeling client only: Instructs the Azure Information Protection scanner to start a one time scan cycle. 

### [Start-AIPScannerDiagnostics](Start-AIPScannerDiagnostics.md)
Unified labeling client only: Starts a series of health checks for a locally installed AIP scanner service.

### [Start-MIPNetworkDiscovery](Start-MIPNetworkDiscovery.md)
Unified labeling client only: Instructs the Azure Information Protection scanner to start a network scan job.

### [Stop-AIPScan](Stop-AIPScan.md)
Unified labeling client only: Instructs the Azure Information Protection scanner to immediately stop the currently running scan cycle.

### [Uninstall-AIPScanner](Uninstall-AIPScanner.md)
Unified labeling and classic clients: Uninstalls the Windows Server service for the Azure Information Protection scanner.

### [Uninstall-MIPNetworkDiscovery](Uninstall-MIPNetworkDiscovery.md)
Unified labeling client only: Uninstalls the Network Discovery Windows server service.

### [Unprotect-RMSFile](Unprotect-RMSFile.md)
Classic client only: Unprotects a file that is currently protected by RMS.

For the unified labeling client, use **Set-AIPFileLabel** instead.

### [Update-AIPScanner](Update-AIPScanner.md)
Updates the database schema for the Azure Information Protection scanner.

Relevant for both the unified labeling and classic clients.
