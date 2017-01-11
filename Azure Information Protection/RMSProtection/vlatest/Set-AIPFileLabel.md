---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=838766 
schema: 2.0.0
---

# Set-AIPFileLabel

## SYNOPSIS
Sets or removes a classification label for one or more files, and sets the protection according to the label configuration.

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
The **Set-AIPFileLabel** cmdlet sets or removes a classification label for one or more files. This action can also apply or remove protection when labels are configured for Rights Management protection in the Azure Information Protection policy. When the command runs successfully, any existing label or protection is replaced.

To run this cmdlet, the Azure Information Protection policy must be downloaded. If this policy is not downloaded, you will be prompted to download it.

Note: This cmdlet is currently installed as part of the preview version of the Azure Information Protection client, and is not installed with the RMS Protection tool. 

## EXAMPLES

### Example 1: Apply a label with protection to a single file
```
PS C:\> Set-AIPFileLabel C:\Temp\Test.docx -LabelId d9f23ae3-a239-45ea-bf23-f515f824c57b
FileName                                    Status  Comment
--------                                    ------  -------
C:\Temp\Test.docx                           Success
```

This command sets a label for the file named C:\Temp\Test.docx. Because this label is configured to apply protection by using a Rights Management template, the file is also protected by using this template.

### Example 2: Apply a label to a multiple files
```
PS C:\> Set-AIPFileLabel -Path \\SharedDrive\DocsFolder -LabelId d9f23ae3-c839-75ef-ba62-a523e414c84c
FileName                                       Status  Comment
--------                                       ------  -------
\\SharedDrive\DocsFolder\Test1.docx            Success
\\SharedDrive\DocsFolder\Test2.docx            Success
\\SharedDrive\DocsFolder\Working\Test3.docx    Success
```

This command sets a label for all files in the DocsFolder folder and any subfolder. Because this label is not configured to apply protection by using a Rights Management template, these files are labeled but not protected.

### Example 3: Ensure all files for a specified path have a minimum label
```
PS C:\> Set-AIPFileLabel -Path \\SharedDrive\DocsFolder -LabelId d9f23ae3-a239-45ea-bf23-f515f824c57b
FileName                                       Status  Comment
--------                                       ------  -------
\\SharedDrive\DocsFolder\Test1.docx            Skipped Justification required
\\SharedDrive\DocsFolder\Test2.docx            Skipped Justification required
\\SharedDrive\DocsFolder\Working\Test3.docx    Success
```

This command attempts to set a label for all files in the DocsFolder folder and any subfolder when some files are already labeled and the Azure Information Protection policy is configured to require justification for lowering the classification label, removing a label, or removing protection. Because some files are already labeled with a higher classification and a justification message is not provided in the command, these files keep their existing label while the unlabeled file has the specified label applied.

### Example 3: Apply a label to a single file, which requires justification
```
PS C:\> Set-AIPFileLabel C:\Temp\Test.docx -LabelId d9f23ae3-a239-45ea-bf23-f515f824c57b -JustificationMessage 'The previous label no longer applies'
FileName                                    Status  Comment
--------                                    ------  -------
C:\Temp\Test.docx                           Success
```

This command set a label for the file named C:\Temp\Test.docx, which is already labeled with a higher classification label. The Azure Information Protection policy is configured to require justification for lowering the classification label, removing a label, or removing protection. Because the command includes a justification message, the new label is successfully applied.

### Example 4: Remove a label from a file
```
PS C:\> Set-AIPFileLabel C:\Temp\Test.docx -RemoveLabel -JustificationMessage 'The previous label no longer applies'
FileName                                    Status  Comment
--------                                    ------  -------
C:\Temp\Test.docx                           Success
```

This command removes the existing label from the file named C:\Temp\Test.docx, and specifies a justification message that is required because the Azure Information Protection policy setting is enabled that requires justification for lowering the classification label, removing a label, or removing protection.

## PARAMETERS

### -JustificationMessage
The justification reason for lowering the classification label, removing a label, or removing protection, if the Azure Information Protection policy requires users to supply this information. If setting a label triggers the justification and this reason is not supplied, the label is not applied. In this case, the status returned is "Skipped" with the comment "Justification required".

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
Specifies the identity (ID) of the label to apply. When a label has sub-labels, always specify the ID of just a sub-label and not the parent label. 

The label ID value is displayed in the Azure portal, on the Label blade, when you view or configure the Azure Information Protection policy. For files that have labels applied, you can also run the [Get-AIPFileLabel](./Get-AIPFileLabel.md) cmdlet to identify the label ID (MainLabelId or SubLabelId).

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
Specifies the path to the file or files to which you want to apply labels. When the path includes folders and subfolders, all files in these folders are automatically included. Wildcards are not supported. 

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
Removes any label that has been applied to a file.

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