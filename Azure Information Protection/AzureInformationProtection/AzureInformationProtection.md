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

- **Installation:** The AzureInformationProtection module is installed with either the Azure Information Protection unified labeling or classic client. 

    To check the version you have installed, run: `(Get-Module AIPService -ListAvailable).Version` If this command or any cmdlet from this module fails to run, first run **Import-Module AIPService**.

- **.dll file:** The .dll file for this module is *AIP.dll*.

For more information, see:
    
|Client  |References  |
|---------|---------|
|**Unified labeling client**     | - [AIP unified labeling client](/azure/information-protection/rms-client/aip-clientv2) </br>- [Unified client version release history](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history) </br>- [Using PowerShell with the AIP unified labeling client](/azure/information-protection/rms-client/clientv2-admin-guide-powershell)        |
|**Classic client**     |  - [AIP classic client](/azure/information-protection/rms-client/aip-client) </br>- [Classic client version release history](/azure/information-protection/rms-client/client-version-release-history) </br>- [Using PowerShell with the AIP classic client](/azure/information-protection/rms-client/client-admin-guide-powershell) | 
| | |

> [!TIP]
> This docset indicates whenever information is relevant for only one of the clients. If no client is specified, the cmdlet or parameter is relevant for both clients. 
>
>Not sure of the differences between these two clients? See this [FAQ](/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client).
> 
> Check the version that you have installed by running the following command: `(Get-Module AzureInformationProtection -ListAvailable).Version`.

[!INCLUDE [The AIP classic client is sunset](../includes/classic-client-sunset.md)]

## AzureInformationProtection Cmdlets
### [Add-AIPScannerRepository](Add-AIPScannerRepository.md)
**Unified labeling client only:** Adds a repository to an Azure Information Protection content scan job.

### [Add-AIPScannerScannedFileTypes](Add-AIPScannerScannedFileTypes.md)
**Deprecated:** Adds new file types to a configured list of file types to scan or exclude from scanning by the Azure Information Protection scanner.

### [Add-MIPScannerRepository](Add-MIPScannerRepository.md)
**Unified labeling client only:** Adds a repository to an Azure Information Protection content scan job.


### [Clear-AIPAuthentication](Clear-AIPAuthentication.md)
Clears the user settings and RMS templates for the current user.

### [Clear-RMSAuthentication](Clear-RMSAuthentication.md)
**Classic client only:** Clears credentials for a user who is authenticated to the Azure RMS service.

### [Export-AIPLogs](Export-AIPLogs.md)
**Unified labeling client only:** Gathers and exports Azure Information Protection client and scanner log files to a compressed file.

### [Get-AIPFileStatus](Get-AIPFileStatus.md)
Gets the Azure Information Protection label and protection information for a specified file or files. 

### [Get-AIPScannerConfiguration](Get-AIPScannerConfiguration.md)
Gets the configuration settings for the Azure Information Protection scanner.

### [Get-AIPScannerContentScanJob](Get-AIPScannerContentScanJob.md)
Gets details about your content scan job.

Supported only by the AIP unified labeling client.

### [Get-AIPScannerRepository](Get-AIPScannerRepository.md)
**Unified labeling client only:** Gets repository data for an Azure Information Protection content scan job.

### [Get-AIPScannerStatus](Get-AIPScannerStatus.md)
Gets the current status of the service for the Azure Information Protection scanner.

### [Get-MIPNetworkDiscoveryConfiguration](Get-MIPNetworkDiscoveryConfiguration.md)
**Unified labeling client only:** Gets configuration settings for the Network Discovery service.

Supported only for the AIP unified labeling client.

### [Get-MIPNetworkDiscoveryJobs](Get-MIPNetworkDiscoveryJobs.md)
**Unified labeling client only:** Gets a list of Azure Information Protection network scan jobs configured in your tenant.

### [Get-MIPNetworkDiscoveryStatus](Get-MIPNetworkDiscoveryStatus.md)
**Unified labeling client only:** Gets the current status of the Network Discovery service.

### [Get-RMSFileStatus](Get-RMSFileStatus.md)
Gets the RMS protection status of a specified file.

### [Get-RMSServer](Get-RMSServer.md)
**Classic client only:** Gets a list of RMS servers that can issue templates.

### [Get-RMSServerAuthentication](Get-RMSServerAuthentication.md)
**Classic** client only: Gets the server mode status that is used for authentication to RMS.

### [Get-RMSTemplate](Get-RMSTemplate.md)
**Classic client only:** Gets a list of RMS templates.

For the unified labeling client, use **[Get-RMSFileStatus](Get-RMSFileStatus.md)** instead.

### [Import-AIPScannerConfiguration](Import-AIPScannerConfiguration)
Imports a local configuration for the Azure Information Protection scanner.

### [Import-MIPNetworkDiscoveryConfiguration](Import-MIPNetworkDiscoveryConfiguration.md)
**Unified labeling client only:** Imports a local configuration for Network Discovery network scan jobs.

### [Install-AIPScanner](Install-AIPScanner.md)
Installs the Azure Information Protection scanner.

### [Install-MIPNetworkDiscovery](Install-MIPNetworkDiscovery.md)
**Unified labeling client only:** Installs the Network Discovery service.

### [New-AIPCustomPermissions](New-AIPCustomPermissions.md)
**Unified labeling client only:** Creates an ad-hoc protection policy for custom permissions.

### [New-RMSProtectionLicense](New-RMSProtectionLicense.md)
**Classic client only:** Creates an ad-hoc protection policy for RMS protection.

For the unified labeling client, use **[New-AIPCustomPermissions](New-AIPCustomPermissions.md)** instead. 

### [Protect-RMSFile](Protect-RMSFile.md)
**Classic client only:** Protects a specified file or the files in a specified folder by using RMS.

For the unified labeling client, use **[Set-AIPFileLabel](Set-AIPFileLabel.md)** instead.

### [Remove-AIPScannerContentScanJob](Remove-AIPScannerContentScanJob.md)
Deletes the entire Azure Information Protection content scan job.

Supported only for the AIP unified labeling client.

### [Remove-AIPScannerRepository](Remove-AIPScannerRepository.md)
**Unified labeling client only:** Removes a repository from an Azure Information Protection content scan job.

### [Remove-AIPScannerScannedFileTypes](Remove-AIPScannerScannedFileTypes.md)
**Deprecated:** Removes file types from a configured list of file types to scan or exclude from scanning by the Azure Information Protection scanner.

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

### [Set-AIPScannerContentScanJob](Set-AIPScannerContentScanJob.md)
**Unified labeling client only:** Defines settings for an Azure Information Protection content scan job.

### [Set-AIPScannerRepository](Set-AIPScannerRepository.md)
**Unified labeling client only:** Updates an existing repository in an Azure Information Protection content scan job.

### [Set-AIPScannerScannedFileTypes](Set-AIPScannerScannedFileTypes.md)
**Deprecated:** Sets a list of file types to scan or exclude from scanning by the Azure Information Protection scanner.

### [Set-MIPNetworkDiscovery](Set-MIPNetworkDiscovery.md)
**Unified labeling client only:** Updates the installation settings for the Network Discovery service.

### [Set-MIPNetworkDiscoveryConfiguration](Set-MIPNetworkDiscoveryConfiguration.md)
**Unified labeling client only:** Sets optional configurations for the Network Discovery service.

### [Set-RMSServerAuthentication](Set-RMSServerAuthentication.md)
**Classic client only:** Sets the server mode, which is required for non-interactive sessions.

For the unified labeling client, use **[Set-AIPAuthentication](Set-AIPAuthentication.md)** instead.

### [Start-AIPScan](Start-AIPScan.md)
**Unified labeling client only:** Instructs the Azure Information Protection scanner to start a one time scan cycle. 

### [Start-AIPScannerDiagnostics](Start-AIPScannerDiagnostics.md)
**Unified labeling client only:** Starts a series of health checks for a locally installed AIP scanner service.

### [Start-MIPNetworkDiscovery](Start-MIPNetworkDiscovery.md)
**Unified labeling client only:** Instructs the Azure Information Protection scanner to start a network scan job.

### [Stop-AIPScan](Stop-AIPScan.md)
**Unified labeling client only:** Instructs the Azure Information Protection scanner to immediately stop the currently running scan cycle.

### [Uninstall-AIPScanner](Uninstall-AIPScanner.md)
Uninstalls the Windows Server service for the Azure Information Protection scanner.

### [Uninstall-MIPNetworkDiscovery](Uninstall-MIPNetworkDiscovery.md)
**Unified labeling client only:** Uninstalls the Network Discovery Windows server service.

### [Unprotect-RMSFile](Unprotect-RMSFile.md)
**Classic client only:** Unprotects a file that is currently protected by RMS.

For the unified labeling client, use **[Set-AIPFileLabel](Set-AIPFileLabel.md)** instead.

### [Update-AIPScanner](Update-AIPScanner.md)
Updates the database schema for the Azure Information Protection scanner.