---
Module Name: AIPService
Module Guid: XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
Download Help Link: N/A
Help Version: 1.0.0.1
Locale: en-US
---

# AIPService Module
## Description

This page displays help links for the cmdlets that administer the protection service from Azure Information Protection. 

> [!NOTE]
> This module replaces the older module, **AADRM**. Support for the AADRM module ends July 15, 2020.

These PowerShell cmdlets let you administer Azure Information Protection from the command line. Although this administration method enables automation, it also supports reliable and repeated processes to help reduce administrative overheads. In addition, advanced configurations and some operations require this PowerShell module.

For more information about when you must use PowerShell cmdlets and to see groupings of cmdlets by administration tasks, see [Administering the protection service from Azure Information Protection by using PowerShell](/information-protection/deploy-use/administer-powershell).

- **Current version:** The current version of this module is **1.0.0.4**. 

    To check the version you have installed, run: `(Get-Module AIPService -ListAvailable).Version` If this command or any cmdlet from this module fails to run, first run **Import-Module AIPService**.

- **.dll file:** The .dll file for this module is *AIPService.dll*.

### Azure Information Protection client support

Some of the cmdlets listed below support features that are relevant only for the [Azure Information Protection classic client](/azure/information-protection/rms-client/aip-client), and not for the [unified labeling client](/azure/information-protection/rms-client/aip-clientv2). 

If no client is specified, the cmdlet or parameter is supported for both clients.

Not sure of the differences between these two clients? See this [FAQ](/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client).

> [!NOTE]
> To provide a unified and streamlined customer experience, the **Azure Information Protection classic client** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021.** 
> 
> This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).
>

## AIPService Cmdlets
### [Add-AipServiceRoleBasedAdministrator](Add-AipServiceRoleBasedAdministrator.md)
Grants administrative rights to Azure Information Protection.

### [Add-AipServiceSuperUser](Add-AipServiceSuperUser.md)
Adds a super user to Azure Information Protection.

### [Add-AipServiceTemplate](Add-AipServiceTemplate.md)
**Classic client only.** Creates a protection template for Azure Information Protection.

### [Clear-AipServiceDoNotTrackUserGroup](Clear-AipServiceDoNotTrackUserGroup.md)
**Classic client only.** Clears the group for the users who must not be tracked by Azure Information Protection.

### [Clear-AipServiceSuperUserGroup](Clear-AipServiceSuperUserGroup.md)
Removes the super user group for Azure Information Protection.

### [Connect-AipService](Connect-AipService.md)
Connects to Azure Information Protection.

### [Convert-AipServiceKeyToKeyVault](Convert-AipServiceKeyToKeyVault.md)
Changes the location of a legacy customer-managed key in Azure Information Protection with the location of a customer-managed key in Azure Key Vault.

### [Disable-AipService](Disable-AipService.md)
Deactivates the protection service from Azure Information Protection.

### [Disable-AipServiceDevicePlatform](Disable-AipServiceDevicePlatform.md)
Disables protection support from Azure Information Protection for device platforms.

### [Disable-AipServiceDocumentTrackingFeature](Disable-AipServiceDocumentTrackingFeature.md)
**Classic client only.** Disables document tracking for Azure Information Protection.

### [Disable-AipServiceIPCv3](Disable-AipServiceIPCv3.md)
Disables the MSIPC v3 platform for Azure Information Protection.

### [Disable-AipServiceSuperUserFeature](Disable-AipServiceSuperUserFeature.md)
Disables the super user feature for Azure Information Protection.

### [Disconnect-AipService](Disconnect-AipService.md)
Disconnects from Azure Information Protection.

### [Enable-AipService](Enable-AipService.md)
Activates the protection service for Azure Information Protection.

### [Enable-AipServiceDevicePlatform](Enable-AipServiceDevicePlatform.md)
Enables protection support from Azure Information Protection for device platforms.

### [Enable-AipServiceDocumentTrackingFeature](Enable-AipServiceDocumentTrackingFeature.md)
**Classic client only.** Enables document tracking for Azure Information Protection.

### [Enable-AipServiceIPCv3](Enable-AipServiceIPCv3.md)
Enables the MSIPC v3 platform for Azure Information Protection.

### [Enable-AipServiceSuperUserFeature](Enable-AipServiceSuperUserFeature.md)
Enables the super user feature for Azure Information Protection.

### [Export-AipServiceTemplate](Export-AipServiceTemplate.md)
**Classic client only.** Exports the properties of a protection template from Azure Information Protection to a file.

### [Get-AipService](Get-AipService.md)
Gets the activation status of the protection service from Azure Information Protection.

### [Get-AipServiceAdminLog](Get-AipServiceAdminLog.md)
Generates logs for all protection commands for Azure Information Protection.

### [Get-AipServiceConfiguration](Get-AipServiceConfiguration.md)
Gets the Azure Information Protection configuration of your tenant.

### [Get-AipServiceDevicePlatform](Get-AipServiceDevicePlatform.md)
Gets the device platforms in your organization that support the protection service from Azure Information Protection.

### [Get-AipServiceDocumentLog](Get-AipServiceDocumentLog.md)
**Classic client only.** Gets protection information about documents that are tracked by Azure Information Protection.

### [Get-AipServiceDocumentTrackingFeature](Get-AipServiceDocumentTrackingFeature.md)
**Classic client only.** Indicates whether document tracking is enabled or disabled for Azure Information Protection.

### [Get-AipServiceDoNotTrackUserGroup](Get-AipServiceDoNotTrackUserGroup.md)
**Classic client only.** Gets the group for the users who must not be tracked by Azure Information Protection.

### [Get-AipServiceIPCv3](Get-AipServiceIPCv3.md)
Displays whether the MSIPC v3 service is enabled or disabled for Azure Information Protection.

### [Get-AipServiceKeys](Get-AipServiceKeys.md)
Lists all Azure Information Protection tenant keys associated with your tenant.

### [Get-AipServiceMaxUseLicenseValidityTime](Get-AipServiceMaxUseLicenseValidityTime.md)
Gets the maximum validity time for Rights Management use licenses for Azure Information Protection.

### [Get-AipServiceMigrationUrl](Get-AipServiceMigrationUrl.md)
Gets the migration URL for Azure Information Protection.

### [Get-AipServiceOnboardingControlPolicy](Get-AipServiceOnboardingControlPolicy.md)
Gets the user on-boarding control policy for Azure Information Protection.

### [Get-AipServiceRoleBasedAdministrator](Get-AipServiceRoleBasedAdministrator.md)
Gets the role-based administrators for Azure Information Protection.

### [Get-AipServiceSuperUser](Get-AipServiceSuperUser.md)
Gets the super users for Azure Information Protection.

### [Get-AipServiceSuperUserFeature](Get-AipServiceSuperUserFeature.md)
Gets the status of the super user feature for Azure Information Protection.

### [Get-AipServiceSuperUserGroup](Get-AipServiceSuperUserGroup.md)
Gets the super user group for Azure Information Protection.

### [Get-AipServiceTemplate](Get-AipServiceTemplate.md)
**Classic client only.** Gets a list of protection templates for Azure Information Protection.

### [Get-AipServiceTemplateProperty](Get-AipServiceTemplateProperty.md)
**Classic client only.** Gets the properties of a protection template for Azure Information Protection.

### [Get-AipServiceTrackingLog](Get-AipServiceTrackingLog.md)
**Classic client only.** Gets tracking information for documents protected by Azure Information Protection.

### [Get-AipServiceUserLog](Get-AipServiceUserLog.md)
Downloads protection user logs from Azure Information Protection to local storage.

### [Import-AipServiceTemplate](Import-AipServiceTemplate.md)
**Classic client only.** Creates a custom protection template for Azure Information Protection.

### [Import-AipServiceTpd](Import-AipServiceTpd.md)
Imports a TPD from AD RMS for Azure Information Protection.

### [New-AipServiceRightsDefinition](New-AipServiceRightsDefinition.md)
**Classic client only.** Creates a rights definition object for a protection template for Azure Information Protection.

### [Remove-AipServiceRoleBasedAdministrator](Remove-AipServiceRoleBasedAdministrator.md)
Removes administrative rights from Azure Information Protection.

### [Remove-AipServiceSuperUser](Remove-AipServiceSuperUser.md)
Removes a super user from Azure Information Protection.

### [Remove-AipServiceTemplate](Remove-AipServiceTemplate.md)
**Classic client only.** Deletes a protection template for Azure Information Protection.

### [Set-AipServiceDoNotTrackUserGroup](Set-AipServiceDoNotTrackUserGroup.md)
**Classic client only.** Sets a group for the users who must not be tracked by Azure Information Protection.

### [Set-AipServiceKeyProperties](Set-AipServiceKeyProperties.md)
Updates the properties of a tenant key object for Azure Information Protection.

### [Set-AipServiceMaxUseLicenseValidityTime](Set-AipServiceMaxUseLicenseValidityTime.md)
Sets the maximum validity time for Rights Management use licenses for Azure Information Protection.

### [Set-AipServiceMigrationUrl](Set-AipServiceMigrationUrl.md)
Sets the migration URL for Azure Information Protection.

### [Set-AipServiceOnboardingControlPolicy](Set-AipServiceOnboardingControlPolicy.md)
Sets the user on-boarding control policy for Azure Information Protection.

### [Set-AipServiceSuperUserGroup](Set-AipServiceSuperUserGroup.md)
Sets the super user group for Azure Information Protection.

### [Set-AipServiceTemplateProperty](Set-AipServiceTemplateProperty.md)
**Classic client only.** Updates a property or properties of a protection template for Azure Information Protection.

### [Use-AipServiceKeyVaultKey](Use-AipServiceKeyVaultKey.md)
Tells Azure Information Protection to use a customer-managed tenant key in Azure Key Vault.

