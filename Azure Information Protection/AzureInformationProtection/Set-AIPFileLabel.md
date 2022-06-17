---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
ms.assetid: 566E595C-D574-4DED-AE38-CBCD75694B45
online version: https://go.microsoft.com/fwlink/?linkid=838766
schema: 2.0.0
---

# Set-AIPFileLabel

## SYNOPSIS
Sets or removes an Azure Information Protection label for a file, and sets or removes the protection according to the label configuration or custom permissions.

## SYNTAX

### SetLabel
```
Set-AIPFileLabel -LabelId <Guid> [-JustificationMessage <String>] [-Owner <String>] [-PreserveFileDetails] [-EnableTracking] [-Path] <String[]> [<CommonParameters>]
```

### SetLabelCustom
```
Set-AIPFileLabel -LabelId <Guid> [-JustificationMessage <String>] -CustomPermissions <AIPCustomPermissions> [-Owner <String>] [-PreserveFileDetails] [-Path] <String[]> [<CommonParameters>]
```

### RemoveLabel
```
Set-AIPFileLabel [-JustificationMessage <String>] [-RemoveLabel] [-PreserveFileDetails] [-Path] <String[]> [<CommonParameters>]
```

### RemoveLabelProtection
```
Set-AIPFileLabel [-JustificationMessage <String>] [-RemoveLabel] [-RemoveProtection] [-PreserveFileDetails] [-Path] <String[]> [<CommonParameters>]
```

### RemoveProtection
```
Set-AIPFileLabel [-JustificationMessage <String>] [-RemoveProtection] [-PreserveFileDetails] [-Path] <String[]> [<CommonParameters>]
```

### Custom
```
Set-AIPFileLabel -CustomPermissions <AIPCustomPermissions> [-Owner <String>] [-PreserveFileDetails] [-Path] <String[]> [<CommonParameters>]
```

## DESCRIPTION
For the AIP unified labeling client, the **Set-AIPFileLabel** cmdlet sets or removes a sensitivity label for one or more files. This action can automatically apply protection when labels are configured to apply encryption. 

Additionally, you can use this cmdlet to apply custom permissions when they are created as an ad-hoc protection policy object with the [New-AIPCustomPermissions](New-AIPCustomPermissions.md) cmdlet. 

When the command runs successfully, any existing label or protection can be replaced.

You can run this cmdlet non-interactively. For more information, see the [Unified labeling client admin guide](/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).

> [!NOTE]
> When running the **Set-AIPFileLabel** cmdlet in a loop, add these two lines after the cmdlet:
> **[GC]::Collect()**<br />
> **[GC]::WaitForPendingFinalizers()** 
> 

## EXAMPLES

### Example 1: Apply the "General" label to all files that do not currently have a label
```
PS C:\> Get-AIPFileStatus -Path \\Finance\Projects\ | where {$_.IsLabeled -eq $False} | Set-AIPFileLabel -LabelId d9f23ae3-4321-4321-4321-f515f824c57b
FileName                              Status Comment
--------                              ------ ------------
\\Finance\Projects\Image.jpg          Success
\\Finance\Projects\Pricelist.pdf      Success
\\Finance\Projects\Announcement.docx  Success
\\Finance\Projects\Analysis.xlsx      Success
```

This command first identifies all files that are not labeled by using the **Get-AIPFileStatus** cmdlet. Then, these files are labeled by specifying the "General" label by its ID.

### Example 2: Apply the "General" label to .docx files that are not labeled
```
PS C:\> Get-ChildItem C:\Projects\*.docx -File -Recurse | Get-AIPFileStatus | where {$_.IsLabeled -eq $False} | Set-AIPFileLabel -LabelId d9f23ae3-1234-1234-1234-f515f824c57b
FileName                   Status  Comment
--------                   ------  ------------
C:\Projects\Analysis.docx  Success
C:\Projects\Projects.docx  Success
```

This command first identifies all **.docx** files in the **C:\Projects** folder (and its subfolders) by using [Get-Child-Item](/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7), then finds from these files the ones that are not labeled by using the **Get-AIPFileStatus** cmdlet. The resulting files are then labeled by specifying the "General" label by its ID.

> [!NOTE]
> This command makes use of the **Path** alias of FullName, so that [Get-Child-Item](/powershell/module/microsoft.powershell.management/get-childitem) can be used with **Get-AIPFileStatus**. 
> 

### Example 3: (Unified labeling client only) Apply the "General" label to all files in a folder and any of its subfolders
```
PS C:\> Set-AIPFileLabel -Path C:\Projects\ -LabelId d9f23ae3-1324-1234-1234-f515f824c57b
FileName                    Status      Comment
--------                    ------      ------------
C:\Projects\Project1.docx   Success
C:\Projects\Datasheet.pdf   Success
C:\Projects\Image.jpg       Success
C:\Projects\Analysis.xlsx   Skipped    No label to apply
C:\Projects\Dashboard.xlsx  Success
```

This command sets a label named "General" on all files in the **Projects** folder and any of its subfolders.

If the General label is configured to apply encryption, the files that were successfully labeled with this command will also be encrypted. In this case, the Rights Management owner (who has the Rights Management Full Control permission) of these files is the user who ran the PowerShell command.

In this example, one file was not labeled (skipped) because it required justification. This might be the intended outcome to ensure that a file with a higher classification label or protection isn't accidentally overwritten with a lower classification label or has protection removed. 

To enable this safeguard, the Office 365 classification label policy must be configured to require justification for removing a label or lowering the classification. When you then run this command without the **JustificationMessage** parameter and the label triggers justification, the file is skipped with the comment "No label to apply". 

### Example 4: (Unified labeling client only) Apply the "General" label to a single file, which requires justification
```
PS C:\> Set-AIPFileLabel -Path \\Finance\Projects\Analysis.xlsx -LabelId d9f23ae3-1324-1234-1234-f515f824c57b -JustificationMessage 'The previous label no longer applies'
FileName                          Status      Comment
--------                          ------      ------------
\\finance\projects\analysis.xlsx  Success
```

This command sets the "General" label for a file that is already labeled with a higher classification label. The Office 365 classification label policy is configured to require justification for removing a label or lowering the classification. Because the command includes a justification message, the new label is successfully applied.

### Example 5: (Unified labeling client only) Remove a label from a file

```
PS C:\> Set-AIPFileLabel C:\Projects\Analysis.docx -RemoveLabel -JustificationMessage 'The previous label no longer applies'

FileName                   Status Comment
--------                   ------ ------------
C:\Projects\Analysis.docx  Success
```

This command removes the existing label from the file named **C:\Projects\Analysis.docx**, and specifies a mandatory justification message.

This justification method is required because the relevant Office 365 classification label policy setting is enabled to require justification for removing a label or lowering the classification.

> [!NOTE]
> If the label you're removing was protecting your file using a template, this command removes both the label and the protection.
>
> If the label you're removing was protecting your file using custom permissions, this command removes only the label.
>



### Example 6: (Unified labeling client only) Protect a file with custom permissions

```
PS C:\> $permissions = New-AIPCustomPermissions -Users user1@contoso.com, user2@vanarsdel.com -Permissions Reviewer -ExpirationDate (Get-Date -Month 1 -Day 1 -Year 2020)
PS C:\> Set-AIPFileLabel C:\Projects\Analysis.docx -CustomPermissions $permissions

FileName                   Status Comment
--------                   ------ ------------
C:\Projects\Analysis.docx  Success
```

The first command creates an ad-hoc protection policy object that grants users from different organizations usage rights from the Reviewer permissions, and also applies an expiration date.

The second command protects a single file named **Analysis.docx** by using the custom permissions in the stored ad-hoc protection policy object.

### Example 7: (Unified labeling client only) Apply a label and custom permissions to file

```
PS C:\> $permissions = New-AIPCustomPermissions -Users a@a.com, b@b.com -Permissions Reviewer 
PS C:\> Set-AIPFileLabel C:\Projects\Analysis.docx -LabelId d9f23ae3-1324-1234-1234-f515f824c57b -CustomPermissions $permissions

FileName                   Status Comment
--------                   ------ ------------
C:\Projects\Analysis.docx  Success
```

The first command creates an ad-hoc protection policy object that grants users from different organizations usage rights from the Reviewer permissions, and also applies an expiration date.

The second command applies a label to a single file named **Analysis.docx** and also protects the file by using the custom permissions in the stored ad-hoc protection policy object. If the label is configured for protection settings, they are replaced by the custom permissions.

### Example 8: (Unified labeling client only) Remove protection from a file 

```
PS C:\> Set-AIPFileLabel C:\Projects\Analysis.docx -RemoveProtection

FileName                   Status Comment
--------                   ------ ------------
C:\Projects\Analysis.docx  Success
```

This command removes protection from a single file named **Analysis.docx**. 

### Example 9: (Unified labeling client only) Remove protection and a label from a file

```
PS C:\> Set-AIPFileLabel C:\Projects\Analysis.docx -RemoveProtection -RemoveLabel -JustificationMessage 'The previous label no longer applies'

FileName                   Status Comment
--------                   ------ ------------
C:\Projects\Analysis.docx  Success
```

This command removes the label and custom protection from a single file named **Analysis.docx**. Because the policy is configured to require justification to remove a label, the justification reason is also supplied so that the command can complete without prompting the user for the reason.



## PARAMETERS

### -CustomPermissions
Specifies the variable name that stores an ad-hoc protection policy, which was created by using the [New-AIPCustomPermissions](./New-AIPCustomPermissions.md) cmdlet. The ad-hoc protection policy is used to protect the file or files with custom permissions.

```yaml
Type: AIPCustomPermissions
Parameter Sets: SetLabelCustom, Custom
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableTracking
Specify this parameter to register a protected document with the document tracking portal. 

The user running this cmdlet and global administrators can then track the protected document and if necessary, revoke it. For more information about the document tracking site, see [Configuring and using document tracking for Azure Information Protection](/azure/information-protection/rms-client/client-admin-guide-document-tracking) from the admin guide. 

If the label does not apply protection, this parameter is ignored.

```yaml 
Type: SwitchParameter 
```


### -JustificationMessage
The justification reason for lowering the classification label, removing a label, or removing protection, if the Azure Information Protection policy requires users to supply this information. If setting a label triggers the justification and this reason is not supplied, the label is not applied. In this case, the status returned is "Skipped" with the comment "Justification required".

```yaml
Type: String
Parameter Sets: SetLabel, SetLabelCustom, RemoveLabel, RemoveLabelProtection, RemoveProtection
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LabelId
Specifies the identity (ID) of the label to apply. When a label has sublabels, always specify the ID of just a sublabel and not the parent label. 

To find the label ID:

The label ID value is not displayed in the Microsoft 365 Compliance center. However, you can use the following Office 365 Security & Compliance Center PowerShell command to find this value: `Get-Label | Format-Table -Property DisplayName, Name, Guid`

For files that have labels applied, you can also run the [Get-AIPFileStatus](./Get-AIPFileStatus.md) cmdlet to identify the label ID (MainLabelId or SubLabelId).


```yaml
Type: Guid
Parameter Sets: SetLabel, SetLabelCustom
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### -Path
Specifies a local path, network path, or SharePoint Server URL to the files for which you want to get the label and protection information. 

Wildcards are not supported and WebDav locations are not supported.

For SharePoint paths, the following are supported:

- SharePoint Server 2019
- SharePoint Server 2016
- SharePoint Server 2013

For example:

- C:\Folder\
- C:\Folder\Filename
- \\\Server\Folder
- http://sharepoint.contoso.com/Shared%20Documents/Folder

Paths can include spaces when you enclose the path value with quotes.

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

### -PreserveFileDetails
Specify this parameter to leave the modified date (Windows and SharePoint) and modified by (SharePoint) values unchanged for documents that you label:

- For local or network files, the **Date modified** value remains unchanged.

- For SharePoint files, the **Modified date** and **Modified by** values remain unchanged.

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

### -RemoveLabel
Removes any label that has been applied to a file.

```yaml
Type: SwitchParameter
Parameter Sets: RemoveLabel, RemoveLabelProtection
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveProtection
**Relevant for:** Unified labeling client only

Removes protection from a file. If the file is labeled, the label is not removed.

You must have sufficient usage rights or be a super user for your organization to remove protection from files. For more information, see [Configuring super users for Azure Rights Management and discovery services or data recovery](/azure/information-protection/configure-super-users).

Use the **Set-AIPFileLabel** PowerShell cmdlet to enable removal of protection from container files (**zip**, **.rar**, **.7z**, and **.pst**).

> [!NOTE]
> - This remove protection capability is disabled by default and must first be enabled using the [Set-LabelPolicy](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#enable-removal-of-protection-from-compressed-files) cmdlet.
>
> - For .pst files, 5 GB is the maximum file size supported with this cmdlet.
>

```yaml
Type: SwitchParameter
Parameter Sets: RemoveLabelProtection, RemoveProtection
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. 

For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

### System.String[]

## OUTPUTS

### Microsoft.InformationProtection.Powershell.AIP.Results.SetAIPFileResult

## NOTES

## RELATED LINKS

[Get-AIPFileStatus](./Get-AIPFileStatus.md)

[New-AIPCustomPermissions](./New-AIPCustomPermissions.md)

[Set-AIPFileClassification](./Set-AIPFileClassification.md)

[Set-AIPAuthentication](./Set-AIPAuthentication.md)
