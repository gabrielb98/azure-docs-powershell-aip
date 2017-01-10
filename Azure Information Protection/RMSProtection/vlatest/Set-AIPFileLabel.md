---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=838766 
schema: 2.0.0
---

# Set-AIPFileLabel

## SYNOPSIS
Sets or removes a classification label for a file, and sets the protection according to the label configuration.

## SYNTAX

### Set
```
Set-AIPFileLabel [-LabelId] <Guid> [-JustificationMessage <String>] [-Path] <String[]> [<CommonParameters>]
```

### Clear
```
Set-AIPFileLabel [-JustificationMessage <String>] [-RemoveLabel] [-Path] <String[]> [<CommonParameters>]
```

## DESCRIPTION
The **Set-AIPFileLabel** cmdlet sets or removes a classification label for one or more files, specified by path. This action can also apply or remove protection when labels are configured for Rights Management protection in the Azure Information Protection policy. 

To run this cmdlet, the Azure Information Protection policy must be downloaded. If this policy is not downloaded, you will be prompted to download it.

Note: This cmdlet is currently installed as part of the preview version of the Azure Information Protection client, and is not installed with the RMS Protection tool. 

## EXAMPLES

### Example 1: Apply a label to a single file
```
PS C:\> Set-AIPFileLabel C:\Temp\Test.docx -LabelId d9f23ae3-a239-45ea-bf23-f515f824c57b
FileName           Status ErrorMessage
--------           ------ ------------
C:\temp\Test.docx Passed
```

This command sets a label for the file named C:\Temp\Test.docx. Because this label is configured to apply protection by using a Rights Management template, the file is also protected by using this template.

### Example 2: Unsuccessful attempt to apply a lower classification label to a single file
```
PS C:\> Set-AIPFileLabel C:\Temp\Test.docx -LabelId d9f23ae3-a239-45ea-bf23-f515f824c57b
FileName           Status ErrorMessage
--------           ------ ------------
C:\temp\Test.docx Skipped Justification Required
```

This command attempts to set a label for the file named C:\Temp\Test.docx. In this example, the file already has a higher classification label, which triggers the justification prompt that has been enabled in the Azure Information Protection policy. Because no justification string is supplied in the command, the requested label is not applied and the status of "Skipped" is displayed, with "Justification Required" as the error message. 

A valid scenario for not specifying a justification message is when you want to apply a label to all files in a folder, without lowering any existing classification labels. 

### Example 3: Successfully apply a label to a single file, which requires justification
```
PS C:\> Set-AIPFileLabel C:\Temp\Test.docx -LabelId d9f23ae3-a239-45ea-bf23-f515f824c57b  -JustificationMessage 'The previous label no longer applies'
FileName           Status ErrorMessage
--------           ------ ------------
C:\temp\Test.docx Passed
```

This command, as in the previous example, attempts to set a label for the file named C:\Temp\Test.docx. This file already has a higher classification label, which triggers the justification prompt that has been enabled in the Azure Information Protection policy. Because this example also specifies a justification message, the new label is successfully applied.

### Example 4: Remove a label from a file
```
PS C:\> Set-AIPFileLabel C:\Temp\Test.docx -RemoveLabel -JustificationMessage 'The previous label no longer applies'
FileName           Status ErrorMessage
--------           ------ ------------
C:\temp\Test.docx Passed
```

This command removes the existing label from the file named C:\Temp\Test.docx, and specifies a justification message that is required because the Azure Information Protection policy setting is enabled that requires justification for lowering the classification label, removing a label, or removing protection.

## PARAMETERS

### -JustificationMessage
The justification message for lowering the classification label, removing a label, or removing protection, if the Azure Information Protection policy requires this. If setting a label triggers the justification and this message is not supplied, the label is not applied. In this case, the status returned is "Skipped" with the error message "Justification Required".

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LabelId
Specifies the identity (ID) of the label to apply. When a label has sub-labels, always specify the ID of just a sub-label and not the parent label. The label ID value is displayed in the Azure portal, in the Label blade, when you view or configure the Azure Information Protection policy.

```yaml
Type: Guid
Parameter Sets: Set
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Specifies a path to the files to which you want to apply labels. When the path includes folders and subfolders, all files are in these folders are automatically included. Wildcards are not supported. 

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: FullName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -RemoveLabel
Removes the specified label.

```yaml
Type: SwitchParameter
Parameter Sets: Clear
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

### System.String[]

## OUTPUTS

### Microsoft.InformationProtection.Powershell.AIP.Results.SetAIPFileResult

## NOTES

## RELATED LINKS

[Get-AIPFileLabel](./Get-AIPFileLabel.md)