---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkID=400630
schema: 2.0.0
---

# Remove-AadrmTemplate

## SYNOPSIS
Deletes a Rights Management rights policy template.

## SYNTAX

```
Remove-AadrmTemplate -TemplateId <Guid> [<CommonParameters>]
```

## DESCRIPTION
The Remove-AadrmTemplate cmdlet deletes an Azure Rights Management rights policy template.
You can delete only custom templates.
You can set default templates to an archived state but you cannot delete them.
After a template is deleted, content protected with that template might become inaccessible.
Users who are super users can continue to access content that was previously protected with a template that is now deleted.
For more information about super users, see Configuring super users for Azure Rights Management and discovery services or data recovery (https://docs.microsoft.com/rights-management/deploy-use/configure-super-users) on the Microsoft documentation site.

This cmdlet requires the template ID, which you can get with the Get-AadrmTemplate cmdlet.

This cmdlet performs the following operations:

-- Displays the template properties.
-- Warns that all content protected with this template may become inaccessible.
-- Asks to confirm whether to proceed.
-- Calls the service to remove the template with the specified GUID.

For more information about custom templates, see Configuring custom templates for Azure Rights Management (https://docs.microsoft.com/rights-management/deploy-use/configure-custom-templates) on the Microsoft documentation site.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-AadrmTemplate]()

[Export-AadrmTemplate]()

[Get-AadrmTemplate]()

[Import-AadrmTemplate]()

