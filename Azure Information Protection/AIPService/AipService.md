---
Module Name: AIPService
Module Guid: XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
Download Help Link: N/A
Help Version: 2.13.0.0
Locale: en-US
ms.assetid: 0B91D740-D2BD-4D57-9E21-C582C9BE2CCA
---

# AIPService Module
## Description
This page displays help links for the cmdlets that administer the protection service from Azure Information Protection.

These PowerShell cmdlets let you administer Azure Information Protection from the command line. Although this enables automation, it also supports reliable and repeated processes to help reduce administrative overheads. In addition, advanced configurations and some operations require this PowerShell module.

For more information about when you must use these PowerShell cmdlets and to see groupings of cmdlets by administration tasks, see [Administering the protection service from Azure Information Protection by using PowerShell](/information-protection/deploy-use/administer-powershell).

>**Tip**
>
>If you do not see the cmdlet or options that are documented, make sure that you have [installed the latest version of the module](/information-protection/deploy-use/install-powershell).
>
>The current version is **1.0.0.0**. To check the version you have installed, run: `(Get-Module aadrm -ListAvailable).Version` If this command or any cmdlet from this module fails to run, first run **Import-Module AIPService**.


The .dll file for this module is *AIPService.dll*.

## AIPService cmdlets

### [Add-AipServiceRoleBasedAdministrator](./Add-AipServiceRoleBasedAdministrator.md)
Grants administrative rights to Azure Information Protection.


### [Add-AipServiceSuperUser](./Add-AipServiceSuperUser.md)
Adds a super user to Azure Information Protection.


### [Add-AipServiceTemplate](./Add-AipServiceTemplate.md)
Creates a protection template for Azure Information Protection.


### [Clear-AipServiceDoNotTrackUserGroup](./Clear-AipServiceDoNotTrackUserGroup.md)
Clears the group for the users who must not be tracked by Azure Information Protection.


### [Clear-AipServiceSuperUserGroup](./Clear-AipServiceSuperUserGroup.md)
Removes the super user group for Azure Information Protection.


### [Connect-AipService](./Connect-AipService.md)
Connects to Azure Information Protection.


### [Convert-AipServiceKeyToKeyVault](./Convert-AipServiceKeyToKeyVault.md)
Changes the location of a legacy customer-managed key in Azure Information Protection with the location of a customer-managed key in Azure Key Vault.


### [Disable-AipServiceDevicePlatform](./Disable-AipServiceDevicePlatform.md)
Disables protection support from Azure Information Protection for device platforms.


### [Disable-AipServiceDocumentTrackingFeature](./Disable-AipServiceDocumentTrackingFeature.md)
Disables document tracking for Azure Information Protection.


### [Disable-AipServiceIPCv3](./Disable-AipServiceIPCv3.md)
Disables the MSIPC v3 platform for Azure Information Protection.


### [Disable-AipServiceSuperUserFeature](./Disable-AipServiceSuperUserFeature.md)
Disables the super user feature for Azure Information Protection.


### [Disable-AipServiceUsageLogFeature](./Disable-AipServiceUsageLogFeature.md)
Disables the protection usage log for Azure Information Protection.


### [Disable-AipService](./Disable-AipService.md)
Deactivates the protection service from Azure Information Protection.


### [Disconnect-AipService](./Disconnect-AipService.md)
Disconnects from Azure Information Protection.


### [Enable-AipServiceDevicePlatform](./Enable-AipServiceDevicePlatform.md)
Enables protection support from Azure Information Protection for device platforms.


### [Enable-AipServiceDocumentTrackingFeature](./Enable-AipServiceDocumentTrackingFeature.md)
Enables document tracking for Azure Information Protection.


### [Enable-AipServiceIPCv3](./Enable-AipServiceIPCv3.md)
Enables the MSIPC v3 platform for Azure Information Protection.


### [Enable-AipServiceSuperUserFeature](./Enable-AipServiceSuperUserFeature.md)
Enables the super user feature for Azure Information Protection.


### [Enable-AipServiceUsageLogFeature](./Enable-AipServiceUsageLogFeature.md)
Enables protection usage logging for Azure Information Protection.


### [Enable-AipService](./Enable-AipService.md)
Activates the protection service for Azure Information Protection.


### [Export-AipServiceTemplate](./Export-AipServiceTemplate.md)
Exports the properties of a protection template from Azure Information Protection to a file.


### [Get-AipServiceAdminLog](./Get-AipServiceAdminLog.md)
Generates logs for all protection commands for Azure Information Protection.


### [Get-AipServiceConfiguration](./Get-AipServiceConfiguration.md)
Gets the Azure Information Protection configuration of your tenant.


### [Get-AipServiceDevicePlatform](./Get-AipServiceDevicePlatform.md)
Gets the device platforms in your organization that support the protection service from Azure Information Protection.


### [Get-AipServiceDocumentTrackingFeature](./Get-AipServiceDocumentTrackingFeature.md)
Indicates whether document tracking is enabled or disabled for Azure Information Protection.


### [Get-AipServiceDocumentLog](./Get-AipServiceDocumentLog.md)
Gets protection information about documents that are tracked by Azure Information Protection.


### [Get-AipServiceDoNotTrackUserGroup](./Get-AipServiceDoNotTrackUserGroup.md)
Gets the group for the users who must not be tracked by Azure Information Protection.


### [Get-AipServiceIPCv3](./Get-AipServiceIPCv3.md)
Displays whether the MSIPC v3 service is enabled or disabled for Azure Information Protection.


### [Get-AipServiceKeys](./Get-AipServiceKeys.md)
Lists all Azure Information Protection tenant keys associated with your tenant.


### [Get-AipServiceMaxUseLicenseValidityTime](./Get-AipServiceMaxUseLicenseValidityTime.md)
Gets the maximum validity time for Rights Management use licenses for Azure Information Protection.


### [Get-AipServiceMigrationUrl](./Get-AipServiceMigrationUrl.md)
Gets the migration URL for Azure Information Protection.


### [Get-AipServiceOnboardingControlPolicy](./Get-AipServiceOnboardingControlPolicy.md)
Gets the user on-boarding control policy for Azure Information Protection.


### [Get-AipServiceRoleBasedAdministrator](./Get-AipServiceRoleBasedAdministrator.md)
Gets the role-based administrators for Azure Information Protection.


### [Get-AipServiceSuperUserFeature](./Get-AipServiceSuperUserFeature.md)
Gets the status of the super user feature for Azure Information Protection.


### [Get-AipServiceSuperUserGroup](./Get-AipServiceSuperUserGroup.md)
Gets the super user group for Azure Information Protection.


### [Get-AipServiceSuperUser](./Get-AipServiceSuperUser.md)
Gets the super users for Azure Information Protection.


### [Get-AipServiceTemplateProperty](./Get-AipServiceTemplateProperty.md)
Gets the properties of a protection template for Azure Information Protection.


### [Get-AipServiceTemplate](./Get-AipServiceTemplate.md)
Gets a list of protection templates for Azure Information Protection.


### [Get-AipServiceTrackingLog](./Get-AipServiceTrackingLog.md)
Gets tracking information for documents protected by Azure Information Protection.


### [Get-AipServiceUsageLogFeature](./Get-AipServiceUsageLogFeature.md)
Deprecated: Gets the status of legacy protection usage logging for Azure Information Protection.


### [Get-AipServiceUsageLogLastCounterValue](./Get-AipServiceUsageLogLastCounterValue.md)
Gets the last counter value for the protection usage log for Azure Information Protection.


### [Get-AipServiceUsageLogStorageAccount](./Get-AipServiceUsageLogStorageAccount.md)
Gets the location for protection usage logs for Azure Information Protection.


### [Get-AipServiceUsageLog](./Get-AipServiceUsageLog.md)
Downloads protection logs from Azure Information Protection to local storage.


### [Get-AipServiceUserLog](./Get-AipServiceUserLog.md)
Downloads protection user logs from Azure Information Protection to local storage.


### [Get-AipService](./Get-AipService.md)
Gets the activation status of the protection service from Azure Information Protection.


### [Import-AipServiceTemplate](./Import-AipServiceTemplate.md)
Creates a custom protection template for Azure Information Protection.


### [Import-AipServiceTpd](./Import-AipServiceTpd.md)
Imports a TPD from AD RMS for Azure Information Protection.


### [New-AipServiceRightsDefinition](./New-AipServiceRightsDefinition.md)
Creates a rights definition object for a protection template for Azure Information Protection.


### [Remove-AipServiceRoleBasedAdministrator](./Remove-AipServiceRoleBasedAdministrator.md)
Removes administrative rights from Azure Information Protection.


### [Remove-AipServiceSuperUser](./Remove-AipServiceSuperUser.md)
Removes a super user from Azure Information Protection.


### [Remove-AipServiceTemplate](./Remove-AipServiceTemplate.md)
Deletes a protection template for Azure Information Protection.


### [Set-AipServiceDoNotTrackUserGroup](./Set-AipServiceDoNotTrackUserGroup.md)
Sets a group for the users who must not be tracked by Azure Information Protection.


### [Set-AipServiceKeyProperties](./Set-AipServiceKeyProperties.md)
Updates the properties of a tenant key object for Azure Information Protection.


### [Set-AipServiceMaxUseLicenseValidityTime](./Set-AipServiceMaxUseLicenseValidityTime.md)
Sets the maximum validity time for Rights Management use licenses for Azure Information Protection.


### [Set-AipServiceMigrationUrl](./Set-AipServiceMigrationUrl.md)
Sets the migration URL for Information Protection service.


### [Set-AipServiceOnboardingControlPolicy](./Set-AipServiceOnboardingControlPolicy.md)
Sets the user on-boarding control policy for Azure Information Protection.


### [Set-AipServiceSuperUserGroup](./Set-AipServiceSuperUserGroup.md)
Sets the super user group for Azure Information Protection.


### [Set-AipServiceTemplateProperty](./Set-AipServiceTemplateProperty.md)
Updates a property or properties of a protection template for Azure Information Protection.


### [Set-AipServiceUsageLogStorageAccount](./Set-AipServiceUsageLogStorageAccount.md)
Sets the location for protection usage logs for Azure Information Protection.


### [Use-AipServiceKeyVaultKey](./Use-AipServiceKeyVaultKey.md)
Tells Azure Information Protection to use a customer-managed tenant key in Azure Key Vault.

