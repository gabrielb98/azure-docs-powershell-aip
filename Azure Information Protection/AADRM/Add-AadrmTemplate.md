---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkID=400624
schema: 2.0.0
ms.assetid: 1CBB5251-7084-4545-B71A-670AC19DC5E4
---

# Add-AadrmTemplate

## SYNOPSIS
Creates a Rights Management template.

## SYNTAX

```
Add-AadrmTemplate -Names <Hashtable> -Descriptions <Hashtable>
 [-RightsDefinitions <System.Collections.Generic.List`1[Microsoft.RightsManagementServices.Online.Admin.TemplateRightsDefinition]>]
 [-ContentExpirationOption <ContentExpirationType>] [-ContentExpirationDate <DateTime>]
 [-ContentValidityDuration <Int32>] [-LicenseValidityDuration <Int32>] [-Status <TemplateStatus>]
 [-ScopedIdentities <System.Collections.Generic.List`1[System.String]>] [-EnableInLegacyApps <Boolean>]
 [<CommonParameters>]
```

## DESCRIPTION
The **Add-AadrmTemplate** cmdlet creates an Azure Rights Management custom template with the specified name, description, and policy, and sets the status of the template to archived or published.

The same configuration actions can also be done in the Azure portal. 

Important: Before you use this cmdlet, you must first create a rights definition object that specifies the rights that you want to grant and to whom, by using the [New-AadrmRightsDefinition](./New-AadrmRightsDefinition.md) cmdlet.

You can store a maximum of 500 custom templates (published or archived) in Azure. If you can't add new templates because you have reached this limit as a result of keeping many archived templates, consider exporting them to save the information locally and then removing these templates in Azure.

For more information about custom templates, including how to configure them in the Azure portal, see [Configuring and managing templates for Azure Information Protection](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-templates) on the Microsoft documentation site.

## EXAMPLES

### Example 1: Create a departmental template for confidential content
```
PS C:\> $names = @{}
PS C:\> $names[1033] = "New Launch - Confidential content"
PS C:\> $names[1034] = " Nuevo Lanzamiento - Contenido confidencial"
PS C:\> $descriptions = @{}
PS C:\> $descriptions[1033] = "This content is confidential for people working on the New Launch project and should not be shared externally"
PS C:\> $descriptions[1034] = "Este contenido es confidencial para empleados trabajando en el proyecto Nuevo Lanzamiento y no debe ser compartido fuera de la organización"
PS C:\> $r1 = New-AadrmRightsDefinition -EmailAddress marketing@contoso.com -Rights "VIEW","EXPORT"
PS C:\> $r2 = New-AadrmRightsDefinition -EmailAddress engineering@contoso.com -Rights "VIEW","DOCEDIT"
PS C:\> Add-AadrmTemplate -Names $names -Descriptions $Descriptions -LicenseValidityDuration 5 -RightsDefinitions $r1, $r2 -ScopedIdentities engineering@contoso.com -Status Published
```

This example creates a departmental template for engineers when they are working on the New Launch project. The template is named **New Launch - Confidential Content** and has names and descriptions in English and in Spanish. It grants View and Export rights to the marketing department (lets them view and save to a non-protected file) by using the marketing@contoso.com group, and View and DocEdit rights (lets them view and edit the contents but not save the changes) to the engineering department by using the engineering@contoso.com group.

## PARAMETERS

### -ContentExpirationDate
Specifies the date on which content protected with the template expires.

Use this parameter only if the *ContentExpirationOption* parameter is set to OnDate.

```yaml
Type: DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContentExpirationOption
Specifies the type of content expiration for content protected with the template. 

The acceptable values for this parameter are:

- **Never**.
Indicates that content is available indefinitely.

- **OnDate**.
Indicates that content expires at a certain fixed date.

- **AfterDays**.
Indicates that content is available for the indicated number of days after it is protected.

```yaml
Type: ContentExpirationType
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContentValidityDuration
Specifies the number of days from the first day of protection after which content protected with the template expires.

Use this parameter only if the *ContentExpirationOption* parameter is set to AfterDays.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Descriptions
Specifies a list of descriptions for the template.

Create names and descriptions for multiple locale IDs by using the hash-table syntax in Windows PowerShell. There must be at least one name/description pair. The locale IDs for names and descriptions must match each other. If a locale ID is specified, its value must contain a non-empty string.

$descriptions = @{}

$descriptions\[1033\] = "This content is confidential and should not be shared externally"

$descriptions\[1034\] = "Este contenido es confidencial y no debe ser compartido fuera de la organización"

```yaml
Type: Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableInLegacyApps
Determines the behavior of a departmental template in applications that do not support departmental templates (see the *ScopedIdentities* parameter).

If set to True and the template is a departmental template, all users trying to protect content from an application that does not support departmental templates will see the template and therefore be able to select it, regardless of whether the users are members of the template's target scope or not.

If set to False, no users see and therefore cannot select the template in applications that do not support departmental templates, even if the users are members of the template's target scope.

This setting has no effect on templates that are not departmental templates and also has no effect on applications that natively support departmental templates.

Note: This parameter is functionally the equivalent of the **Show this template to all users when the applications do not support user identity** check box if you configured **APPLICATION COMPATIBILITY** in the Azure classic portal. The classic portal is now retired and there is no equivalent setting in the Azure portal.

The Azure Information Protection client supports departmental templates whereas Exchange Outlook Web Access and Exchange ActiveSync are examples of applications that do not currently support departmental templates. For these Exchange applications (and all other applications that cannot support departmental templates), you must decide whether all users can select a departmental template from the list of available templates, or no users can select a departmental template from the list.

This setting does not affect whether a user can access content that is protected by a departmental template; it only affects the ability for a user to select the template itself.

If you have applications that do not yet natively support departmental templates, you can use a [custom RMS template download script](https://go.microsoft.com/fwlink/?LinkId=524506) or other tools to deploy these templates to the local RMS client folder. Then, these applications will correctly display the departmental templates:

- For Office 2010, the client folder is %localappdata%\Microsoft\DRM\Templates.

- From a client computer that has downloaded all the templates, you can copy and then paste the template files to other computers.

```yaml
Type: Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LicenseValidityDuration
Specifies the validity period of use licenses for content that is protected with this template.

The value is specified as the number of days that content is available offline after a use license is acquired (0-9999). During this period users can re-open content they previously accessed without requiring an Internet network connection.

Reducing this value gives more control to document owners by helping ensure that content that has been revoked or for which the policy has changed cannot be accessed for too long after these changes.

Increasing this value gives more freedom to users to access the content without requiring an Internet network connection.

To specify unlimited access, use -1. To specify that a use license must be obtained each time the protected content is accessed and that content is available only with an Internet connection, specify 0.

Each organization has a maximum use license validity time, which is 30 days by default and can be configured by using the [Set-AadrmMaxUseLicenseValidityTime](./Set-AadrmMaxUseLicenseValidityTime.md). The value that you specify for the *LicenseValidityDuration* parameter must be lower than that value.

When there are different values for the use license validity time, for example, one value for the tenant and one for the template, Azure RMS uses the most restrictive value.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Names
Specifies a list of names for the template.

Do not include any of the following characters in the name because not all services and applications that use Azure Information Protection can support these characters: `< > % & / ? ; + \ : #`

Create names and descriptions for multiple locale IDs by using the hash-table syntax in Windows PowerShell. There must be at least one name/description pair.The locale IDs for names and descriptions must match each other. If a locale ID is specified, its value must contain a non-empty string.


$names = @{}

$names\[1033\] = "Confidential content"

$names\[1034\] = "Contenido confidencial"

```yaml
Type: Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RightsDefinitions
Specifies a list of rights definition objects that are specified by using the [New-AadrmRightsDefinition](./New-AadrmRightsDefinition.md) cmdlet.

These rights definition objects express the rights to grant individual users or groups to content that is protected by applying the template.

Rights definition objects contain the email address for the identity and the rights to assign to it.

```yaml
Type: System.Collections.Generic.List`1[Microsoft.RightsManagementServices.Online.Admin.TemplateRightsDefinition]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScopedIdentities
Lists the users by email address (account or group) that can see and therefore select departmental templates from applications.

For the specified users to see the templates, the application must support departmental templates or the *EnableInLegacyApps* parameter must be set to True.

```yaml
Type: System.Collections.Generic.List`1[System.String]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Status
Specifies the status of the template.

Allowed values are **Archived** and **Published**.

- Archived templates are available to consume previously protected content but are not visible to users. 

- Published templates are distributed to users and made available to protect content.

```yaml
Type: TemplateStatus
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String[],System.String[],System.String[],System.string,System.DateTime,System.int,System.int
-Names $Names ; One or more names for the template, in various languages to present to users depending on their system locale.

\[-Descriptions $Descriptions\] ; One or more descriptions for the template, in various languages to present to users depending on their system locale.

\[-RightsDefinitions {$r1,$r2,...}\] ; A list of rights definitions in the form of **Rights Definition** objects.

\[-ContentExpirationOption ContentExpirationType.Never|OnDate|AfterDays\] ; The type of content expiration for content protected with the template.

\[-ContentExpirationDate **DateTime**\] ; The date or time when the content expires, if *ContentExpirationOption* is set to OnDate.

\[-ContentValidityDuration int\] ; The number of days for which content is available after it is protected if *ContentExpirationOption* is set to AfterDays.

\[-LicenseValidityDuration int\] ; The number of days for which content is available online until it expires (0-9999).
To specify unlimited access, use -1.
To specify that a license must be obtained for each use and that content is available only online, use 0.

\[-Status TemplateStatus.Archived|Published\] ; The status of the template.
Archived templates are available to consume previously protected content but are not presented to users.
Published templates are distributed to users and made available for protecting content.

Create names and descriptions for multiple locale IDs by using the hash-table syntax in Windows PowerShell. There must be at least one name/description pair. The locale IDs for names and descriptions must match each other. If a locale ID is specified, its value must contain a non-empty string.


$names = @{}

$names\[1033\] = "Confidential content"

$names\[1034\] = "Contenido confidencial"

$descriptions = @{}

$descriptions\[1033\] = "This content is confidential and should not be shared externally"

$descriptions\[1034\] = "Este contenido es confidencial y no debe ser compartido fuera de la organización"

The rights are specified as a list of **Rights Definition** objects that contain the email address for the identity and the rights to assign to it.

## OUTPUTS

## NOTES

## RELATED LINKS

[Export-AadrmTemplate](./Export-AadrmTemplate.md)

[Get-AadrmTemplate](./Get-AadrmTemplate.md)

[Import-AadrmTemplate](./Import-AadrmTemplate.md)

[New-AadrmRightsDefinition](./New-AadrmRightsDefinition.md)

[Remove-AadrmTemplate](./Remove-AadrmTemplate.md)
