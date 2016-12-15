---
---
# TOPIC
## about_RMSProtection_AzureRMS

## SHORT DESCRIPTION
Information to get started with the RMS Protection tool for an organization
that uses Azure Rights Management (Azure RMS) data protection.

## LONG DESCRIPTION
This topic describes how to start using the RMS Protection tool to protect
or unprotect files if your organization uses the Azure Rights Management
service from Azure Information Protection. The information includes:
- Additional prerequisites that are specific to Azure RMS
- Using RMS Protection cmdlets - example scenarios

## PREREQUISITES:
In addition to any prerequisites for the RMS Protection tool (see
[RMS Protection Cmdlets](https://msdn.microsoft.com/library/azure/mt433195.aspx) (https://msdn.microsoft.com/library/azure/mt433195.aspx) on MSDN) there are
additional prerequisite for Azure RMS:

1: The Azure Rights Management service must be activated
2: To unprotect files for others using your own account: The
super user feature must be enabled for your organization and your
account must be configured to be a super user for Azure RMS.
3: To protect or unprotect files without interaction: Create a service
principal account, run Set-RMSServerAuthentication, and consider
making this service principal a super user for Azure RMS.
4: For regions outside North America: Edit the registry.

For the first prerequisite, if your Azure Information Protection tenant is not
activated, see the instructions for [Activating Azure Rights Management](https://docs.microsoft.com/information-protection/deploy-use/activate-service)
on the Microsoft documentation site.

For the second prerequisite, see [Configuring super users for
Azure Rights Management and Discovery Services or Data Recovery](https://docs.microsoft.com/information-protection/deploy-use/configure-super-users)
on the Microsoft documentation site.

For the third prerequisite, to use the cmdlets without user interaction
you must authenticate with the Azure RMS service by using a service principal,
which you do by using the [Set-RMSServerAuthentication](./Set-RMSServerAuthentication.md) cmdlet. You must do this
for each Windows PowerShell session that runs cmdlets that contact the
Azure RMS service. Before you run this cmdlet, make sure that you have
these three identifiers:

- BposTenantId
- AppPrincipalId
- Symmetric Key

To get BposTenantId:
- Run the Get-AadrmConfiguration cmdlet from the Azure RMS
Windows PowerShell module:

1. If this module is not already installed on your computer, see
[Installing Windows PowerShell for Azure Rights Management]
(https://docs.microsoft.com/information-protection/deploy-use/install-powershell)

2. Start Windows PowerShell with the Run as Administrator option.

3. Use the **Connect-AadrmService** cmdlet to connect to the Azure RMS service:
C:\PS> Connect-AadrmService

When prompted, enter your Azure Information Protection tenant
administrator credentials (typically, you will use an account that is a
global administrator for Azure Active Directory or Office 365).

4. Run **Get-AadrmConfiguration** and make a copy of the BPOSId value.
The following is an example of output from **Get-AadrmConfiguration**

C:\PS> Get-AadrmConfiguration

BPOSId                                   : 23976bc6-dcd4-4173-9d96-dad1f48efd42
RightsManagement ServiceId               : 1a302373-f233-440600909-4cdf305e2e76
LicensingIntranetDistributionPointUrl    : https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/licensing
LicensingExtranetDistributionPointUrl    : https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/licensing
CertificationIntranetDistributionPointUrl: https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/certification
CertificationExtranetDistributionPointUrl: https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/certification
6. Disconnect from the service:

```
C:\PS>Disconnect-AadrmService
```
To get AppPrincipalId and Symmetric Key:
- Run the **New-MsolServicePrincipal cmdlet** from the Azure Active Directory
module:

1. If this module is not already installed on your computer, see
[Install the Azure AD Module](https://technet.microsoft.com/library/jj151815.aspx#bkmk_installmodule).

2. Start Windows PowerShell with the Run as Administrator option.

3. Use the **Connect-MsolService** cmdlet to connect to Azure AD:

```
C:\PS> Connect-MsolService
```
When prompted, enter your Azure AD tenant administrator
credentials (typically, you will use an account that is a global
administrator for Azure Active Directory or Office 365).

4. Run the **New-MsolServicePrincipal** cmdlet to create a new
service principal:
```
C:\PS> New-MsolServicePrincipal
```
When prompted, enter your choice of a display name for this
service principal that will help you identify its purpose later as
an account for you to connect to the Azure Rights Management service so
that you can protect and unprotect files.

An example of the output of **New-MsolServicePrincipal** is shown here:
```
Supply values for the following parameters:
DisplayName: AzureRMSProtectionServicePrincipal
The following symmetric key was created as one was not supplied
zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=

Display Name: AzureRMSProtectionServicePrincipal
ServicePrincipalNames: (b5e3f7g1-b5c2-4c96-a594-a0807f65bba4)
ObjectId: 23720996-593c-4122-bfc7-1abb5a0b5109
AppPrincialId: b5e3f76a-b5c2-4c96-a594-a0807f65bba4
TrustedForDelegation: False
AccountEnabled: True
Addresses: ()
KeyType: Symmetric
KeyId: 8ef61651-ca11-48ea-a350-25834a1ba17c
StartDate: 3/7/2014 4:43:59 AM
EndDate: 3/7/2014 4:43:59 AM
Usage: Verify
```
5. From this output, make a note of the symmetric key and the AppPrincialId.

It is particularly important that you make a copy of the symmetric key
because you cannot retrieve it in full later so if you do not know it,
you will have to create a new service principal the next time you need
to authenticate to the Azure Rights Management service.

From these instructions and our examples, we have the three identifiers
required to run [Set-RMSServerAuthentication](./Set-RMSServerAuthentication.md):
* Tenant Id: 23976bc6-dcd4-4173-9d96-dad1f48efd42
* Symmetric key: zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=
* AppPrincipalId: b5e3f76a-b5c2-4c96-a594-a0807f65bba4

Our example command would then look like this:
```
C:\PS> Set-RMSServerAuthentication
-Key zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=
-AppPrincipalId b5e3f76a-b5c2-4c96-a594-a0807f65bba4
-BposTenantId 23976bc6-dcd4-4173-9d96-dad1f48efd42
```
As shown in the previous command, you can supply the values with a single
command, or just type [Set-RMSServerAuthentication](./Set-RMSServerAuthentication.md), and supply the values
one-by-one when prompted. When the command completes, you see
"The RmsServerAuthentication is set to ON", which means you can now protect
and unprotect files by using your service principal.

Consider making this service principal a super user: To ensure that this
service principal can always unprotect files for others, it can be configured
to be a super user. In the same way as you configure a standard user account
to be a super user, you use the same Azure RMS cmdlet, Add-AadrmSuperUser
(https://msdn.microsoft.com/library/azure/dn629411.aspx) but specify the
-ServicePrincipalId parameter with your AppPrincipalId value.

For more information about super users, see "Configuring super users for
Azure Rights Management and discovery services or data recovery"
(https://docs.microsoft.com/information-protection/deploy-use/configure-super-users)
on the Microsoft documentation site.

Note: To use your own account to authenticate to the Azure Rights Management
service, there's no need to run **Set-RMSServerAuthentication** before you
protect or unprotect files, or get templates.

Finally, for the fourth prerequisite for authentication outside the Azure
North America region, you must edit the registry as follows (if your Azure
Information Protection tenant is in North America, do not do this step):

1. Run the **Get-AadrmConfiguration** cmdlet again, and make a note of the
values for CertificationExtranetDistributionPointUrl and
LicensingExtranetDistributionPointUrl

2. On each computer where you will run the RMS Protection cmdlets, open the
registry editor and navigate to:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC

3. If you do not see the ServiceLocation key, create it, so that your
registry path shows
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation

4. For the ServiceLocation key, create two keys if they do not exist, named
EnterpriseCertification and EnterprisePublishing. When you create these
REG_SZ keys, do not change the Name of "(Default)", but edit them to set
the Value data:
- For EnterpriseCertification, paste your
CertificationExtranetDistributionPointUrl value.
- For EnterprisePublishing, paste your
LicensingExtranetDistributionPointUrl value.

5. Close the registry editor. There is no need to restart your computer. However,
if you are using a service principal account rather than your own user account,
you must run the **Set-RMSServerAuthentication** command after making this registry
edit.

## USING RMS PROTECTION CMDLETS - EXAMPLE SCENARIOS
A typical scenario for these cmdlets is to protect all files in a folder
by using a rights policy template, or to unprotect a file.

First, only if you need to authenticate to the Azure Rights Management service
with a service principal rather than use your own account, type:
```
C:\PS> Set-RMSServerAuthentication
```
When prompted, enter the three identifiers as described in the
prerequisites section.

Before you can protect files, you need to get a list of Rights Management
templates to identify which one to use and its corresponding ID number. From the
output, you can then copy the template ID:
```
C:\PS> Get-RMSTemplate

TemplateId        : {82bf3474-6efe-4fa1-8827-d1bd93339119}
CultureInfo       : en-US
Description       : This content is proprietary information intended for
internal users only. This content cannot be modified.
Name              : Contoso, Ltd - Confidential View Only
IssuerDisplayName : Contoso, Ltd
FromTemplate      : True

TemplateId        : {e6ee2481-26b9-45e5-b34a-f744eacd53b0}
CultureInfo       : en-US
Description       : This content is proprietary information intended for
internal users only. This content can be modified but
cannot be copied and printed.
Name              : Contoso, Ltd - Confidential
IssuerDisplayName : Contoso, Ltd
FromTemplate      : True
FromTemplate      : True
```
Note that if you didn't run the **Set-RMSServerAuthentication** command, you will be
authenticated to the Azure Rights Management service by using your own user
account. If you are on a domain-joined computer, your current credentials will
always be used automatically. If you are on a workgroup computer, you will be
prompted to sign in to Azure and these credentials are then cached for subsequent
commands. In this scenario, if you later need to sign in as a different user, use
the **Clear-RMSAuthentication** cmdlet.

Now you know the template ID, you can use it with the **Protect-RMSFile**
cmdlet to protect a single file or all files in a folder. For example, if
you want to protect a single file only and overwrite the original, by using the
"Contoso, Ltd - Confidential" template:
```
C:\PS> Protect-RMSFile -File C:\Test.docx -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

InputFile             EncryptedFile
---------             -------------
C:\Test.docx          C:\Test.docx
```
To protect all files in a folder, use the -Folder parameter with a drive
letter and path, or UNC path. For example:
```
C:\PS> Protect-RMSFile -Folder \Server1\Documents -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

InputFile                          EncryptedFile
---------                          -------------
\Server1\Documents\Test1.docx     \Server1\Documents\Test1.docx
\Server1\Documents\Test2.docx     \Server1\Documents\Test2.docx
\Server1\Documents\Test3.docx     \Server1\Documents\Test3.docx
\Server1\Documents\Test4.docx     \Server1\Documents\Test4.docx
```
When the file name extension does not change after RMS protection is
applied, you can always use the [Get-RMSFileStatus](./Get-RMSFileStatus.md) cmdlet later to check
whether the file is protected. For example:
```
C:\PS> Get-RMSFileStatus -File \Server1\Documents\Test1.docx

FileName                              Status
--------                              ------
\Server1\Documents\Test1.docx         Protected
```
To unprotect a file, you must have Owner or Extract rights from when the
file was protected, or you must be running the cmdlets as a super user. Then,
use the Unprotect cmdlet. For example:
```
C:\PS> Unprotect-RMSFile C:\test.docx -InPlace

InputFile                             DecryptedFile
---------                             -------------
C:\Test.docx                          C:\Test.docx
```
For more information about any of the RMS Protection module cmdlets, use the
**Get-Help** <cmdlet name> cmdlet, where <cmdlet name> is the name of the cmdlet
that you want to research. For example:
```
C:\PS> Get-Help Get-RMSTemplate
```
## SEE ALSO

[Clear-RMSAuthentication](./Clear-RMSAuthentication.md)

[Get-RMSFileStatus](./Get-RMSFileStatus.md)

[Get-RMSTemplate](./Get-RMSTemplate.md)

[Protect-RMSFile](./Protect-RMSFile.md)

[Unprotect-RMSFile](./Unprotect-RMSFile)

[Set-RMSServerAuthentication](./Set-RMSServerAuthentication.md)
