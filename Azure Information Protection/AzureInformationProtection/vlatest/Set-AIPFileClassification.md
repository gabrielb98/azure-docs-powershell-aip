---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=845215
schema: 2.0.0
---

# Set-AIPFileClassification

## SYNOPSIS
Scans a file to automatically set an Azure Information Protection label for a file, according to conditions that are configured in the policy.

## SYNTAX

```
Set-AIPFileClassification [-JustificationMessage <String>] [-Force] [-Path] <String[]> [<CommonParameters>]
```

## DESCRIPTION
The Set-AIPFileClassification cmdlet can automatically apply an Azure Information Protection label for one or more files when you configure labels in your Azure Information Protection policy to use conditions. By default, labels are applied when the conditions are configured for automatic classification, but you can also apply labels that are configured for recommended classification. For more information about conditions, see [How to configure conditions for automatic and recommended classification for Azure Information Protection](/information-protection/deploy-use/configure-policy-classification).

When this cmdlet is run, it inspects the file contents and if the condition is met for a label, that label is applied. This action can automatically apply or remove protection when the applied label is also configured for Rights Management protection in the Azure Information Protection policy.

By default, if the file already has a label, the existing label or protection is not replaced.

Currently, you cannot create or edit labels by using PowerShell but must do this by using the Azure portal. For instructions, see Configuring Azure Information Protection policy (https://docs.microsoft.com/information-protection/deploy-use/configure-policy).

In addition, this cmdlet does not support a service principal account in Azure Active Directory; you must run it interactively with a user account.

NOTE: This cmdlet is currently in preview and is not included in the 1.4.21.0 version of the module. To run this cmdlet, you must install a preview version of the client and the module version number must be at least 1.5.16.0.

## EXAMPLES

### Example 1: Scan all files in a folder and any of its subfolders, and apply labels according to the configured conditions for automatic classification
```
PS C:\> Set-AIPFileClassification -Path C:\Projects\


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

### Example 2: Scan all files in a folder and any of its subfolders, and apply labels according to the configured conditions for automatic or recommended classification, overriding any existing labels
```
PS C:\> Set-AIPFileClassification -Path C:\Projects\ -Force 


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

This command is similar to the previous example in that it also scans all files in the Projects folder and any of its subfolders, and sets labels according to the configured conditions in the Azure Information Protection policy. However, this time, because the command includes the *-Force* parameter, it also replaces the existing label for Dashboard.xlsx, and Pricelist.xlsx. The contents of Datasheet.pdf did not match any configured conditions and this file remains without a label.  

## PARAMETERS

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

If setting a label triggers the justification and this reason is not supplied, the label is not applied, even if the *-Force* paramter is set. In this case, the status returned is "Skipped" with the comment "Justification required".

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
Specifies a local or network path to the file or files to which you want to apply labels. 

Examples include C:\Folder\, C:\Folder\Filename, \\Server\Folder.

Wildcards are not supported.

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

### Microsoft.InformationProtection.Powershell.AIP.Results.SetAIPFileClassificationResult

## NOTES

## RELATED LINKS

