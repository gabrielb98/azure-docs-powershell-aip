---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=838766
schema: 2.0.0
---

# Set-AIPPolicy

## SYNOPSIS
Sets an Azure Information Protection label for a file, according to the file content, and sets the protection according to the label configuration.

## SYNTAX

```
Set-AIPPolicy [-JustificationMessage <String>] [-Force] [-ApplyRecommended] [-Path] <String[]>
```

## DESCRIPTION
The Set-AIPPolicy cmdlet sets or removes an Azure Information Protection label for one or more files, according to the file content, applying the rules present in the policy.
This action can automatically apply or remove protection when labels are configured for Rights Management protection in the Azure Information Protection policy.
When the command runs successfully, any existing label or protection is replaced.

Currently, you cannot create or edit labels by using PowerShell but must do this by using the Azure portal.
For instructions, see Configuring Azure Information Protection policy (https://docs.microsoft.com/information-protection/deploy-use/configure-policy).

In addition, this cmdlet does not support a service principal account in Azure Active Directory; you must run it interactively with a user account.

## EXAMPLES

### Example 1: Sets labels to all files in a folder and any of its subfolders, according to a files content.
```
PS C:\> Set-AIPPolicy -Path C:\Projects\


FileName      : C:\Projects\Project1.docx
Status        : Success
Comment       :
MainLabelName : Confidential
MainLabelId   : 074e257c-1234-1234-1234-34a182080e71
SubLabelName  : Finance group
SubLabelId    : d9f23ae3-1234-1234-1234-f515f824c57b

FileName      : C:\Projects\Datasheet.pdf
Status        : Success
Comment       :
MainLabelName : 
MainLabelId   : 
SubLabelName  : 
SubLabelId    : 

FileName      : C:\Projects\Analysis.xlsx
Status        : Skipped
Comment       : This file already has labels
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

This command sets a label on all files in the Projects folder and any of its subfolders, according to the content of the file.

If the set label is configured in the Azure Information Protection policy to apply Rights Management protection, the files that were successfully labeled with this command will also be protected.
In this case, the Rights Management owner (who has the Rights Management Full Control permission) of these files is the user who ran the PowerShell command.

### Example 2: Sets labels to all files in a folder and any of its subfolders, according to a files content, applying recommended labeling, and overriding existing labels.
```
PS C:\> Set-AIPPolicy -Path C:\Projects\ -Force


FileName      : C:\Projects\Project1.docx
Status        : Success
Comment       :
MainLabelName : Confidential
MainLabelId   : 074e257c-1234-1234-1234-34a182080e71
SubLabelName  : Finance group
SubLabelId    : d9f23ae3-1234-1234-1234-f515f824c57b

FileName      : C:\Projects\Datasheet.pdf
Status        : Success
Comment       :
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

FileName      : C:\Projects\Dashboard.xlsx
Status        : Success
Comment       : This file already has labels
MainLabelName : Public
MainLabelId   : f018e9e7-0cfc-4c69-b27a-ac3cb7df43cc
SubLabelName  : 
SubLabelId    :
```

This command sets a label on all files in the Projects folder and any of its subfolders, according to the content of the file.

If the set label is configured in the Azure Information Protection policy to apply Rights Management protection, the files that were successfully labeled with this command will also be protected.
In this case, the Rights Management owner (who has the Rights Management Full Control permission) of these files is the user who ran the PowerShell command.

## PARAMETERS

### -ApplyRecommended
Sets a labeld which the policy rules would recommend.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
Applies the label which the policy sets, regardless of current existing labels on the file.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -JustificationMessage
The justification reason for lowering the classification label, removing a label, or removing protection, if the Azure Information Protection policy requires users to supply this information.
If setting a label triggers the justification and this reason is not supplied, the label is not applied, even if the policy doesn't suggest any label for this file content, and the Force paramter was set.
In this case, the status returned is "Skipped" with the comment "Justification required".

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
Examples include C:\Folder\, C:\Folder\Filename, \Server\Folder).
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

## INPUTS

### System.String[]

## OUTPUTS

### Microsoft.InformationProtection.Powershell.AIP.Results.SetAIPPolicyResult

## NOTES

## RELATED LINKS

