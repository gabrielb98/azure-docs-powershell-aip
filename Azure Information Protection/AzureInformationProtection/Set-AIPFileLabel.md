---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
ms.assetid: 566E595C-D574-4DED-AE38-CBCD75694B45
online version: https://go.microsoft.com/fwlink/?linkid=838766
schema: 2.0.0
---

# Set-AIPFileLabel

## SYNOPSIS
**Relevant for:** AIP unified labeling and classic clients

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
**Unified labeling client support**

For the AIP unified labeling client, the **Set-AIPFileLabel** cmdlet sets or removes a sensitivity label for one or more files. This action can automatically apply protection when labels are configured to apply encryption. 

Additionally, you can use this cmdlet to apply custom permissions when they are created as an ad-hoc protection policy object with the [New-AIPCustomPermissions](New-AIPCustomPermissions.md) cmdlet. 

When the command runs successfully, any existing label or protection can be replaced.

When you run this cmdlet with the Azure Information Protection unified labeling client, there are other differences from the Azure Information Protection client:

- The *Owner* parameter is not supported.

- When a file isn't labeled because it was manually labeled, there was no match for the conditions that you specified, or the file had a higher classification, the file is skipped with the single comment of "No label to apply".


**Classic client support**

For the AIP classic client, the **Set-AIPFileLabel** cmdlet sets or removes an Azure Information Protection label for one or more files. This action can automatically apply or remove protection when labels are configured for protection in the Azure Information Protection policy. When the command runs successfully, any existing label or protection can be replaced.

> [!TIP]
> When using the classic client, you must create and edit labels in the Azure portal. For instructions, see [Configuring the Azure Information Protection policy](/information-protection/configure-policy).
> 

[!INCLUDE [The AIP classic client is deprecated](../includes/classic-client-deprecated.md)]


**Running the cmdlet non-interactively**

For both clients, you can run this cmdlet non-interactively. For instructions, see the relevant admin guide for your client:

- **[Classic client](/information-protection/rms-client/client-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection)**

- **[Unified labeling client](/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection)**


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

This command removes the existing label from the file named **C:\Projects\Analysis.docx**, and specifies a justification message that is required because the Office 365 classification label policy setting is enabled that requires justification for removing a label or lowering the classification. 

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


### Example 10: (Classic client only) Apply the "General" label to all files in a folder and any of its subfolders
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

In this example, one file was not labeled (skipped) with the comment that justification is required. This might be the intended outcome to ensure that a file with a higher classification label or protection isn't accidentally overwritten with a lower classification label or has protection removed. 

To enable this safeguard, the Azure Information Protection policy must be configured to require justification for lowering the classification label, removing a label, or removing protection. When you then run this command without the **JustificationMessage** parameter and the label triggers justification, the file is skipped. 

### Example 11: (Classic client only) Apply the "General" label to a single file, which requires justification
```
PS C:\> Set-AIPFileLabel -Path \\Finance\Projects\Analysis.xlsx -LabelId d9f23ae3-1324-1234-1234-f515f824c57b -JustificationMessage 'The previous label no longer applies'
FileName                          Status      Comment
--------                          ------      ------------
\\finance\projects\analysis.xlsx  Success
```

This command sets the "General" label for a file that is already labeled with a higher classification label. The Azure Information Protection policy is configured to require justification for lowering the classification label, removing a label, or removing protection. Because the command includes a justification message, the new label is successfully applied and the justification reason is logged on the local computer.

### Example 12: (Classic client only) Remove a label from a file

```
PS C:\> Set-AIPFileLabel C:\Projects\Analysis.docx -RemoveLabel -JustificationMessage 'The previous label no longer applies'

FileName                   Status Comment
--------                   ------ ------------
C:\Projects\Analysis.docx  Success
```

This command removes the existing label from the file named **C:\Projects\Analysis.docx**, and specifies a justification message that is required because the Azure Information Protection policy setting is enabled that requires justification for lowering the classification label, removing a label, or removing protection.


### Example 13: (Classic client only) Apply the "Confidential \ All Employees" label to all files in a folder and register these files with the document tracking site

```
PS C:\> Set-AIPFileLabel -Path C:\Projects\ -LabelId ade72bf1-4714-4714-4714-a325f824c55a -EnableTracking 
FileName                    Status      Comment 
--------                    ------      ------------ 
C:\Projects\Project1.docx   Success 
C:\Projects\Project2.docx   Success 
C:\Projects\Project3.docx   Success 
C:\Projects\Project4.docx   Success 
C:\Projects\Datasheet.pdf   Success 
C:\Projects\Image.jpg       Success 
C:\Projects\Dashboard.xlsx  Success
```

 
This command sets a label named "Confidential \ All Employees" on all files in the Projects folder and any of its subfolders. The Label ID specified is for the sublabel "All Employees" that has a parent label of "Confidential". 

If the "Confidential \ All Employees" label applies protection, the files that were successfully labeled with this command will also be protected. Because the *EnableTracking* parameter was specified, the protected documents can now be tracked and revoked in the document tracking site by the person who labeled the document, and by global administrators who use the Administrator mode.

## PARAMETERS

### -CustomPermissions
**Relevant for:** Unified labeling client only

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
**Relevant for:** Classic client only

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

- **For the unified labeling client:** The label ID value is not displayed in the Microsoft 365 Compliance center. However, you can use the following Office 365 Security & Compliance Center PowerShell command to find this value: `Get-Label | Format-Table -Property DisplayName, Name, Guid`

- **For the classic client:** The label ID value is displayed in the Azure portal, on the Label blade, when you view or configure the Azure Information Protection policy. 

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

### -Owner
**Relevant for:** Classic client only

Specify the email address that is written to the Owner custom property.


```yaml
Type: String
Parameter Sets: SetLabel, SetLabelCustom, Custom
Aliases:

Required: False
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