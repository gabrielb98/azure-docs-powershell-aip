---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 7B9098EE-CE4B-4033-AB04-2F53B6238CE2
online version: https://go.microsoft.com/fwlink/?linkid=2045037
schema: 2.0.0
---

# Export-AipServiceTemplate

## SYNOPSIS
Exports the properties of a protection template from Azure Information Protection to a file.

## SYNTAX

```
Export-AipServiceTemplate -TemplateId <Guid> -Path <String> [-Force] [<CommonParameters>]
```

## DESCRIPTION
The **Export-AipServiceTemplate** cmdlet exports all the properties of a protection template from Azure Information Protection to a file. You can then import the template to another tenant using Azure Information Protection, or you can edit the exported template and import it back to the original tenant. You can use this technique to perform bulk edits of complex properties in templates, such as multilingual names and descriptions.

Although you can configure protection templates in the Azure portal, you must use PowerShell to export and import these templates.

Tip: Consider using this cmdlet as a way to back up your protection templates, so that you can revert to a known-good version if required.

The export process does not automatically append a file name extension, so you can specify a file name extension to match the application that you will use to view and edit the resulting data.

You can use the [Get-AipServiceTemplate](./Get-AipServiceTemplate.md) cmdlet to get the GUIDs of all templates.

For more information about protection templates, including how to configure them in the Azure portal, see [Configuring and managing templates for Azure Information Protection](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-templates).

## EXAMPLES

### Example 1: Export a template
```
PS C:\>Export-AipServiceTemplate -Path "C:\MyTemplates\MyTemplateFile.xml" -TemplateId 28168524-29c3-44f1-9e11-ea6c60bb6428
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
Specifies the GUID of a protection template.

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

[Add-AipServiceTemplate](./Add-AipServiceTemplate.md)

[Get-AipServiceTemplate](./Get-AipServiceTemplate.md)

[Import-AipServiceTemplate](./Import-AipServiceTemplate.md)

[Remove-AipServiceTemplate](./Remove-AipServiceTemplate.md)

