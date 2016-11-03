---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkID=400625
schema: 2.0.0
ms.assetid: 7B9098EE-CE4B-4033-AB04-2F53B6238CE2
---

# Export-AadrmTemplate

## SYNOPSIS
Exports the properties of a rights policy template to a file.

## SYNTAX

```
Export-AadrmTemplate -TemplateId <Guid> -Path <String> [-Force] [<CommonParameters>]
```

## DESCRIPTION
The **Export-AadrmTemplate** cmdlet exports all the properties of a rights policy template to a file.
You can then import the template to another Azure Rights Management tenant or you can edit it and import it back to the original tenant.
You can use this technique to perform bulk edits of complex properties in templates, such as multilingual names and descriptions.

Tip: Consider using this cmdlet as a way to back up your custom templates, so that you can revert to a known-good version if required..

The export process does not automatically append a file name extension, so you can specify a file name extension to match the application that you will use to view and edit the resulting data.

You can use the Get-AadrmTemplate cmdlet to get the GUIDs of all templates.

For more information about custom templates, see Configuring custom templates for Azure Rights Managementhttps://docs.microsoft.com/rights-management/deploy-use/configure-custom-templates (https://docs.microsoft.com/rights-management/deploy-use/configure-custom-templates) on the Microsoft documentation site.

## EXAMPLES

### Example 1: Export a template
```
PS C:\>Export-AadrmTemplate -Path "C:\MyTemplates\MyTemplateFile.xml" -TemplateId 28168524-29c3-44f1-9e11-ea6c60bb6428
```

This command exports the specified template to the file named MyTemplateFile.xml.

## PARAMETERS

### -Force
Indicates that the cmdlet overwrites an existing template file that has the same path.

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

### -Path
Specifies the path to the location where you want to save the file.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TemplateId
Specifies the GUID of an Rights Management template.

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

[Add-AadrmTemplate](./Add-AadrmTemplate.md)

[Get-AadrmTemplate](./Get-AadrmTemplate.md)

[Import-AadrmTemplate](./Import-AadrmTemplate.md)

[Remove-AadrmTemplate](./Remove-AadrmTemplate.md)


