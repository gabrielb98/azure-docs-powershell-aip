---
external help file: RMSProtection.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=734985
schema: 2.0.0
---

# Get-AIPFileStatus

## SYNOPSIS
Gets the AIP status of a specified file, or of files in a specified folder.

## SYNTAX

```
Get-AIPFileStatus [-Path] <String[]> [<CommonParameters>]
```

## DESCRIPTION
The **Get-AIPFileStatus** cmdlet returns the AIP status, which consists of the RMS status (whether the file has RMS protection and if relevant the RMS template information)
as well as the Labeling status (whether the file is labeled, and the file labels) of a specified file.

## EXAMPLES

### Example 1 Get the status of a single file.
```
PS C:\> Get-AIPFileStatus C:\Test.docx
FileName        : C:\Test.docx
IsLabelled      : True
MainLabelId     : 074e257c-5848-4582-9a6f-34a182080e71
MainLabelName   : Confidential
SubLabelId      : d9f23ae3-a239-45ea-bf23-f515f824c57b
SubLabelName    : Microsoft FTE
LabelingRef     : https://api.informationprotection.azure.com/api/72f988bf-86f1-41af-91ab-2d7cd011db47
LabeledBy       : daschuld@microsoft.com
LabelingMethod  : Manual
LabelDate       : 12/20/2016 2:51:29 PM
IsRMSProtected  : True
RMSTemplateId   : e6ee2481-26b9-45e5-b34a-f744eacd53b0
RMSTemplateName : Contoso, Ltd - Confidential View Only
```

This command gets the AIP status of the file Test.docx. This file has a main lable Confidential, and a SubLabel Microsoft FTE. It is RMS protected with the template Contoso, Ltd - Confidential View Only.

### Example 2 Prepare a report of the status of files in a folder.
```
PS C:\> Get-AIPFileStatus \\SharedDrive\SharedFolder\DocsFolder | Export-Csv c:\ReportsFolder\Report.csv -NoTypeInformation
```

This example will prepare a csv report of all files in the DocsFolder of the shared drive. If a previous report exists in c:\ReportsFolder\Report.csv, it will be overwritten.

### Example 3 Count confidential files in a folder.
```
PS C:\> (Get-AIPFileStatus \\SharedDrive\SharedFolder\DocsFolder | Where-Object {$_.MainLabelName -eq 'Confidential'}).Count
```

This example will count all files in the DocsFolder of the shared drive which are labeled as Confidential (regardless of sublabel).

## PARAMETERS

### -Path
Specifies a path to one or more locations. Wildcards are not permitted. Will return AIP status for all files in these locations.

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
