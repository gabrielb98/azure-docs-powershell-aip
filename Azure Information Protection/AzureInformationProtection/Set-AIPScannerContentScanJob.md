---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2144639

schema: 2.0.0
---

# Set-AIPScannerContentScanJob

## SYNOPSIS
Defines settings for an Azure Information Protection content scan job.

## SYNTAX

```
Set-AIPScannerContentScanJob [-Schedule <Schedule>] [-DiscoverInformationTypes <DiscoverInformationTypes>]
 [-RecommendedAsAutomatic <OnOffEnum>] [-EnableDlp <OnOffEnum>] [-Enforce <OnOffEnum>]
 [-LabelFilesByContent <OnOffEnum>] [-RelabelFiles <OnOffEnum>] [-AllowLabelDowngrade <OnOffEnum>]
 [-EnforceDefaultLabel <OnOffEnum>] [-DefaultLabelType <DefaultLabelType>] [-DefaultLabelId <Guid>]
 [-DefaultOwner <String>] [-RepositoryOwner <String>] [-PreserveFileDetails <OnOffEnum>]
 [-IncludeFileTypes <String>] [-ExcludeFileTypes <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
Defines the configuration for your content scan job, which scans the content in the defined repositories, according to the settings defined.
For more information about content scan jobs, see the [Azure Information Protection on-premises scanner documentation](/information-protection/deploy-aip-scanner-configure-install#create-a-content-scan-job).

## EXAMPLES

### Example 1 Define default content scan job settings

```PowerShell
PS C:\WINDOWS\system32> Set-AIPScannerContentScanJob -Enforce Off
```

This example defines the content scan job with default settings, and sets the **Policy enforcement** option to **Off.**

### Example 2 Define a basic content scan job that runs continuously

```PowerShell
PS C:\WINDOWS\system32> Set-AIPScannerContentScanJob -Enforce Off -RelabelFiles On -EnforceDefaultLabel On -Schedule Always
```

This example defines the content scan job with without enforcing a policy, allowing files to be re-labeled, using a default label, and is scheduled to run always.

### Example 3 Define a content scan job that allows for specific re-labeling actions only

```PowerShell
PS C:\WINDOWS\system32> Set-AIPScannerContentScanJob -RelabelFiles On -AllowLabelDowngrade On -EnforceDefaultLabel On
```

This example defines a content scan job that allows for content to be re-labeled only to downgrade a label or use a default label.

### Example 4 Define a content scan job that excludes .msg and .tmp files

```PowerShell
PS C:\WINDOWS\system32> Set-AIPScannerContentScanJob -IncludeFileTypes '' -ExcludeFileTypes '.msg,.tmp'
```

This example defines a content scan job that includes all file types except for .msg and .tmp files. 


### Example 5 Define a content scan job with DLP enabled, and a specific repository owner

```PowerShell
PS C:\WINDOWS\system32> Set-AIPScannerContentScanJob -EnableDLP On -RepositoryOwner 'domain\user'
```

This example defines the content scan job to use the Microsoft 365 built-in data loss prevention (DLP) sensitivity information types when scanning your content, and also defines a specific owner for the content scan job's repositories.

### Example 6 Define a content scan job with a default label to use when automatically labeling content

```PowerShell
PS C:\WINDOWS\system32> Set-AIPScannerContentScanJob -DefaultLabelType Custom -DefaultLabelId 'ff1f1c9d-2f92-4a18-3d84-4608b742424'
```

This example defines the content scan job with a specific label used as the default label, specified by the label ID.

## PARAMETERS

### -AllowLabelDowngrade
Determines whether the content scan job allows for labeling downgrade actions.

Relevant only when the **RelabelFiles** parameter is set to **on**.

```yaml
Type: OnOffEnum
Parameter Sets: (All)
Aliases:
Accepted values: On, Off

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultLabelId
Defines the ID of the default label used when automatically labeling content with a default label.

Mandatory if the **DefaultLabelType** parameter is set to **custom**.

```yaml
Type: Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultLabelType
Determines the type of default label used when automatically labeling content with a default label.

When used, define the label ID you want to use as the default ID using the **DefaultLabelId** parameter.

```yaml
Type: DefaultLabelType
Parameter Sets: (All)
Aliases:
Accepted values: None, PolicyDefault, Custom

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultOwner
Defines the default owner value used for the files scanned, using the account email address. By default, this is the scanner account.

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

### -DiscoverInformationTypes
Determines the types of information types discovered during the content scan job.

```yaml
Type: DiscoverInformationTypes
Parameter Sets: (All)
Aliases:
Accepted values: PolicyOnly, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableDlp
Determines whether the content scan job uses the Microsoft 365 built-in data loss prevention (DLP) sensitivity information types when scanning your content.

> [!TIP]
> If you configure this parameter, you may also want to configure a specific repository owner using the **RepositoryOwner** parameter.
> 

```yaml
Type: OnOffEnum
Parameter Sets: (All)
Aliases:
Accepted values: On, Off

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Enforce
Determines whether the content scan job enforces content scanning and labeling according to your policy.

```yaml
Type: OnOffEnum
Parameter Sets: (All)
Aliases:
Accepted values: On, Off

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnforceDefaultLabel
Determines whether using a default label is always used when relabeling content.

Relevant only when the **RelabelFiles** parameter is set to **on**.

```yaml
Type: OnOffEnum
Parameter Sets: (All)
Aliases:
Accepted values: On, Off

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExcludeFileTypes
Determines any file types that are ignored during your content scan job. Define multiple file types using a comma-separated list.

If you define this parameter, define the **IncludeFileTypes** parameter as null. For example, **Example 4** above.

Relevant only when the **OverrideContentScanJob** parameter is set to **on**.

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

### -IncludeFileTypes
Explicitly determines the file types that are scanned by your content scan job. Define multiple file types using a comma-separated list.

If you define this parameter, define the **ExcludeFileTypes** parameter as null. For example, **Example 4** above.

Relevant only when the **OverrideContentScanJob** parameter is set to **on**.

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

### -LabelFilesByContent
Determines whether the **Label files based on content** content scan job option is enabled or disabled. 

```yaml
Type: OnOffEnum
Parameter Sets: (All)
Aliases:
Accepted values: On, Off

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PreserveFileDetails
Determines whether the file details, including the date modified, last modified, and modified by settings are preserved while scanning and auto-labeling.

```yaml
Type: OnOffEnum
Parameter Sets: (All)
Aliases:
Accepted values: On, Off

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RecommendedAsAutomatic
Determines whether recommended labels are used to automatically label your content.

```yaml
Type: OnOffEnum
Parameter Sets: (All)
Aliases:
Accepted values: On, Off

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RelabelFiles
Determines whether the content scan job is allowed to relabel files.

> [!TIP]
> When using this parameter, use the following additional parameters as needed:
> - **EnforceDefaultLabel**
> - **AllowLabelDowngrade**
> 

```yaml
Type: OnOffEnum
Parameter Sets: (All)
Aliases:
Accepted values: On, Off

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RepositoryOwner

Specifies the SAMAccountname (**domain\user**), UPN (**user@domain**), or SID of a group that owns the repository.

The owners are granted full control permissions on the file if the permissions on the file are changed by a matched DLP rule.

Relevant only when the **EnableDlp** parameter is set to **on**.

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

### -Schedule
Determines whether the content scan job runs according to a specific schedule, or continuously.

```yaml
Type: Schedule
Parameter Sets: (All)
Aliases:
Accepted values: Manual, Always

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object
## NOTES

## RELATED LINKS

- [Add-AIPScannerRepository](Add-AIPScannerRepository.md)

- [Get-AIPScannerContentScanJob](Get-AIPScannerContentScanJob.md)

- [Get-AIPScannerRepository](Get-AIPScannerRepository.md)

- [Remove-AIPScannerContentScanJob](Remove-AIPScannerContentScanJob.md)

- [Remove-AIPScannerRepository](Remove-AIPScannerRepository.md)

- [Set-AIPScannerRepository](Set-AIPScannerRepository.md)
