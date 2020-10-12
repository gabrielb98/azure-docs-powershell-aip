---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2144823
schema: 2.0.0
---

# Add-MIPScannerRepository

## SYNOPSIS
Adds a repository to an Azure Information Protection content scan job.

## SYNTAX

``` PowerShell
Add-MIPScannerRepository -Path <String> [-OverrideContentScanJob <OnOffEnum>] [-EnableDlp <OnOffEnum>]
 [-Enforce <OnOffEnum>] [-LabelFilesByContent <OnOffEnum>] [-RelabelFiles <OnOffEnum>]
 [-AllowLabelDowngrade <OnOffEnum>] [-EnforceDefaultLabel <OnOffEnum>] [-DefaultLabelType <DefaultLabelType>]
 [-DefaultLabelId <Guid>] [-DefaultOwner <String>] [-RepositoryOwner <String>]
 [-PreserveFileDetails <OnOffEnum>] [-IncludeFileTypes <String>] [-ExcludeFileTypes <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
Adds a repository for your content scan job to scan.

For more information about content scan jobs, see the [Azure Information Protection on-premises scanner documentation](/information-protection/deploy-aip-scanner-configure-install#create-a-content-scan-job).

## EXAMPLES

### Example 1 Add a new repository using the configured content scan jobs settings
```PowerShell
PS C:\WINDOWS\system32> Add-MIPScannerRepository -Path 'c:\repoToScan'
```

This example adds the **repoToScan** repository to your content scan job, using the content scan job's current settings.

### Example 2 Add a new repository, overriding the content scan job's current settings

```PowerShell
PS C:\WINDOWS\system32> Add-MIPScannerRepository -Path 'c:\repoToScan' -OverrideContentScanJob On -Enforce On -DefaultOwner 'ms@gmail.com'
```

This example adds the **repoToScan** repository to your content scan job, overriding the currently configured content scan job settings.

## PARAMETERS

### -AllowLabelDowngrade
Determines whether the content scan job allows for labeling downgrade actions.

Relevant only when the following parameters are set to **on**:

- **OverrideContentScanJob**
- **RelabelFiles**

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

- Mandatory if the **DefaultLabelType** parameter is set to **custom**.

- Relevant only when the **OverrideContentScanJob** parameter is set to **true**.


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

Relevant only when the **OverrideContentScanJob** parameter is set to **true**.


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

Relevant only when the **OverrideContentScanJob** parameter is set to **true**.


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

### -EnableDlp
Determines whether the content scan job uses the Microsoft 365 built-in data loss prevention (DLP) sensitivity information types when scanning your content.

> [!TIP]
> If you configure this parameter, you may also want to configure a specific repository owner using the **RepositoryOwner** parameter.
> 

Relevant only when the **OverrideContentScanJob** parameter is set to **true**.

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

Relevant only when the **OverrideContentScanJob** parameter is set to **true**.

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

Relevant only when the following parameters are set to **on**:

- **RelabelFiles**
- **OverrideContentScanJob** 

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

Define either this parameter, or the **IncludeFileTypes** parameter, but not both.

Relevant only when the **OverrideContentScanJob** parameter is set to **true**.


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

Define either this parameter, or the **ExcludeFileTypes** parameter, but not both.

Relevant only when the **OverrideContentScanJob** parameter is set to **true**.

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

Relevant only when the **OverrideContentScanJob** parameter is set to **true**.

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

### -OverrideContentScanJob
Determines whether the settings for this repository override the settings defined for the content scan job.

If set to **On**, define any settings you want to override using additional parameters.

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

### -Path
Defines the path to the repository you want to add to the content scan job.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PreserveFileDetails
Determines whether the file details, including the date modified, last modified, and modified by settings are preserved while scanning and auto-labeling.

Relevant only when the **OverrideContentScanJob** parameter is set to **true**.

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

Relevant only when the **OverrideContentScanJob** parameter is set to **true**.

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
Specifies the SAMAccountname (domain\user), UPN (user@domain), or SID of a group that owns the repository.
The owners are granted full control permissions on file if the permissions on the file are changed by matched DLP rule.

Relevant only when the following parameters are set to **on**:

- **OverrideContentScanJob**
- **EnableDlp**

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

- [Get-MIPScannerContentScanJob](Get-MIPScannerContentScanJob.md)

- [Get-MIPScannerRepository](Get-MIPScannerRepository.md)

- [Remove-MIPScannerContentScanJob](Remove-MIPScannerContentScanJob.md)

- [Remove-MIPScannerRepository](Remove-MIPScannerRepository.md)

- [Set-MIPScannerContentScanJob](Set-MIPScannerContentScanJob.md)

- [Set-MIPScannerRepository](Set-MIPScannerRepository.md)