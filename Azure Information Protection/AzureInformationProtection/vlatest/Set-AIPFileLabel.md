---
external help file: AIP.dll-Help.xml
ms.assetid: 566E595C-D574-4DED-AE38-CBCD75694B45
online version: https://go.microsoft.com/fwlink/?linkid=838766
schema: 2.0.0
---

# Set-AIPFileLabel

## SYNOPSIS
Sets or removes an Azure Information Protection label for a file, and sets the protection according to the label configuration.

## SYNTAX

### Set
```
Set-AIPFileLabel [-LabelId] <Guid> [-JustificationMessage <String>] [-Owner <String>] [-PreserveFileDetails]
 [-Path] <String[]> [<CommonParameters>]
```

### Clear
```
Set-AIPFileLabel [-JustificationMessage <String>] [-RemoveLabel] [-Owner <String>] [-PreserveFileDetails]
 [-Path] <String[]> [<CommonParameters>]
```

## DESCRIPTION
The **Set-AIPFileLabel** cmdlet sets or removes an Azure Information Protection label for one or more files. This action can automatically apply or remove protection when labels are configured for Rights Management protection in the Azure Information Protection policy. When the command runs successfully, any existing label or protection is replaced.

Currently, you cannot create or edit labels by using PowerShell but must do this by using the Azure portal. For instructions, see [Configuring Azure Information Protection policy](https://docs.microsoft.com/information-protection/deploy-use/configure-policy).

In addition, this cmdlet does not support a service principal account in Azure Active Directory; you must run it interactively with a user account. However, you can run it concurrently.

Note: You can run this cmdlet non-interactively with the preview version of the Azure Information Protection client. For more information, see [How to label files non-interactively for Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection) from the admin guide.


## EXAMPLES

### Example 1: Apply the "General" sub-label to all files in a folder and any of its subfolders
```
PS C:\> Set-AIPFileLabel -Path C:\Projects\ -LabelId d9f23ae3-1324-1234-1234-f515f824c57b
FileName                    Status      Comment
--------                    ------      ------------
C:\Projects\Project1.docx   Success
C:\Projects\Datasheet.pdf   Success
C:\Projects\Image.jpg       Success
C:\Projects\Analysis.xlsx   Skipped    Justification required
C:\Projects\Dashboard.xlsx  Success
```

This command sets a label named "General" on all files in the Projects folder and any of its subfolders.

If the General label is configured in the Azure Information Protection policy to apply Rights Management protection, the files that were successfully labeled with this command will also be protected. In this case, the Rights Management owner (who has the Rights Management Full Control permission) of these files is the user who ran the PowerShell command.

In this example, one file was not labeled (skipped) with the comment that justification is required. This might be the intended outcome to ensure that a file with a higher classification label or protection isn't accidentally overwritten with a lower classification label or has protection removed. To enable this safeguard, the Azure Information Protection policy must be configured to require justification for lowering the classification label, removing a label, or removing protection. When you then run this command without the **JustificationMessage** parameter and the label triggers justification, the file is skipped. 

### Example 2: Apply the "General" label to a single file, which requires justification
```
PS C:\> Set-AIPFileLabel -Path \\Finance\Projects\Analysis.xlsx -LabelId d9f23ae3-1324-1234-1234-f515f824c57b -JustificationMessage 'The previous label no longer applies'
FileName                          Status      Comment
--------                          ------      ------------
\\finance\projects\analysis.xlsx  Success
```

This command sets the "General" label for a file that is already labeled with a higher classification label. The Azure Information Protection policy is configured to require justification for lowering the classification label, removing a label, or removing protection. Because the command includes a justification message, the new label is successfully applied and the justification reason is logged on the local computer.

### Example 3: Apply the "General" label to all files that do not currently have a label
```
PS C:\> Get-AIPFileStatus -Path \\Finance\Projects\ | where {$_.IsLabeled -eq $False} | Set-AIPFileLabel -LabelId d9f23ae3-4321-4321-4321-f515f824c57b
FileName                              Status Comment
--------                              ------ ------------
\\Finance\Projects\Image.jpg          Success
\\Finance\Projects\Pricelist.pdf      Success
\\Finance\Projects\Announcement.docx  Success
\\Finance\Projects\Analysis.xlsx      Success
```

This command first identifies all files that are not labeled by using the Get-AIPFileStatus cmdlet. Then, these files are labeled by specifying the "General" label by its ID.

### Example 4: Apply the "General" label to .docx files that are not labeled
```
PS C:\> Get-ChildItem C:\Projects\*.docx -File -Recurse | Get-AIPFileStatus | where {$_.IsLabeled -eq $False} | Set-AIPFileLabel -LabelId d9f23ae3-1234-1234-1234-f515f824c57b
FileName                   Status  Comment
--------                   ------  ------------
C:\Projects\Analysis.docx  Success
C:\Projects\Projects.docx  Success
```

This command first identifies all .docx files in the C:\Projects folder (and its subfolders) by using Get-Child-Item, then finds from these files the ones that are not labeled by using the Get-AIPFileStatus cmdlet. The resulting files are then labeled by specifying the "General" label by its ID.

Note: This command makes use of the Path alias of FullName, so that Get-Child-Item can be used with Get-AIPFileStatus. 

### Example 5: Remove a label from a file
```
PS C:\> Set-AIPFileLabel C:\Projects\Analysis.docx -RemoveLabel -JustificationMessage 'The previous label no longer applies'

FileName                   Status Comment
--------                   ------ ------------
C:\Projects\Analysis.docx  Success
```

This command removes the existing label from the file named C:\Projects\Analysis.docx, and specifies a justification message that is required because the Azure Information Protection policy setting is enabled that requires justification for lowering the classification label, removing a label, or removing protection. 

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

The label ID value is displayed in the Azure portal, on the Label blade, when you view or configure the Azure Information Protection policy. For files that have labels applied, you can also run the [Get-AIPFileStatus](./Get-AIPFileStatus.md) cmdlet to identify the label ID (MainLabelId or SubLabelId).


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

### -RemoveLabel
Removes any label that has been applied to a file.

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

### -Owner
Specify the email address that is written to the Owner custom property.

Note: This parameter requires the preview version of the Azure Information Protection client.

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

Note: This cmdlet requires the preview version of the Azure Information Protection client.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String[]

## OUTPUTS

### Microsoft.InformationProtection.Powershell.AIP.Results.SetAIPFileResult

## NOTES

## RELATED LINKS

[Get-AIPFileStatus](./Get-AIPFileStatus.md)

[Set-AIPFileClassification](./Set-AIPFileClassification.md)