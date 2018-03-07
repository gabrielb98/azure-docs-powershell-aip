---
Module Name: AADRM
Module Guid: XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
Download Help Link: N/A
Help Version: 2.12.0.0
Locale: en-US
ms.assetid: 0B91D740-D2BD-4D57-9E21-C582C9BE2CCA
---

# AADRM Module
## Description
This topic displays help topics for the cmdlets that administer the Azure Rights Management (Azure RMS) service for Azure Information Protection.

These PowerShell cmdlets let you administer the Azure Rights Management service from the command line. Although this enables automation, it also supports reliable and repeated processes to help reduce administrative overheads. In addition, advanced configurations and some operations require this PowerShell module.

For more information about when you must use these PowerShell cmdlets and to see groupings of cmdlets by administration tasks, see [Administering the Azure Rights Management service by Using Windows PowerShell](/information-protection/deploy-use/administer-powershell).

>**Tip**
>
>If you do not see the cmdlet or options that are documented, make sure that you have [installed the latest version of the module](/information-protection/deploy-use/install-powershell).
>
>The current version is **2.12.0.0**, with a minor increment version (2.12.1.0) available that supports the PowerShell Gallery. To check the version you have installed, run: `(Get-Module aadrm -ListAvailable).Version` If this command or any cmdlet from this module fails to run, first run **Import-Module AADRM**.


The .dll file for this module is *Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll*.

## AADRM cmdlets

### [Add-AadrmRoleBasedAdministrator](./Add-AadrmRoleBasedAdministrator.md)
Grants administrative rights to Rights Management.


### [Add-AadrmSuperUser](./Add-AadrmSuperUser.md)
Adds a super user to Rights Management.


### [Add-AadrmTemplate](./Add-AadrmTemplate.md)
Creates a Rights Management template.


### [Clear-AadrmDoNotTrackUserGroup](./Clear-AadrmDoNotTrackUserGroup.md)
Clears the group for the users who must not be tracked by Rights Management.


### [Clear-AadrmSuperUserGroup](./Clear-AadrmSuperUserGroup.md)
Removes the super user group for your organization.


### [Connect-AadrmService](./Connect-AadrmService.md)
Connects to Rights Management.


### [Convert-AadrmKeyToKeyVault](./Convert-AadrmKeyToKeyVault.md)
Changes the location of a legacy customer-managed key in Azure Rights Management with the location of a customer-managed key in Azure Key Vault.


### [Disable-AadrmDevicePlatform](./Disable-AadrmDevicePlatform.md)
Disables Rights Management support for device platforms.


### [Disable-AadrmDocumentTrackingFeature](./Disable-AadrmDocumentTrackingFeature.md)
Disables document tracking for Rights Management.


### [Disable-AadrmIPCv3Service](./Disable-AadrmIPCv3Service.md)
Disables the MSIPC v3 platform for Rights Management.


### [Disable-AadrmSuperUserFeature](./Disable-AadrmSuperUserFeature.md)
Disables the super user feature.


### [Disable-AadrmUsageLogFeature](./Disable-AadrmUsageLogFeature.md)
Disables the usage log for Rights Management.


### [Disable-Aadrm](./Disable-Aadrm.md)
Deactivates Rights Management.


### [Disconnect-AadrmService](./Disconnect-AadrmService.md)
Disconnects from Rights Management.


### [Enable-AadrmDevicePlatform](./Enable-AadrmDevicePlatform.md)
Enables Rights Management support for device platforms.


### [Enable-AadrmDocumentTrackingFeature](./Enable-AadrmDocumentTrackingFeature.md)
Enables document tracking for Rights Management.


### [Enable-AadrmIPCv3Service](./Enable-AadrmIPCv3Service.md)
Enables the MSIPC v3 platform for Rights Management.


### [Enable-AadrmSuperUserFeature](./Enable-AadrmSuperUserFeature.md)
Enables the super user feature for Rights Management.


### [Enable-AadrmUsageLogFeature](./Enable-AadrmUsageLogFeature.md)
Enables usage logging for Rights Management.


### [Enable-Aadrm](./Enable-Aadrm.md)
Activates Rights Management for your organization.


### [Export-AadrmTemplate](./Export-AadrmTemplate.md)
Exports the properties of a rights policy template to a file.


### [Get-AadrmAdminLog](./Get-AadrmAdminLog.md)
Generates logs for all Rights Management  administrative commands.


### [Get-AadrmConfiguration](./Get-AadrmConfiguration.md)
Gets the Rights Management configuration of your tenant.


### [Get-AadrmDevicePlatform](./Get-AadrmDevicePlatform.md)
Gets the device platforms in your organization that support Rights Management.


### [Get-AadrmDocumentTrackingFeature](./Get-AadrmDocumentTrackingFeature.md)
Indicates whether document tracking is enabled or disabled for Rights Management.


### [Get-AadrmDocumentLog](./Get-AadrmDocumentLog.md)
Generates content information logs for all documents associated with a specific user.


### [Get-AadrmDoNotTrackUserGroup](./Get-AadrmDoNotTrackUserGroup.md)
Gets the group for the users who must not be tracked by Rights Management.


### [Get-AadrmIPCv3Service](./Get-AadrmIPCv3Service.md)
Displays whether the MSIPC v3 service is enabled or disabled for Rights Management.


### [Get-AadrmKeys](./Get-AadrmKeys.md)
Lists all tenant keys associated with your Rights Management tenant.


### [Get-AadrmMaxUseLicenseValidityTime](./Get-AadrmMaxUseLicenseValidityTime.md)
Gets the maximum validity time for Rights Management use licenses.


### [Get-AadrmMigrationUrl](./Get-AadrmMigrationUrl.md)
Gets the migration URL for Rights Management.


### [Get-AadrmOnboardingControlPolicy](./Get-AadrmOnboardingControlPolicy.md)
Gets user on-boarding control policy for Rights Management.


### [Get-AadrmRoleBasedAdministrator](./Get-AadrmRoleBasedAdministrator.md)
Gets the role-based administrators for Rights Management.


### [Get-AadrmSuperUserFeature](./Get-AadrmSuperUserFeature.md)
Gets the status of the super user feature for Rights Management.


### [Get-AadrmSuperUserGroup](./Get-AadrmSuperUserGroup.md)
Gets the super user group for Rights Management.


### [Get-AadrmSuperUser](./Get-AadrmSuperUser.md)
Gets the super users for Rights Management.


### [Get-AadrmTemplateProperty](./Get-AadrmTemplateProperty.md)
Gets the properties of a Rights Management template.


### [Get-AadrmTemplate](./Get-AadrmTemplate.md)
Gets a list of Rights Management templates.


### [Get-AadrmTrackingLog](./Get-AadrmTrackingLog.md)
Generates tracking information logs for all documents associated with a specific user.


### [Get-AadrmUsageLogFeature](./Get-AadrmUsageLogFeature.md)
Deprecated: Gets the status of legacy usage logging for Rights Management.


### [Get-AadrmUsageLogLastCounterValue](./Get-AadrmUsageLogLastCounterValue.md)
Gets the last counter value for the usage log.


### [Get-AadrmUsageLogStorageAccount](./Get-AadrmUsageLogStorageAccount.md)
Gets the location for usage logs.


### [Get-AadrmUsageLog](./Get-AadrmUsageLog.md)
Downloads Rights Management logs to local storage.


### [Get-AadrmUserLog](./Get-AadrmUserLog.md)
Downloads Rights Management user logs to local storage.


### [Get-Aadrm](./Get-Aadrm.md)
Gets the activation status of Rights Management for your organization.


### [Import-AadrmTemplate](./Import-AadrmTemplate.md)
Creates a custom Rights Management policy template.


### [Import-AadrmTpd](./Import-AadrmTpd.md)
Imports a TPD from AD RMS for Rights Management.


### [New-AadrmRightsDefinition](./New-AadrmRightsDefinition.md)
Creates a Rights Definition object for Rights Management.


### [Remove-AadrmRoleBasedAdministrator](./Remove-AadrmRoleBasedAdministrator.md)
Removes administrative rights from Rights Management.


### [Remove-AadrmSuperUser](./Remove-AadrmSuperUser.md)
Removes a super user from Rights Management.


### [Remove-AadrmTemplate](./Remove-AadrmTemplate.md)
Deletes a Rights Management rights policy template.


### [Set-AadrmDoNotTrackUserGroup](./Set-AadrmDoNotTrackUserGroup.md)
Sets a group for the users who must not be tracked by Rights Management.


### [Set-AadrmKeyProperties](./Set-AadrmKeyProperties.md)
Updates the properties of a tenant key object for Rights Management.


### [Set-AadrmMaxUseLicenseValidityTime](./Set-AadrmMaxUseLicenseValidityTime.md)
Sets the maximum validity time for Rights Management use licenses.


### [Set-AadrmMigrationUrl](./Set-AadrmMigrationUrl.md)
Sets the migration URL for Rights Management.


### [Set-AadrmOnboardingControlPolicy](./Set-AadrmOnboardingControlPolicy.md)
Sets the user on-boarding control policy for Rights Management.


### [Set-AadrmSuperUserGroup](./Set-AadrmSuperUserGroup.md)
Sets the super user group for Rights Management.


### [Set-AadrmTemplateProperty](./Set-AadrmTemplateProperty.md)
Updates a property or properties of a Rights Management template.


### [Set-AadrmUsageLogStorageAccount](./Set-AadrmUsageLogStorageAccount.md)
Sets the location for Rights Management usage logs.


### [Use-AadrmKeyVaultKey](./Use-AadrmKeyVaultKey.md)
Tells Rights Management to use a customer-managed tenant key in Azure Key Vault.



