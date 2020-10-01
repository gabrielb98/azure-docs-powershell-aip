---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: EAC26502-ECB3-43A0-B468-D166C1E4A9C4
online version: https://go.microsoft.com/fwlink/?linkid=2045542
schema: 2.0.0
---

# Remove-AipServiceTemplate

## SYNOPSIS
Deletes a protection template for Azure Information Protection.

## SYNTAX

```
Remove-AipServiceTemplate -TemplateId <Guid> [<CommonParameters>]
```

## DESCRIPTION
The **Remove-AipServiceTemplate** cmdlet deletes a protection template for Azure Information Protection.

You can delete only templates that you have created for your organization. You can set default templates to an archived state but you cannot delete them.

Although you can configure protection templates in the Azure portal, you must use PowerShell to remove these templates.

After a template is deleted, content protected with that template might become inaccessible. Users who are super users can continue to access content that was previously protected with a template that is now deleted. For more information about super users, see [Configuring super users for Azure Information Protection and discovery services or data recovery](/information-protection/deploy-use/configure-super-users).

This cmdlet requires the template ID, which you can get with the [Get-AipServiceTemplate](./Get-AipServiceTemplate.md) cmdlet.

This cmdlet performs the following operations:

- Displays the template properties.

- Warns that all content protected with this template may become inaccessible.

- Asks to confirm whether to proceed.

- Calls the service to remove the template with the specified GUID.

For more information about protection templates, including how to configure them in the Azure portal, see [Configuring and managing templates for Azure Information Protection](/information-protection/deploy-use/configure-policy-templates).

## EXAMPLES

### Example 1: Delete a template
```
PS C:\>Remove-AipServiceTemplate -TemplateId 36546649-4944-4462-a409-74373a67b6dd
```

This command deletes the specified template.

## PARAMETERS

### -TemplateId
Specifies the GUID of the protection template.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-AipServiceTemplate](./Add-AipServiceTemplate.md)

[Export-AipServiceTemplate](./Export-AipServiceTemplate.md)

[Get-AipServiceTemplate](./Get-AipServiceTemplate.md)

[Import-AipServiceTemplate](./Import-AipServiceTemplate.md)