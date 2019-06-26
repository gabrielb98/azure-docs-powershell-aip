---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
ms.assetid: ed1080cd-ae6f-4720-bac7-e719e31c708b
online version: https://go.microsoft.com/fwlink/?linkid=845215
schema: 2.0.0
---

# Set-AIPFileClassification

## SYNOPSIS
Scans a file to automatically set an Azure Information Protection label for a file, according to conditions that are configured in the policy.

## SYNTAX

### ApplyChanges
```
Set-AIPFileClassification [-JustificationMessage <String>] [-Force] [-PreserveFileDetails] [-Path] <String[]>
 [<CommonParameters>]
```

### WhatIf
```
Set-AIPFileClassification [-JustificationMessage <String>] [-Force] [-WhatIf] [-DiscoveryInfoTypes <String[]>]
 [-Path] <String[]> [<CommonParameters>]
```

## DESCRIPTION
The Set-AIPFileClassification cmdlet can automatically apply a label for one or more files when you configure labels for automatic classification. For more information, see the following:

- For the Azure Information Protection client: [How to configure conditions for automatic and recommended classification for Azure Information Protection](https://docs.microsoft.com/information-protection/configure-policy-classification).

- For the Azure Information Protection unified labeling client: [Apply a sensitivity label to content automatically](https://docs.microsoft.com/Office365/SecurityCompliance/apply_sensitivity_label_automatically).

When this cmdlet is run, it inspects the file contents and if the configured conditions are met for a label, that label is applied. This action will automatically apply protection if the selected label applies protection. For the Azure Information Protection client, because labels support removing protection, protection can also be removed from files when you run this cmdlet.

By default, if the file already has a label, the existing label or protection is not replaced.

For both clients, you can run this cmdlet non-interactively. For instructions, see the following documentation in the admin guides:

- Azure Information Protection client: [How to label files non-interactively for Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).

- Azure Information Protection unified labeling client: [How to label files non-interactively for Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).

NOTE: When you run this cmdlet with the Azure Information Protection unified labeling client, there are differences from the Azure Information Protection client:

- The *Owner* parameter is not supported.

- SharePoint Server paths are not supported.

- When a file isn't labeled because it was manually labeled, there was no match for the conditions that you specified, or the file had a higher classification, the file is skipped with the single comment of "No label to apply".

- The *WhatIf* parameter is supported. You can use the WhatIf mode with *DiscoveryInfoTypes* to find known sensitive information types.

## EXAMPLES

### Example 1a: Scan all files in a folder and any of its subfolders, and apply labels according to the configured conditions for automatic classification - Azure Information Protection client only
```
PS C:\> Set-AIPFileClassification -Path C:\Projects\ -PreserveFileDetails


FileName      : C:\Projects\Project1.docx
Status        : Success
Comment       :
MainLabelName : Confidential
MainLabelId   : 074e257c-1234-1234-1234-34a182080e71
SubLabelName  : Finance group
SubLabelId    : d9f23ae3-1234-1234-1234-f515f824c57b

FileName      : C:\Projects\Datasheet.pdf
Status        : Skipped
Comment       : No conditions match for this file
MainLabelName : 
MainLabelId   : 
SubLabelName  : 
SubLabelId    : 

FileName      : C:\Projects\Analysis.xlsx
Status        : Skipped
Comment       : The file is labeled manually
MainLabelName : 
MainLabelId   : 
SubLabelName  : 
SubLabelId    : 

FileName      : C:\Projects\Pricelist.xlsx
Status        : Skipped
Comment       : The file has a higher classification label
MainLabelName : 
MainLabelId   : 
SubLabelName  : 
SubLabelId    : 

FileName      : C:\Projects\Dashboard.xlsx
Status        : Success
Comment       : 
MainLabelName : Public
MainLabelId   : f018e9e7-0cfc-4c69-b27a-ac3cb7df43cc
SubLabelName  : 
SubLabelId    :
```

This command scans all files in the Projects folder and any of its subfolders, and sets labels according to the configured conditions in the Azure Information Protection policy. In this example, there are five files and two files are automatically labeled. The Datasheet.pdf file is not labeled because its contents does not match the configured conditions for automatic classification Analysis.xlsx was already manually labeled, and Pricelist.xlsx has a higher label. Because the command is run without the *-Force* parameter, the existing labels for Analysis.xlsx and Pricelist.xlsx are not overwritten.

If the applied labels are also configured to apply Rights Management protection, the files that are successfully labeled with this command are also protected. In this case, the Rights Management owner (who has the Rights Management Full Control permission) of these files is the user who ran the PowerShell command.

Because the PreserveFileDetails parameter is specified, the Date Modified of the labeled files remains unchanged.

### Example 1b: Scan all files in a folder and any of its subfolders, and apply labels according to the configured conditions for automatic classification - Azure Information Protection unified labeling client only
```
PS C:\> Set-AIPFileClassification -Path C:\Projects\ -PreserveFileDetails


FileName      : C:\Projects\Project1.docx
Status        : Success
Comment       :
MainLabelName : Confidential
MainLabelId   : 074e257c-1234-1234-1234-34a182080e71
SubLabelName  : Finance group
SubLabelId    : d9f23ae3-1234-1234-1234-f515f824c57b

FileName      : C:\Projects\Datasheet.pdf
Status        : Skipped
Comment       : No label to apply
MainLabelName : 
MainLabelId   : 
SubLabelName  : 
SubLabelId    : 

FileName      : C:\Projects\Analysis.xlsx
Status        : Skipped
Comment       : No label to apply
MainLabelName : 
MainLabelId   : 
SubLabelName  : 
SubLabelId    : 

FileName      : C:\Projects\Pricelist.xlsx
Status        : Skipped
Comment       : No label to apply
MainLabelName : 
MainLabelId   : 
SubLabelName  : 
SubLabelId    : 

FileName      : C:\Projects\Dashboard.xlsx
Status        : Success
Comment       : 
MainLabelName : Public
MainLabelId   : f018e9e7-0cfc-4c69-b27a-ac3cb7df43cc
SubLabelName  : 
SubLabelId    :
```

This command scans all files in the Projects folder and any of its subfolders, and sets labels according to the configured conditions in the auto labeling policy. In this example, there are five files and two files are automatically labeled. The Datasheet.pdf file is not labeled because its contents does not match the configured conditions for automatic classification Analysis.xlsx was already manually labeled, and Pricelist.xlsx has a higher label. Because the command is run without the *-Force* parameter, the existing labels for Analysis.xlsx and Pricelist.xlsx are not overwritten.

If the applied labels are also configured to apply Rights Management protection, the files that are successfully labeled with this command are also protected. In this case, the Rights Management owner (who has the Rights Management Full Control permission) of these files is the user who ran the PowerShell command.

Because the PreserveFileDetails parameter is specified, the Date Modified of the labeled files remains unchanged.


### Example 2a: Scan all files in a folder and any of its subfolders, and apply labels according to the configured conditions for automatic classification, overriding any existing labels - Azure Information Protection client only

```
PS C:\> Set-AIPFileClassification -Path C:\Projects\ -Force -PreserveFileDetails


FileName      : C:\Projects\Project1.docx
Status        : Success
Comment       :
MainLabelName : Confidential
MainLabelId   : 074e257c-1234-1234-1234-34a182080e71
SubLabelName  : Finance group
SubLabelId    : d9f23ae3-1234-1234-1234-f515f824c57b

FileName      : C:\Projects\Datasheet.pdf
Status        : Skipped
Comment       : No conditions match for this file
MainLabelName : 
MainLabelId   : 
SubLabelName  : 
SubLabelId    : 

FileName      : C:\Projects\Analysis.xlsx
Status        : Success
Comment       :
MainLabelName : Public
MainLabelId   : f018e9e7-0cfc-4c69-b27a-ac3cb7df43cc
SubLabelName  : 
SubLabelId    : 

FileName      : C:\Projects\Pricelist.xlsx
Status        : Success
Comment       :
MainLabelName : Public
MainLabelId   : f018e9e7-0cfc-4c69-b27a-ac3cb7df43cc
SubLabelName  : 
SubLabelId    : 

FileName      : C:\Projects\Dashboard.xlsx
Status        : Success
Comment       : 
MainLabelName : Public
MainLabelId   : f018e9e7-0cfc-4c69-b27a-ac3cb7df43cc
SubLabelName  : 
SubLabelId    :
```

This command is similar to the previous example in that it also scans all files in the Projects folder and any of its subfolders, and sets labels according to the configured conditions in the Azure Information Protection policy. However, this time, because the command includes the *-Force* parameter, it also replaces the existing label for Dashboard.xlsx, and Pricelist.xlsx. 

The contents of Datasheet.pdf did not match any configured conditions and this file remains without a label.

### Example 2b: Scan all files in a folder and any of its subfolders, and apply labels according to the configured conditions for automatic classification, overriding any existing labels - Azure Information Protection unified labeling client only

```
PS C:\> Set-AIPFileClassification -Path C:\Projects\ -Force -PreserveFileDetails


FileName      : C:\Projects\Project1.docx
Status        : Success
Comment       :
MainLabelName : Confidential
MainLabelId   : 074e257c-1234-1234-1234-34a182080e71
SubLabelName  : Finance group
SubLabelId    : d9f23ae3-1234-1234-1234-f515f824c57b

FileName      : C:\Projects\Datasheet.pdf
Status        : Skipped
Comment       : No label to apply
MainLabelName : 
MainLabelId   : 
SubLabelName  : 
SubLabelId    : 

FileName      : C:\Projects\Analysis.xlsx
Status        : Success
Comment       :
MainLabelName : Public
MainLabelId   : f018e9e7-0cfc-4c69-b27a-ac3cb7df43cc
SubLabelName  : 
SubLabelId    : 

FileName      : C:\Projects\Pricelist.xlsx
Status        : Success
Comment       :
MainLabelName : Public
MainLabelId   : f018e9e7-0cfc-4c69-b27a-ac3cb7df43cc
SubLabelName  : 
SubLabelId    : 

FileName      : C:\Projects\Dashboard.xlsx
Status        : Success
Comment       : 
MainLabelName : Public
MainLabelId   : f018e9e7-0cfc-4c69-b27a-ac3cb7df43cc
SubLabelName  : 
SubLabelId    :
```

This command is similar to the previous example in that it also scans all files in the Projects folder and any of its subfolders, and sets labels according to the configured conditions for auto labeling. However, this time, because the command includes the *-Force* parameter, it also replaces the existing label for Dashboard.xlsx, and Pricelist.xlsx. 

The contents of Datasheet.pdf did not match any configured conditions and this file remains without a label.

### Example 3: Scan a file in WhatIf mode for all known sensitive information types - Azure Information Protection unified labeling client only

```
PS C:\> Set-AIPFileClassification -Path C:\Projects\Project1.docx -WhatIf -DiscoveryInfoTypes All


MainLabelName           : General
MainLabelId             : 89a453df-5df4-4976-8191-jdn2fsf9560a
SubLabelName            :
SubLabelId              :
WhatIf                  : True
MatchedInformationTypes : {Credit Card Number, U.S. Social Security Number (SSN), International Classification of
                          Diseases (ICD-10-CM), International Classification of Diseases (ICD-9-CM)}
LastModifiedBy          :
LastModifiedTime        : 8/19/2014 5:11:26 AM
FileName                : C:\Projects\Project1.docx
Status                  : Success
Comment                 :
```

This command discovers all known information types in Project1.docx file without applying protection or a label.

### Example 4: Scan a file in WhatIf mode for specific sensitive information types - Azure Information Protection unified labeling client only

```
PS C:\> Set-AIPFileClassification -Path C:\Projects\Project1.docx -WhatIf -DiscoveryInfoTypes "50842eb7-edc8-4019-85dd-5a5c1f2bb085","a44669fe-0d48-453d-a9b1-2cc83f2cba77"

MainLabelName           : General
MainLabelId             : 89a453df-5df4-4976-8191-jdn2fsf9560a
SubLabelName            :
SubLabelId              :
WhatIf                  : True
MatchedInformationTypes : {Credit Card Number, U.S. Social Security Number (SSN)}
LastModifiedBy          :
LastModifiedTime        : 8/19/2014 5:11:26 AM
FileName                : Project1.docx
Status                  : Success
Comment                 :

```

This command discovers the specific information types of "Credit Card Number", and "Social Security Number (SSN)" in Project1.docx file without applying protection or a label.


### Example 5: Scan a file in WhatIf mode for specific sensitive information types and display the values found - Azure Information Protection unified labeling client only

```
PS C:\> $x=Set-AIPFileClassification -Path "C:\Projects\Project1.docx" -WhatIf -DiscoveryInfoTypes "50842eb7-edc8-4019-85dd-5a5c1f2bb085","a44669fe-0d48-453d-a9b1-2cc83f2cba77"
PS C:\> $x.MatchedInformationTypes

RulePackageSetId  : 00000000-0000-0000-0000-000000000000
RulePackageId     : 00000000-0000-0000-0000-000000000000
RuleId            : 50842eb7-edc8-4019-85dd-5a5c1f2bb085
Name              : Credit Card Number
Count             : 1
UniqueCount       : 1
Confidence        : 85
SensitiveContents : {Offset: 2089, Length: 19}
 
RulePackageSetId  : 00000000-0000-0000-0000-000000000000
RulePackageId     : 00000000-0000-0000-0000-000000000000
RuleId            : a44669fe-0d48-453d-a9b1-2cc83f2cba77
Name              : U.S. Social Security Number (SSN)
Count             : 1
UniqueCount       : 1
Confidence        : 85
SensitiveContents : {Offset: 7063, Length: 11}


PS C:\> $x.MatchedInformationTypes[0].SensitiveContents | fl

Offset  : 2089
Length  : 19
Value   : 4539-9572-7949-2212
Context : OLOGICAL SCIENCES     Credit Card #
          Expiration Date:      4539-9572-7949-2212
          8/2009                Department:     BIOLOGICAL SCIENCES     Anticipa
```

Similar to the previous example, the first command discovers the specific information types of "Credit Card Number", and "Social Security Number (SSN)" in Project1.docx file without applying protection or a label. However, in this example, the results are stored in a variable for further processing.

The second command is then used to display the contents of the matched information types, which includes the SensitiveContents parameter.

The final command displays and formats for easier reading the data that's identified by the first sensitive information type, which in this example, is the credit card details.

## PARAMETERS

### -DiscoveryInfoTypes
Note: This parameter is supported only with the Azure Information Protection unified labeling client.

Specify the sensitive information types to be discovered when you use the *WhatIf* parameter.

If you want to search for specific sensitive information types, specify the **Entity id** number for that information type, which you can find listed in [Sensitive information types in Exchange Server](https://docs.microsoft.com/Exchange/policy-and-compliance/data-loss-prevention/sensitive-information-types?view=exchserver-2019). For example, "50842eb7-edc8-4019-85dd-5a5c1f2bb085" is the number to specify for the Credit Card Number sensitive information type.

```yaml
Type: String[]
Parameter Sets: WhatIf
Accepted values: All, "rule_id_1", "rule_id_2"
Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
Replaces an existing label when the configured conditions apply.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JustificationMessage
The justification reason for lowering the classification label, removing a label, or removing protection, if the Azure Information Protection policy requires users to supply this information.

If setting a label triggers the justification and this reason is not supplied, the label is not applied, even if the *-Force* parameter is set. In this case, the status returned is "Skipped" with the comment "Justification required" for the Azure Information Protection client, and "No label to apply" for the Azure Information Protection unified labeling client.

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

### -Path
Note: For the Azure Information Protection unified labeling client, SharePoint Server paths are not supported.

Specifies a local path, network path, or SharePoint Server URL to the files for which you want to get the label and protection information.

Wildcards are not supported and WebDav locations are not supported.

For SharePoint paths: SharePoint Server 2019, SharePoint Server 2016, and SharePoint Server 2013 are supported.

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

### -Owner
Note: This parameter is not supported with the Azure Information Protection unified labeling client.

Specify the email address that is written to the Owner custom property. 


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

### -PreserveFileDetails
Specify this parameter to leave the date unchanged for documents that you label.

For local or network files, the Last Modified date remains unchanged.

For SharePoint files, the Modified date and Modified By date remains unchanged.


```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Note: This parameter is supported only with the Azure Information Protection unified labeling client.

Shows what would happen if the cmdlet runs, and is the equivalent of the discovery mode for the scanner. Changes will not apply on input or output files.

Use this parameter with *DiscoveryInfoTypes* to look for all sensitive information types, or specific sensitive information types.

```yaml
Type: SwitchParameter
Parameter Sets: WhatIf
Aliases:

Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String[]

## OUTPUTS

### Microsoft.InformationProtection.Powershell.AIP.Results.SetAIPFileClassificationResult

## NOTES

## RELATED LINKS

[Get-AIPFileStatus](./Get-AIPFileStatus.md)

[Set-AIPAuthentication](./Set-AIPAuthentication.md)

[Set-AIPFileLabel](./Set-AIPFileLabel.md)

