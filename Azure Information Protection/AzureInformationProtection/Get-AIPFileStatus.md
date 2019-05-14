---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
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
The **Get-AIPFileStatus** cmdlet returns the Azure Information Protection status of a specified file or all files in a specified path. This status includes whether the file has a label, and if it does, the label name, who applied it, how it was applied, and when. 

The status also includes whether the file is protected by Rights Management, and if it is, what Rights Management template was used to apply this protection. If the file was protected with custom permissions (an ad-hoc rights policy) instead of a template, "Restricted Access" is displayed instead of the template name. In addition, the [Rights Management owner and Rights Management issuer](https://docs.microsoft.com/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) is displayed, and when the file was protected.

Note that password-protected files always return the protection status of **False**.

For the Azure Information Protection client, but not the Azure Information Protection unified labeling client, you can run this cmdlet non-interactively. For instructions, see [How to label files non-interactively for Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).

NOTE: If you have the Azure Information Protection unified labeling client, there are other differences from the Azure Information Protection client:

- This cmdlets returns label information from your own tenant only and the *LabelingSiteId* parameter is not displayed in the output.

- The *Owner* and *RMSIssuedTime* parameters are not supported and are not displayed in the output.

- The *LabelingMethod* parameter display the values of **Privileged** or **Standard** instead of **Manual** or **Automatic**:
    
    - **Privileged**: A label was applied by a user and is the equivalent of Manual for the Azure Information Protection client.
    - **Standard**: A label was applied by an auto labeling policy from one of the admin centers, such as the Office 365 Security & Compliance Center, or by a service using a rule. This value is the equivalent to Automatic for the Azure Information Protection client.

## EXAMPLES

### Example 1a: Get the label and protection status of a single file - Azure Information Protection client only

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
RMSIssuedTime   : 5/6/2018 9:15:03 AM
RMSOwner        : John@Contoso.com
RMSIssuer       : John@Contoso.com
```

This command provides information about a file that is labeled as "Confidential \ Finance group". This file was labeled manually by John and it is also protected by using the Rights Management template, "Contoso - Confidential Finance". 

### Example 1b: Get the label and protection status of a single file - Azure Information Protection unified labeling client only

```
PS C:\> Get-AIPFileStatus -Path \\Finance\Projects\Project.docx

FileName        : \\Finance\Projects\Project.docx
IsLabeled       : True
MainLabelId     : 074e257c-1234-1234-1234-34a182080e71
MainLabelName   : Confidential
SubLabelId      : d9f23ae3-1234-1234-1234-f515f824c57b
SubLabelName    : Finance group
LabelingMethod  : Privileged
LabelDate       : 12/12/2016 12:24:36 PM
IsRMSProtected  : True
RMSTemplateId   : e6ee2481-1234-1234-1234-f744eacd53b0
RMSTemplateName : Contoso - Confidential Finance
RMSOwner        : John@Contoso.com
RMSIssuer       : John@Contoso.com
```

This command provides information about a file that is labeled as "Confidential \ Finance group", which is a label that is configured for your tenant. This file was labeled manually by John and it is also protected by using the Rights Management template, "Contoso - Confidential Finance". 

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
Specifies a local path, network path, or SharePoint Server URL to the files for which you want to get the label and protection information. Wildcards are not supported.

For SharePoint paths: SharePoint Server 2016 and SharePoint Server 2013 are supported.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

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

