---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
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
For the Azure Information Protection client, the **Set-AIPFileLabel** cmdlet sets or removes an Azure Information Protection label for one or more files. This action can automatically apply or remove protection when labels are configured for Rights Management protection in the Azure Information Protection policy. When the command runs successfully, any existing label or protection can be replaced.

You cannot create or edit labels by using PowerShell but must do this by using the Azure portal. For instructions, see [Configuring the Azure Information Protection policy](https://docs.microsoft.com/information-protection/configure-policy).

For the Azure Information Protection unified labeling client, currently in preview, the **Set-AIPFileLabel** cmdlet sets or removes an Office 365 sensitivity label for one or more files. This action can automatically apply protection when labels are configured to apply encryption. When the command runs successfully, any existing label or protection can be replaced.

You can run this cmdlet concurrently. To run this cmdlet non-interactively, see [How to label files non-interactively for Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection) from the admin guide.

NOTE: When you run this cmdlet with the Azure Information Protection unified labeling client, there are differences from the Azure Information Protection client:

- The *Owner* parameter is not supported.

- SharePoint Server paths are not supported.

- When a file isn't labeled because it was manually labeled, there was no match for the conditions that you specified, or the file had a higher classification, the file is skipped with the single comment of "No label to apply".

## EXAMPLES

### Example 1a: Apply the "General" label to all files in a folder and any of its subfolders - Azure Information Protection client only
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

### Example 1b: Apply the "General" label to all files in a folder and any of its subfolders - Azure Information Protection unified labeling client only
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

This command sets a label named "General" on all files in the Projects folder and any of its subfolders.

If the General label is configured to apply encryption, the files that were successfully labeled with this command will also be encrypted. In this case, the Rights Management owner (who has the Rights Management Full Control permission) of these files is the user who ran the PowerShell command.

In this example, one file was not labeled (skipped) because it required justification. This might be the intended outcome to ensure that a file with a higher classification label or protection isn't accidentally overwritten with a lower classification label or has protection removed. To enable this safeguard, the Office 365 classification label policy must be configured to require justification for removing a label or lowering the classification. When you then run this command without the **JustificationMessage** parameter and the label triggers justification, the file is skipped with the comment "No label to apply". 

### Example 2: Apply the "General" label to a single file, which requires justification - Azure Information Protection client only
```
PS C:\> Set-AIPFileLabel -Path \\Finance\Projects\Analysis.xlsx -LabelId d9f23ae3-1324-1234-1234-f515f824c57b -JustificationMessage 'The previous label no longer applies'
FileName                          Status      Comment
--------                          ------      ------------
\\finance\projects\analysis.xlsx  Success
```

This command sets the "General" label for a file that is already labeled with a higher classification label. The Azure Information Protection policy is configured to require justification for lowering the classification label, removing a label, or removing protection. Because the command includes a justification message, the new label is successfully applied and the justification reason is logged on the local computer.

### Example 2: Apply the "General" label to a single file, which requires justification - Azure Information Protection unified labeling client only
```
PS C:\> Set-AIPFileLabel -Path \\Finance\Projects\Analysis.xlsx -LabelId d9f23ae3-1324-1234-1234-f515f824c57b -JustificationMessage 'The previous label no longer applies'
FileName                          Status      Comment
--------                          ------      ------------
\\finance\projects\analysis.xlsx  Success
```

This command sets the "General" label for a file that is already labeled with a higher classification label. The Office 365 classification label policy is configured to require justification for removing a label or lowering the classification. Because the command includes a justification message, the new label is successfully applied.

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

### Example 5a: Remove a label from a file - Azure Information Protection client only

```
PS C:\> Set-AIPFileLabel C:\Projects\Analysis.docx -RemoveLabel -JustificationMessage 'The previous label no longer applies'

FileName                   Status Comment
--------                   ------ ------------
C:\Projects\Analysis.docx  Success
```

This command removes the existing label from the file named C:\Projects\Analysis.docx, and specifies a justification message that is required because the Azure Information Protection policy setting is enabled that requires justification for lowering the classification label, removing a label, or removing protection.

### Example 5b: Remove a label from a file - Azure Information Protection unified labeling client only

```
PS C:\> Set-AIPFileLabel C:\Projects\Analysis.docx -RemoveLabel -JustificationMessage 'The previous label no longer applies'

FileName                   Status Comment
--------                   ------ ------------
C:\Projects\Analysis.docx  Success
```

This command removes the existing label from the file named C:\Projects\Analysis.docx, and specifies a justification message that is required because the Office 365 classification label policy setting is enabled that requires justification for removing a label or lowering the classification. 

### Example 6: Apply the "Confidential \ All Employees" label to all files in a folder and register these files with the document tracking site - Azure Information Protection client preview version only

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

Note: This example requires the preview version of the Azure Information Protection client.

This command sets a label named "Confidential \ All Employees" on all files in the Projects folder and any of its subfolders. The Label ID specified is for the sublabel "All Employees" that has a parent label of "Confidential". 

If the "Confidential \ All Employees" label applies protection, the files that were successfully labeled with this command will also be protected. Because the *EnableTracking* parameter was specified, the protected documents can now be tracked and revoked in the document tracking site by the person who labeled the document, and by global administrators who use the Administrator mode.

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
Specifies the identity (ID) of the label to apply. When a label has sublabels, always specify the ID of just a sublabel and not the parent label. 

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
Note: For the current preview version of the Azure Information Protection unified labeling client, SharePoint Server paths are not supported.

Specifies a local path, network path, or SharePoint Server URL to the files for which you want to get the label and protection information. 

Wildcards are not supported and WebDav locations are not supported.

For SharePoint paths: SharePoint Server 2013 and SharePoint Server 2016 are supported.

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

### -EnableTracking
Note: This parameter is available only in the preview version of the Azure Information Protection client.

Specify this parameter to register a protected document with the document tracking portal. 

The user running this cmdlet and global administrators can then track the protected document and if necessary, revoke it. For more information about the document tracking site, see [Configuring and using document tracking for Azure Information Protection](https://docs.microsoft.com/azure/information-protection/rms-client/client-admin-guide-document-tracking) from the admin guide. 

If the label does not apply protection, this parameter is ignored.

```yaml 
Type: SwitchParameter 
```



### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String[]

## OUTPUTS

### Microsoft.InformationProtection.Powershell.AIP.Results.SetAIPFileResult

## NOTES

## RELATED LINKS

[Get-AIPFileStatus](./Get-AIPFileStatus.md)

[Set-AIPFileClassification](./Set-AIPFileClassification.md)

[Set-AIPAuthentication](./Set-AIPAuthentication.md)