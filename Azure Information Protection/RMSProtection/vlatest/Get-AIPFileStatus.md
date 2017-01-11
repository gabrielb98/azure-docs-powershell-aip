---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=838765
schema: 2.0.0
---

# Get-AIPFileStatus

## SYNOPSIS
Gets the Azure Information Protection status for a specified file or files.

## SYNTAX

```
Get-AIPFileStatus [-Path] <String[]> [<CommonParameters>]
```

## DESCRIPTION
The **Get-AIPFileStatus** cmdlet returns the Azure Information Protection status of a specified file or all files in a specified path. This status includes whether the file has a label, and if it does, the label name, who applied it, how it was applied, and when. In addition, the status includes whether the file is protected by Rights Management, and it is, what Rights Management template was used to apply this protection.  

Note: This cmdlet is currently installed as part of the preview version of the Azure Information Protection client, and not the RMS Protection tool.

## EXAMPLES

### Example 1: Get the status of a single file
```
PS C:\> Get-AIPFileStatus C:\Test.docx
FileName        : C:\Test.docx
IsLabelled      : True
MainLabelId     : 074e257c-5848-4582-9a6f-34a182080e71
MainLabelName   : Confidential
SubLabelId      : d9f23ae3-a239-45ea-bf23-f515f824c57b
SubLabelName    : All Company
LabelingRef     : https://api.informationprotection.azure.com/api/71f988be-86f1-41aa-91ab-2b7cd011db47
LabeledBy       : alice@contoso.com
LabelingMethod  : Manual
LabelDate       : 12/20/2016 2:51:29 PM
IsRMSProtected  : True
RMSTemplateId   : e6ee2485-26b9-45e5-b34a-f744eaca53b0
RMSTemplateName : Contoso, Ltd - Confidential View Only
```

This command gets the Azure Information Protection status of the file named Test.docx. In this example, the file has a main label of Confidential, and a sub-label of All Company. The file is protected by using the template Contoso, Ltd - Confidential View Only.

### Example 2: Get the status of multiple files
```
PS C:\> Get-AIPFileStatus -Path C:\Reports
FileName        : C:\Reports\Dec.docx
IsLabelled      : True
MainLabelId     : 074e257c-5848-4582-9a6f-34a182080e71
MainLabelName   : Confidential
SubLabelId      : d9f23ae3-a239-45ea-bf23-f515f824c57b
SubLabelName    : All Company
LabelingRef     : https://api.informationprotection.azure.com/api/71f988be-86f1-41aa-91ab-2b7cd011db47
LabeledBy       : alice@contoso.com
LabelingMethod  : Manual
LabelDate       : 12/20/2016 2:51:29 PM
IsRMSProtected  : True
RMSTemplateId   : e6ee2485-26b9-45e5-b34a-f744eaca53b0
RMSTemplateName : Contoso, Ltd - Confidential View Only

FileName        : C:\Reports\In progress\Jan.docx
IsLabelled      : False
MainLabelId     : 
MainLabelName   : 
SubLabelId      : 
SubLabelName    : 
LabelingRef     : 
LabeledBy       : 
LabelingMethod  : 
LabelDate       : 
IsRMSProtected  : False
RMSTemplateId   : 
RMSTemplateName : 
```

This command gets the Azure Information Protection status of all files in the C:\Reports folder and any subfolders. In this example, the command returns one file that is labeled and protected, and another file that is not labeled or protected.

### Example 3: Create a report that contains the status of all files in a folder
```
PS C:\> Get-AIPFileStatus -Path \\SharedDrive\SharedFolder\DocsFolder | Export-Csv C:\ReportsFolder\Report.csv -NoTypeInformation
```

This command creates a .csv report of all files in the DocsFolder of the shared drive, so that you can more easily sort and find Azure Information Protection status information for multiple files. If a previous report exists in C:\ReportsFolder\Report.csv, it will be overwritten.

### Example 4: Count of files with a specific label in a folder
```
PS C:\> (Get-AIPFileStatus -Path \\SharedDrive\SharedFolder\DocsFolder | Where-Object {$_.MainLabelName -eq 'Confidential'}).Count
5
```

This command counts all files in the DocsFolder of the shared drive when these files are labeled as Confidential (regardless of their sub-label). In this example, 5 files are found.

## PARAMETERS

### -Path
Specifies the path to the file or files for which you want to get the Azure Information Protection status. When the path includes folders or subfolders, all files are in these folders are automatically included. Wildcards are not supported.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String[]

## OUTPUTS

### Microsoft.InformationProtection.Powershell.AIP.Results.GetAIPFileStatusResult

## NOTES

## RELATED LINKS

[Get-RMSTemplate](./Get-RMSTemplate.md)

[Set-AIPFileLabel](./Set-AIPFileLabel.md)
