---
external help file: RMSProtection.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=838766
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
Use the **Set-AIPFileLabel** cmdlet to apply or clear a label using Azure Information Protection. Upon label action this cmdlet may apply or remove RMS protection automatically – based on the protection action that is associated with this label on your Azure Information Protection policy.

## EXAMPLES

### Example 1: Apply "Confidential" label on all files in a folder (and its entire subfolders)
```
PS C:\> Set-AIPFileLabel -Path c:\projects\ -LabelId d9f23ae3-1324-1234-1234-f515f824c57b
FileName                    Status      Comment
--------                    ------      ------------
C:\projects\project1.docx   Success
C:\projects\datasheet.pdf   Success
C:\projects\image.jpg       Success
C:\projects\analysis.xlsx   Skipped    Justification required
C:\projects\dashboard.xlsx  Success
```

This command sets a Confidential label on all files in the Projects folder, and its entire subfolders. 
Files labeled Confidential may become encrypted (in place) if your Azure Information Protection policy applies encryption for files labeled Confidential.
The labeling and encryption owner is the user that is signed-in to the device running this PowerShell command.
Note that in this example the analysis.xlsx file was not labeled, as it is currently classified with a higher label, and a justification was not provided in the cmdlet. 


### Example 2: Apply "Confidential" label on a single file, providing business justification, in case that the file is classified with a higher label 
```
PS C:\> Set-AIPFileLabel -Path \\finance\projects\analysis.xlsx -LabelId d9f23ae3-1324-1234-1234-f515f824c57b -JustificationMessage 'The previous label no longer applies'
FileName                          Status      Comment
--------                          ------      ------------
\\finance\projects\analysis.xlsx  Success     
```

This command labels a file as “Confidential” using a business justification. 
This justification is used and logged when required by the policy, on cases of downgrade the label, remove the protection or clear the label. 

### Example 3: Apply “Internal” label on all files that are currently NOT labeled  
```
PS C:\> Get-AIPFileStatus -Path \\finance\projects\ | where {$_.IsLabelled -eq $False} | Set-AIPFileLabel -LabelId d9f23ae3-4321-4321-4321-f515f824c57b
FileName                              Status Comment
--------                              ------ ------------
\\finance\projects\image.jpg          Success
\\finance\projects\pricelist.pdf      Success
\\finance\projects\announcement.docx  Success
\\finance\projects\analysis.xlsx      Success
```

This command identifies all files that are not labeled using the Get-AIPFileStatus cmdlet. 
These files are then labeled using the Set-AIPFilelabel cmdlet.

### Example 4: Apply "Confidential" label on DOCX files that are not labeled 
```
PS C:\> Get-ChildItem C:\Projects\*.docx -File -Recurse | Get-AIPFileStatus | where {$_.IsLabelled -eq $False} | Set-AIPFileLabel -LabelId d9f23ae3-1234-1234-1234-f515f824c57b
FileName                   Status  Comment
--------                   ------  ------------
C:\Projects\analysis.docx  Success
C:\Projects\projects.docx  Success
```

This example first identifies all DOCX files in the c:\Projects folder (and its subfolders) using Get-Child-Item, then finds the files that are not labeled using the Get-AIPFileStatus cmdlet. 
These files are then labeled using the Set-AIPFilelabel cmdlet.
Note: Get-Child-Item can be used with Get-AIPFileStatus as the FullName is an alias for Path. 

### Example 5: Remove a label from a file.
```
PS C:\> Set-AIPFileLabel C:\Projects\analysis.docx -RemoveLabel -JustificationMessage 'The previous label no longer applies'

FileName                   Status Comment
--------                   ------ ------------
C:\Projects\analysis.docx  Success
```

This command removes the Azure Information Protection label from C:\Projects\analysis.docx. 

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
Aliases: FullName, FileName

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

[Get-AIPFileStatus](./Get-AIPFileStatus.md)