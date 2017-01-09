---
external help file: RMSProtection.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkID=623207
schema: 2.0.0
---

# Set-AIPFileLabel

## SYNOPSIS
Sets a file label, and sets the RMS protection according to the policy

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
The **Set-AIPFileLabel** cmdlet applies a label to files (or to files in folders) specified by path, or clears the label from these files.

In order to run this cmdlet the user who is running it should have a AIP policy downloaded. If no such policy is found, the user will be prompted to download a policy.

## EXAMPLES

### Example 1 Applies a label to a single file
```
PS C:\> Set-AIPFileLabel C:\Temp\Test.docx -LabelId d9f23ae3-a239-45ea-bf23-f515f824c57b
FileName           Status ErrorMessage
--------           ------ ------------
C:\temp\Test.docx Passed
```

This command sets a confidential label to the file C:\Temp\Test.docx. As this label is associated with an RMS protection template, the template is also set.

### Example 2 Applies a label to a single file which is currently labeled with a higher label.
```
PS C:\> Set-AIPFileLabel C:\Temp\Test.docx -LabelId d9f23ae3-a239-45ea-bf23-f515f824c57b
FileName           Status ErrorMessage
--------           ------ ------------
C:\temp\Test.docx Skipped Justification Required
```

This command attempts to set a confidential label to the file C:\Temp\Test.docx. However this file was labeled as Secret, and the policy requires a justification when downgrading a label.
Therefore the file was skipped, and we receives a Error Message of Justification Required. A more general use of this functionality would be if we want to apply a label to all files in a folder, but without downgrading any
existing labeled file.

### Example 3 Force apply a label to a single file which is currently labeled with a higher label.
```
PS C:\> Set-AIPFileLabel C:\Temp\Test.docx -LabelId d9f23ae3-a239-45ea-bf23-f515f824c57b  -JustificationMessage 'The previous label no longer applies'
FileName           Status ErrorMessage
--------           ------ ------------
C:\temp\Test.docx Passed
```

This command sets a confidential label to the file C:\Temp\Test.docx. Even though this file was labeled as Secret, and the policy requires a justification when downgrading a label, the labelling succeeds, as a justification message was provided.

### Example 4 Remove labels from a file.
```
PS C:\> Set-AIPFileLabel C:\Temp\Test.docx -RemoveLabel  -JustificationMessage 'The previous label no longer applies'
FileName           Status ErrorMessage
--------           ------ ------------
C:\temp\Test.docx Passed
```

This command removes labels from the file C:\Temp\Test.docx. As this is considered as downgrading a label, and the policy requires a justification in such cases, a justification message is provided.

## PARAMETERS

### -JustificationMessage
The justification message for downgrading labels, if the policy requires one. If this is missing, and the result of the cmdlet would result in downgrading the labels, and the policy requires such a justification, the file will be skipped.

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
Specifies the ID of the label to apply. When applying a sub-label, this should be the ID of the sub-label. This *LabelId* can be found in the Azure Portal AIP management.

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
Specifies a path to one or more locations. Wildcards are not permitted. This cmdlet will clear labels for all files in these locations.

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
Indicates that this cmdlet removes labels.

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
