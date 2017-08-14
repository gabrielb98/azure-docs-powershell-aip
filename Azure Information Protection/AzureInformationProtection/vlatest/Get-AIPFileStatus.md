---
external help file: AIP.dll-Help.xml
ms.assetid: ED3F3730-434E-4EDF-969B-0ABE30D68030
online version: https://go.microsoft.com/fwlink/?linkid=838765
schema: 2.0.0
---

# Get-AIPFileStatus

## SYNOPSIS
Gets the Azure Information Protection label and protection information for a specified file or files.

## SYNTAX

```
Get-AIPFileStatus [-Path] <String[]> [<CommonParameters>]
```

## DESCRIPTION
The **Get-AIPFileStatus** cmdlet returns the Azure Information Protection status of a specified file or all files in a specified path. This status includes whether the file has a label, and if it does, the label name, who applied it, how it was applied, and when. In addition, the status includes whether the file is protected by Rights Management, and if it is, what Rights Management template was used to apply this protection.  

Note that password-protected files always return the protection status of **False**.

This cmdlet does not support a service principal account in Azure Active Directory; you must run it interactively with a user account. 

Note: You can run this cmdlet non-interactively with the preview version of the Azure Information Protection client. For more information, see [How to label files non-interactively for Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection) from the admin guide.

## EXAMPLES

### Example 1: Get the label and protection status of a single file
```
PS C:\> Get-AIPFileStatus -Path \\Finance\Projects\Project.docx
FileName        : \\Finance\Projects\Project.docx
IsLabeled       : True
MainLabelId     : 074e257c-1234-1234-1234-34a182080e71
MainLabelName   : Confidential
SubLabelId      : d9f23ae3-1234-1234-1234-f515f824c57b
SubLabelName    : Finance group
LabelingSiteId  : 72f988bf-1234-1234-1234-2d7cd011db47
Owner           : John@Contoso.com
LabelingMethod  : Manual
LabelDate       : 12/12/2016 12:24:36 PM
IsRMSProtected  : True
RMSTemplateId   : e6ee2481-1234-1234-1234-f744eacd53b0
RMSTemplateName : Contoso - Confidential Finance
```

This command provides information about a file that is labeled as Confidential \ Finance Group. This file was labeled manually by John and it is also protected by using the Rights Management template, "Contoso - Confidential Finance". 

### Example 2: Get the label and protection status for all files in a  folder and export the results to a CSV file
```
PS C:\> Get-AIPFileStatus -Path \\Finance\Projects\ | Export-Csv C:\Reports\AIP-status.csv
```

This command gets the label and protection information of all files on the Finance server, in the Projects folder and any of its subfolders. The results are exported to the file named AIP-status.csv so that they can be more easily searched and sorted. If a previous report exists in C:\Reports\Report.csv, it will be overwritten.

### Example 3: List the files labeled "Confidential" and export the results to a CSV file
```
PS C:\> Get-AIPFileStatus -Path \\Finance\Projects\ | Where-Object {$_.MainLabelName -eq 'Confidential'} | Export-Csv C:\Reports\AIP-status.csv
```

This command gets the label and protection information for just the files that are labeled "Confidential" (regardless of their sub-label) on the Finance server, in the Projects folder and any of its subfolders. The results are exported to the file named AIP-status.csv so that they can be more easily searched and sorted. If a previous report exists in C:\Reports\Report.csv, it will be overwritten.

### Example 4: Count of files with a "Confidential" label
```
PS C:\> (Get-AIPFileStatus -Path C:\Projects\ | Where-Object {$_.MainLabelName -eq 'Confidential'}).Count
5
```

This command provides the number of files with the "Confidential" label that are in the C:\Projects folder and any of its subfolders. In this example, 5 files are found.

## PARAMETERS

### -Path
Specifies a local path, network path, or SharePoint URL to the files for which you want to get the label and protection information. Wildcards are not supported.

Examples include C:\Folder\, C:\Folder\Filename, \\\Server\Folder, http://sharepoint.contoso.com/Shared%20Documents/Folder. Paths can include spaces when you enclose the path value with quotes.

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

[Set-AIPAuthentication](./Set-AIPAuthentication.md)

[Set-AIPFileClassification](./Set-AIPFileClassification.md)

[Set-AIPFileLabel](./Set-AIPFileLabel.md)

[Get-RMSTemplate](./Get-RMSTemplate.md)

