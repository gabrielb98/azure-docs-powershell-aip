---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?LinkID=400630
schema: 2.0.0
ms.assetid: EAC26502-ECB3-43A0-B468-D166C1E4A9C4
---

# Remove-AadrmTemplate

## SYNOPSIS
Deletes a Rights Management rights policy template.

## SYNTAX

```
Remove-AadrmTemplate -TemplateId <Guid> [<CommonParameters>]
```

## DESCRIPTION
The **Remove-AadrmTemplate** cmdlet deletes an Azure Rights Management protection template.

You can delete only custom templates. You can set default templates to an archived state but you cannot delete them.

Although you can configure Rights Management templates in the Azure portal, you must use PowerShell to remove these templates.

To ensure that previously protected content can be opened and used as intended by administrators, we usually advise against deleting templates. As a best practice, delete templates only if you are sure they were not used to protect documents or emails in production. Users who are super users can continue to access content that was previously protected with a template that is now deleted. For more information about super users, see [Configuring super users for Azure Rights Management and discovery services or data recovery](https://docs.microsoft.com/information-protection/deploy-use/configure-super-users).

This cmdlet requires the template ID, which you can get with the [Get-AadrmTemplate](./Get-AadrmTemplate.md) cmdlet.

This cmdlet performs the following operations:

- Displays the template properties.

- Warns that all content protected with this template may become inaccessible.

- Asks to confirm whether to proceed.

- Calls the service to remove the template with the specified GUID.

For more information about custom templates, including how to configure them in the Azure portal, see [Configuring and managing templates for Azure Information Protection](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-templates).

## EXAMPLES

### Example 1: Delete a template
```
PS C:\>Remove-AadrmTemplate -TemplateId 36546649-4944-4462-a409-74373a67b6dd
```

This command deletes the specified template.

## PARAMETERS

### -TemplateId
Specifies the GUID of the Rights Management template.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-AadrmTemplate](./Add-AadrmTemplate.md)

[Export-AadrmTemplate](./Export-AadrmTemplate.md)

[Get-AadrmTemplate](./Get-AadrmTemplate.md)

[Import-AadrmTemplate](./Import-AadrmTemplate.md)
