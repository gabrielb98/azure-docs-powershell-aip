---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=838765
schema: 2.0.0
---

# Get-AIPFileStatus

## SYNOPSIS
Gets the Azure Information Protection status of a specified file, or of files in a specified folder.

## SYNTAX

```
Get-AIPFileStatus [-Path] <String[]> [<CommonParameters>]
```

## DESCRIPTION
The **Get-AIPFileStatus** cmdlet returns the Azure Information Protection status of a specified file or of files in a specified folder. This status consists of the protection status (whether the file has Rights Management protection, and if relevant, the Rights Management template information) and the label status (whether the file is labeled, and if so, the label information). 

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

This command gets the Azure Information Protection status of the file named Test.docx. This file has a main label of Confidential, and a sub-label of All Company. The file is protected by using the template Contoso, Ltd - Confidential View Only.

### Example 2: Create a report of the status of files in a folder
```
PS C:\> Get-AIPFileStatus \\SharedDrive\SharedFolder\DocsFolder | Export-Csv c:\ReportsFolder\Report.csv -NoTypeInformation
```

This example creates a .csv report of all files in the DocsFolder of the shared drive. If a previous report exists in c:\ReportsFolder\Report.csv, it will be overwritten.

### Example 3: Count of files with a specific label in a folder
```
PS C:\> (Get-AIPFileStatus \\SharedDrive\SharedFolder\DocsFolder | Where-Object {$_.MainLabelName -eq 'Confidential'}).Count
```

This example counts all files in the DocsFolder of the shared drive when these files are labeled as Confidential (regardless of their sub-label).

## PARAMETERS

### -Path
Specifies a path to one or more locations. Wildcards are not permitted. Returns the Azure Information Protection  status for all files in the specified location.

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
