---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2144825
schema: 2.0.0
---

# Get-MIPScannerRepository

## SYNOPSIS
Gets repository data for an Azure Information Protection content scan job.

## SYNTAX

```
Get-MIPScannerRepository [-Path <String>] [<CommonParameters>]
```

## DESCRIPTION
Gets a list of data repositories that the content scan job is configured to scan.

For more information about content scan jobs, see the [Azure Information Protection on-premises scanner documentation](/information-protection/deploy-aip-scanner-configure-install#create-a-content-scan-job).

## EXAMPLES

### Example 1 Get details for all repositories for the content scan job
```PowerShell
PS C:\WINDOWS\system32> Get-MIPScannerRepository

Path: c:\repoToScan1
OverrideContentScanJob:                : Off
EnableDlp: Off
Enforce: On
LabelFilesByContent: On
RelabelFiles: Off
AllowLabelDowngrade: Off
EnforceDefaultLabel: Off
DefaultLabelType: PolicyDefault
DefaultLabelID: 
DefaultOwner: Scanner
RepositoryOwner:
PreserveFileDetails: On
IncludeFileTypes: 
ExcludeFileTypes        : .lnk,.exe.,.com,.cmd,.bat,.dll,.ini,.sca,.drm,.sys,.cpl,.inf,.drv,.dat,.tmp,.msp,.msi,.pdb,.jar,.ocx,.rtf,.rar,.msg

Path: c:\repoToScan2
OverrideContentScanJob:                : On
EnableDlp: Off
Enforce: Off
LabelFilesByContent: On
RelabelFiles: On
AllowLabelDowngrade: On
EnforceDefaultLabel: Off
DefaultLabelType: PolicyDefault
DefaultLabelID: 
DefaultOwner: Scanner
RepositoryOwner:
PreserveFileDetails: On
IncludeFileTypes: 
ExcludeFileTypes        : .lnk,.exe.,.com,.cmd,.bat,.dll,.ini,.sca,.drm,.sys,.cpl,.inf,.drv,.dat,.tmp,.msp,.msi,.pdb,.jar,.ocx,.rtf,.rar,.msg

```

This example shows a response that includes all repositories configured for the content scan job.

### Example 2 Get details for a specific repository in the content scan job
```PowerShell
PS C:\WINDOWS\system32> Get-MIPScannerRepository -Path 'c:\repoToScan1'

Path: c:\repoToScan1
OverrideContentScanJob:                : Off
EnableDlp: Off
Enforce: On
LabelFilesByContent: On
RelabelFiles: Off
AllowLabelDowngrade: Off
EnforceDefaultLabel: Off
DefaultLabelType: PolicyDefault
DefaultLabelID: 
DefaultOwner: Scanner
RepositoryOwner:
PreserveFileDetails: On
IncludeFileTypes: 
ExcludeFileTypes        : .lnk,.exe.,.com,.cmd,.bat,.dll,.ini,.sca,.drm,.sys,.cpl,.inf,.drv,.dat,.tmp,.msp,.msi,.pdb,.jar,.ocx,.rtf,.rar,.msg
```

This example shows the a response that includes all repositories configured for the content scan job.

## PARAMETERS

### -Path
Defines the path to a specific repository you want to return data for.

This parameter value must be the exact path or path pattern as is defined in the content scan job.

However, this parameter also supports the ***** and **?** wildcards:

For example:

- Entering `-Path c:\repo?` returns details for any repositories named **repo**, with an additional single-character suffix, such as **c:\repo1**.

- Entering `-Path c:\repo*` returns details for any repositories named **repo** with any additional characters as a suffix, such as **c:\repoToScan**.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object
## NOTES

## RELATED LINKS

- [Add-MIPScannerRepository](Add-MIPScannerRepository.md)

- [Get-MIPScannerContentScanJob](Get-MIPScannerContentScanJob.md)

- [Remove-MIPScannerContentScanJob](Remove-MIPScannerContentScanJob.md)

- [Remove-MIPScannerRepository](Remove-MIPScannerRepository.md)

- [Set-MIPScannerContentScanJob](Set-MIPScannerContentScanJob.md)

- [Set-MIPScannerRepository](Set-MIPScannerRepository.md)