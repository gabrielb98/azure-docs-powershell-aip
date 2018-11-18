---
external help file: AIPService.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkID=400628
schema: 2.0.0
ms.assetid: 86B51085-E23E-4A2E-A512-9098C908F3AD
---

# Import-AipServiceTemplate

## SYNOPSIS
Creates a custom protection template for Azure Information Protection.

## SYNTAX

```
Import-AipServiceTemplate -Path <String> [<CommonParameters>]
```

## DESCRIPTION
The **Import-AipServiceTemplate** cmdlet creates a custom protection template for Azure Information Protection and sets its properties according to data contained in a template file.

Although you can configure protection templates in the Azure portal, you must use PowerShell to export and import these templates.

The file you import must be a valid protection template file that has been exported from Azure Information Protection or AD RMS. The file can have any file name extension.

If you import a template file identified by a GUID that matches the GUID of an existing template for the tenant, the original template is overwritten without warning. During the import operation, the GUID for the new template is set to the GUID in the input file, so the new template is valid to consume content protected with the imported template as long as Azure Information Protection has the necessary decryption keys.

If the name of the template in the import file matches the name of an existing template for the tenant in any language, you will have two templates with the same name.

You can store a maximum of 500 custom templates (published or archived) in Azure. If you can't import templates because you have reached this limit as a result of keeping many archived templates, consider exporting them to save the information locally and then removing these templates from Azure Information Protection.

For more information about protection templates, see [Configuring and managing templates for Azure Information Protection](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-templates).

## EXAMPLES

### Example 1: Import a template file
```
PS C:\>Import-AipServiceTemplate -Path "C:\MyTemplates\MyFile.xml"
```

This command imports a template file.

## PARAMETERS

### -Path
Specifies the path to the template file to import.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-AipServiceTemplate](./Add-AipServiceTemplate.md)

[Export-AipServiceTemplate](./Export-AipServiceTemplate.md)

[Get-AipServiceTemplate](./Get-AipServiceTemplate.md)

[Remove-AipServiceTemplate](./Remove-AipServiceTemplate.md)
