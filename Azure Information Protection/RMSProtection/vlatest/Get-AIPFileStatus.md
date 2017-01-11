---
external help file: RMSProtection.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=838765
schema: 2.0.0
---

# Get-AIPFileStatus

## SYNOPSIS
Get the Azure Information Protection label and protection associated with a file

## SYNTAX

```
Get-AIPFileStatus [-Path] <String[]> [<CommonParameters>]
```

## DESCRIPTION
The **Get-AIPFileStatus** cmdlet returns the Azure Information Protection status of a specified file or all files in a specified path. This status includes whether the file has a label, and if it does, the label name, who applied it, how it was applied, and when. In addition, the status includes whether the file is protected by Rights Management, and it is, what Rights Management template was used to apply this protection.  

Note: This cmdlet is currently installed as part of the preview version of the Azure Information Protection client, and not the RMS Protection tool.

## EXAMPLES

### Example 1: Get label and protection status on a single file.
```
PS C:\> Get-AIPFileStatus -Path \\finance\projects\project.docx
FileName        : \\finance\projects\project.docx
IsLabelled      : True
MainLabelId     : 074e257c-1234-1234-1234-34a182080e71
MainLabelName   : Confidential
SubLabelId      : d9f23ae3-1234-1234-1234-f515f824c57b
SubLabelName    : Finance group
LabelingRef     : https://api.informationprotection.azure.com/api/72f988bf-1234-1234-1234-2d7cd011db47
LabeledBy       : John@Contoso.com
LabelingMethod  : Manual
LabelDate       : 12/12/2016 12:24:36 PM
IsRMSProtected  : True
RMSTemplateId   : e6ee2481-1234-1234-1234-f744eacd53b0
RMSTemplateName : Contoso - Confidential Finance  
```

This command provides information about a file that is labeled as Confidential \ Finance Group. This file was labeled manually by John. This file is also encrypted. 

### Example 2: Get label and protection status on all files stored in a specific folder. Export the results to a CSV file.
```
PS C:\> Get-AIPFileStatus -Path \\finance\projects\ | Export-Csv c:\reports\AIP-status.csv 
```

This example provides the label and protection information about all files under the projects folder (and its entire subfolders) in the finance server. The results are exported to AIP-status.CSV

### Example 3: List all “Confidential” files that are stored in a specific folder. Export the results to a CSV file.
```
PS C:\> Get-AIPFileStatus -Path \\finance\projects\ | Where-Object {$_.MainLabelName -eq 'Confidential'} | Export-Csv c:\reports\AIP-status.csv
```

This example provides information about all Confidential files stored in the “projects” folder (and its entire subfolders) in the finance server. The results are exported to AIP-status.CSV

### Example 4: Count how many "Confidential" files are stored in a folder.
```
PS C:\> (Get-AIPFileStatus -Path c:\projects\ | Where-Object {$_.MainLabelName -eq 'Confidential'}).Count
```

This example provides the number of all "Confidential" files stored in the c:\projects folder (and its entire subfolders) 

## PARAMETERS

### -Path
Specifies a local or network path to one or more locations. (examples: c:\folder\ c:\folder\filename, \\server\folder). Wildcards are not permitted. 

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

