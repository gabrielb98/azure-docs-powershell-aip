---
external help file: AIPService.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkID=400627
schema: 2.0.0
ms.assetid: E7942746-0F62-4D15-AD46-5DB8235FAF62
---

# Get-AipServiceTemplateProperty

## SYNOPSIS
Gets the properties of an Information Protection service template.

## SYNTAX

```
Get-AipServiceTemplateProperty -TemplateId <Guid> [-Names] [-Descriptions] [-RightsDefinitions]
 [-ContentExpirationOption] [-ContentExpirationDate] [-ContentValidityDuration] [-LicenseValidityDuration]
 [-ReadOnly] [-Status] [-ScopedIdentities] [-EnableInLegacyApps] [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceTemplateProperty** cmdlet gets specified properties of an Azure Information Protection service template, by using the *TemplateId* parameter.

Similar configuration information can also be viewed in the Azure portal, but this cmdlet also includes the template GUID.

You can query properties of a default template, or a custom template. For more information about custom templates, including how to configure them in the Azure portal, see [Configuring and managing templates for Azure Information Protection](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-templates).

## EXAMPLES

### Example 1: Get the description and the usage rights for a template
```
PS C:\>Get-AipServiceTemplateProperty -TemplateId 28168524-29c3-44f1-9e11-ea6c60bb6428 -Descriptions -RightsDefinitions
```

This command gets the description and the usage rights for all users or groups that are configured for the specified Information Protection service template.

### Example 2: For all templates, get the name, the usage rights, whether a default template, and whether published or archived
```
PS C:\>$templates = Get-AipServiceTemplate PS C:\>foreach ($template in $templates) {Get-AipServiceTemplateProperty -TemplateId $template.TemplateId -Name -RightsDefinitions -ReadOnly -Status}
```

The first command gets all the template IDs and stores them in a variable. The second command then uses this variable to get the template name, the usage rights, whether it is read-only (True for a default template, False for a custom template), and the status (Published or Archived) for each template.

## PARAMETERS

### -ContentExpirationDate
Lists the date on which content protected with the template expires.

Use this parameter only if *ContentExpirationOption* is set to OnDate.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContentExpirationOption
Gets the content expiration configuration setting for content that is protected with the template.

One of the following values is returned:

- **Never**. Indicates that content is available indefinitely.

- **OnDate**. Indicates that content expires at a certain fixed date.

- **AfterDays**. Indicates that content is available for the indicated number of days after it is protected.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContentValidityDuration
Lists the number of days from the day of protection after which content protected with the template expires.

Use this parameter only if *ContentExpirationOption* is set to AfterDays.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Descriptions
Lists the descriptions for the template in all locales.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableInLegacyApps
Indicates the behavior of a departmental template in applications that do not support departmental templates (see the *ScopedIdentities* parameter).

If set to True and the template is a departmental template, all users trying to protect content from an application that does not support departmental templates will see the template and therefore be able to select it, regardless of whether the users are members of the template's target scope or not.

If set to False, no users see and therefore cannot select the template in applications that do not support departmental templates, even if the users are members of the template's target scope.

This setting has no effect on templates that are not departmental templates and also has no effect on applications that natively support departmental templates.

This parameter is functionally the equivalent of the **Show this template to all users when the applications do not support user identity** check box when you configure **APPLICATION COMPATIBILITY** in the Azure classic portal.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LicenseValidityDuration
Lists the number of days content is accessible offline after a license to consume it is acquired.

-1 indicates unlimited access.

0 indicates that a license must be obtained for each use and that content is only available online.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Names
Lists the names for the template in all locales.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReadOnly
Indicates whether the template is a default template (True) and therefore cannot be edited or deleted, or a custom template (False) and therefore can be edited or deleted by an administrator.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RightsDefinitions
Lists the rights granted to users or groups for the content that is protected with the template.

```yaml
Type: SwitchParameter
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
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Status
The status of the template:

-**Archived** templates are available to consume previously protected content but are not displayed to users.

--**Published** templates are available to users to protect content.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TemplateId
Specifies the GUID of an Information Protection service template.

You can use the [Get-AipServiceTemplate](./Get-AipServiceTemplate.md) cmdlet to obtain the template ID of all templates.

```yaml
Type: Guid
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-AipServiceTemplate](./Get-AipServiceTemplate.md)

[Set-AipServiceTemplateProperty](./Set-AipServiceTemplateProperty.md)

