---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2144825
schema: 2.0.0
---

# Get-AIPScannerRepository

## SYNOPSIS
**Relevant for:** AIP unified labeling client. Deprecated for the classic client.

Gets repository data for an Azure Information Protection content scan job.

## SYNTAX

```
Get-AIPScannerRepository [-Path <String>] [<CommonParameters>]
```

## DESCRIPTION
Gets a list of data repositories that the content scan job is configured to scan.

For more information about content scan jobs, see the [Azure Information Protection on-premises scanner documentation](/information-protection/deploy-aip-scanner-configure-install#create-a-content-scan-job).

[!INCLUDE [This classic client cmdlet is sunset](../includes/classic-client-sunset-cmdlet.md)]

## EXAMPLES

### Example 1 Get details for all repositories for the content scan job
```powershell
PS C:\WINDOWS\system32> Get-AIPScannerRepository

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
```powershell
PS C:\WINDOWS\system32> Get-AIPScannerRepository -Path 'c:\repoToScan1'

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

### None

## OUTPUTS

### System.Object
## NOTES

## RELATED LINKS

- [Add-AIPScannerRepository](Add-AIPScannerRepository.md)

- [Get-AIPScannerContentScanJob](Get-AIPScannerContentScanJob.md)

- [Remove-AIPScannerContentScanJob](Remove-AIPScannerContentScanJob.md)

- [Remove-AIPScannerRepository](Remove-AIPScannerRepository.md)

- [Set-AIPScannerContentScanJob](Set-AIPScannerContentScanJob.md)

- [Set-AIPScannerRepository](Set-AIPScannerRepository.md)