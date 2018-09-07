---
Module Name: AADRM
Module Guid: XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
Download Help Link: N/A
Help Version: 2.13.0.0
Locale: en-US
ms.assetid: 0B91D740-D2BD-4D57-9E21-C582C9BE2CCA
---

# AADRM Module
## Description
This topic displays help topics for the cmdlets that administer the Azure Information Protection service (AIP Service) service for Azure Information Protection.

These PowerShell cmdlets let you administer the Azure Information Protection service from the command line. Although this enables automation, it also supports reliable and repeated processes to help reduce administrative overheads. In addition, advanced configurations and some operations require this PowerShell module.

For more information about when you must use these PowerShell cmdlets and to see groupings of cmdlets by administration tasks, see [Administering the Azure Information Protection service by Using Windows PowerShell](/information-protection/deploy-use/administer-powershell).

>**Tip**
>
>If you do not see the cmdlet or options that are documented, make sure that you have [installed the latest version of the module](/information-protection/deploy-use/install-powershell).
>
>The current version is **2.13.1.0**. To check the version you have installed, run: `(Get-Module aadrm -ListAvailable).Version` If this command or any cmdlet from this module fails to run, first run **Import-Module AADRM**.


The .dll file for this module is *Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll*.

## AADRM cmdlets

### [Add-AipServiceRoleBasedAdministrator](./Add-AipServiceRoleBasedAdministrator.md)
Grants administrative rights to Information Protection service.


### [Add-AipServiceSuperUser](./Add-AipServiceSuperUser.md)
Adds a super user to Information Protection service.


### [Add-AipServiceTemplate](./Add-AipServiceTemplate.md)
Creates an Information Protection service template.


### [Clear-AipServiceDoNotTrackUserGroup](./Clear-AipServiceDoNotTrackUserGroup.md)
Clears the group for the users who must not be tracked by Information Protection service.


### [Clear-AipServiceSuperUserGroup](./Clear-AipServiceSuperUserGroup.md)
Removes the super user group for your organization.


### [Connect-AipService](./Connect-AipService.md)
Connects to Information Protection service.


### [Convert-AipServiceKeyToKeyVault](./Convert-AipServiceKeyToKeyVault.md)
Changes the location of a legacy customer-managed key in Azure Information Protection service with the location of a customer-managed key in Azure Key Vault.


### [Disable-AipServiceDevicePlatform](./Disable-AipServiceDevicePlatform.md)
Disables Information Protection service support for device platforms.


### [Disable-AipServiceDocumentTrackingFeature](./Disable-AipServiceDocumentTrackingFeature.md)
Disables document tracking for Information Protection service.


### [Disable-AipServiceIPCv3](./Disable-AipServiceIPCv3.md)
Disables the MSIPC v3 platform for Information Protection service.


### [Disable-AipServiceSuperUserFeature](./Disable-AipServiceSuperUserFeature.md)
Disables the super user feature.


### [Disable-AipServiceUsageLogFeature](./Disable-AipServiceUsageLogFeature.md)
Disables the usage log for Information Protection service.


### [Disable-AipService](./Disable-AipService.md)
Deactivates Information Protection service.


### [Disconnect-AipService](./Disconnect-AipService.md)
Disconnects from Information Protection service.


### [Enable-AipServiceDevicePlatform](./Enable-AipServiceDevicePlatform.md)
Enables Information Protection service support for device platforms.


### [Enable-AipServiceDocumentTrackingFeature](./Enable-AipServiceDocumentTrackingFeature.md)
Enables document tracking for Information Protection service.


### [Enable-AipServiceIPCv3](./Enable-AipServiceIPCv3.md)
Enables the MSIPC v3 platform for Information Protection service.


### [Enable-AipServiceSuperUserFeature](./Enable-AipServiceSuperUserFeature.md)
Enables the super user feature for Information Protection service.


### [Enable-AipServiceUsageLogFeature](./Enable-AipServiceUsageLogFeature.md)
Enables usage logging for Information Protection service.


### [Enable-AipService](./Enable-AipService.md)
Activates Information Protection service for your organization.


### [Export-AipServiceTemplate](./Export-AipServiceTemplate.md)
Exports the properties of a rights policy template to a file.


### [Get-AipServiceAdminLog](./Get-AipServiceAdminLog.md)
Generates logs for all Information Protection service administrative commands.


### [Get-AipServiceConfiguration](./Get-AipServiceConfiguration.md)
Gets the Information Protection service configuration of your tenant.


### [Get-AipServiceDevicePlatform](./Get-AipServiceDevicePlatform.md)
Gets the device platforms in your organization that support Information Protection service.


### [Get-AipServiceDocumentTrackingFeature](./Get-AipServiceDocumentTrackingFeature.md)
Indicates whether document tracking is enabled or disabled for Information Protection service.


### [Get-AipServiceDocumentLog](./Get-AipServiceDocumentLog.md)
Gets protection information about documents that are tracked.


### [Get-AipServiceDoNotTrackUserGroup](./Get-AipServiceDoNotTrackUserGroup.md)
Gets the group for the users who must not be tracked by Information Protection service.


### [Get-AipServiceIPCv3](./Get-AipServiceIPCv3.md)
Displays whether the MSIPC v3 service is enabled or disabled for Information Protection service.


### [Get-AipServiceKeys](./Get-AipServiceKeys.md)
Lists all tenant keys associated with your Information Protection service tenant.


### [Get-AipServiceMaxUseLicenseValidityTime](./Get-AipServiceMaxUseLicenseValidityTime.md)
Gets the maximum validity time for Information Protection service use licenses.


### [Get-AipServiceMigrationUrl](./Get-AipServiceMigrationUrl.md)
Gets the migration URL for Information Protection service.


### [Get-AipServiceOnboardingControlPolicy](./Get-AipServiceOnboardingControlPolicy.md)
Gets user on-boarding control policy for Information Protection service.


### [Get-AipServiceRoleBasedAdministrator](./Get-AipServiceRoleBasedAdministrator.md)
Gets the role-based administrators for Information Protection service.


### [Get-AipServiceSuperUserFeature](./Get-AipServiceSuperUserFeature.md)
Gets the status of the super user feature for Information Protection service.


### [Get-AipServiceSuperUserGroup](./Get-AipServiceSuperUserGroup.md)
Gets the super user group for Information Protection service.


### [Get-AipServiceSuperUser](./Get-AipServiceSuperUser.md)
Gets the super users for Information Protection service.


### [Get-AipServiceTemplateProperty](./Get-AipServiceTemplateProperty.md)
Gets the properties of an Information Protection service template.


### [Get-AipServiceTemplate](./Get-AipServiceTemplate.md)
Gets a list of Information Protection service templates.


### [Get-AipServiceTrackingLog](./Get-AipServiceTrackingLog.md)
Gets tracking information for protected documents.


### [Get-AipServiceUsageLogFeature](./Get-AipServiceUsageLogFeature.md)
Deprecated: Gets the status of legacy usage logging for Information Protection service.


### [Get-AipServiceUsageLogLastCounterValue](./Get-AipServiceUsageLogLastCounterValue.md)
Gets the last counter value for the usage log.


### [Get-AipServiceUsageLogStorageAccount](./Get-AipServiceUsageLogStorageAccount.md)
Gets the location for usage logs.


### [Get-AipServiceUsageLog](./Get-AipServiceUsageLog.md)
Downloads Information Protection service logs to local storage.


### [Get-AipServiceUserLog](./Get-AipServiceUserLog.md)
Downloads Information Protection service user logs to local storage.


### [Get-AipService](./Get-AipService.md)
Gets the activation status of Information Protection service for your organization.


### [Import-AipServiceTemplate](./Import-AipServiceTemplate.md)
Creates a custom Information Protection service policy template.


### [Import-AipServiceTpd](./Import-AipServiceTpd.md)
Imports a TPD from AIP Service for Information Protection service.


### [New-AipServiceRightsDefinition](./New-AipServiceRightsDefinition.md)
Creates a Rights Definition object for Information Protection service.


### [Remove-AipServiceRoleBasedAdministrator](./Remove-AipServiceRoleBasedAdministrator.md)
Removes administrative rights from Information Protection service.


### [Remove-AipServiceSuperUser](./Remove-AipServiceSuperUser.md)
Removes a super user from Information Protection service.


### [Remove-AipServiceTemplate](./Remove-AipServiceTemplate.md)
Deletes an Information Protection service rights policy template.


### [Set-AipServiceDoNotTrackUserGroup](./Set-AipServiceDoNotTrackUserGroup.md)
Sets a group for the users who must not be tracked by Information Protection service.


### [Set-AipServiceKeyProperties](./Set-AipServiceKeyProperties.md)
Updates the properties of a tenant key object for Information Protection service.


### [Set-AipServiceMaxUseLicenseValidityTime](./Set-AipServiceMaxUseLicenseValidityTime.md)
Sets the maximum validity time for Information Protection service use licenses.


### [Set-AipServiceMigrationUrl](./Set-AipServiceMigrationUrl.md)
Sets the migration URL for Information Protection service.


### [Set-AipServiceOnboardingControlPolicy](./Set-AipServiceOnboardingControlPolicy.md)
Sets the user on-boarding control policy for Information Protection service.


### [Set-AipServiceSuperUserGroup](./Set-AipServiceSuperUserGroup.md)
Sets the super user group for Information Protection service.


### [Set-AipServiceTemplateProperty](./Set-AipServiceTemplateProperty.md)
Updates a property or properties of an Information Protection service template.


### [Set-AipServiceUsageLogStorageAccount](./Set-AipServiceUsageLogStorageAccount.md)
Sets the location for Information Protection service usage logs.


### [Use-AipServiceKeyVaultKey](./Use-AipServiceKeyVaultKey.md)
Tells Information Protection service to use a customer-managed tenant key in Azure Key Vault.



