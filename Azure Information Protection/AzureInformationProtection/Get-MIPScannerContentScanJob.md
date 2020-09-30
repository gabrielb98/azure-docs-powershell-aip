---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version:
schema: 2.0.0
---

# Get-MIPScannerContentScanJob

## SYNOPSIS
Gets details about an Azure Information Protection content scan job.

## SYNTAX

```
Get-MIPScannerContentScanJob [<CommonParameters>]
```

## DESCRIPTION
Returns a full list of all the parameters configured for the content scan job.

For more information about content scan jobs, see the [Azure Information Protection on-premises scanner documentation](/information-protection/deploy-aip-scanner-configure-install#create-a-content-scan-job).

## EXAMPLES

### Example 1 Content scan job settings defined by PowerShell
```PowerShell
PS C:\WINDOWS\system32> Get-MIPScannerContentScanJob

Schedule                : Manual
DiscoverInformationTypes: All
RecommendedAsAutomatic  : False
EnableDlp               : Off
Enforce                 : On
LabelFilesByContent     : On
RelabelFiles            : Off
AllowLabelDowngrade     : Off
EnforceDefaultLabel     : Off
DefaultLabelType        : PolicyDefault
DefaultLabelId          :
DefaultOwner            : Scanner
RepositoryOwner         :
PreserveFileDetails     : On
IncludeFileTypes        :
ExcludeFileTypes        : .lnk,.exe.,.com,.cmd,.bat,.dll,.ini,.sca,.drm,.sys,.cpl,.inf,.drv,.dat,.tmp,.msp,.msi,.pdb,.jar,.ocx,.rtf,.rar,.msg
Repositories:
c:\repoToScan1
c:\repoToScan2
```

This example shows a sample command and response when the content scan job has been configured via PowerShell.

### Example 2 Content scan job settings defined by PowerShell
```PowerShell
PS C:\WINDOWS\system32> Get-MIPScannerContentScanJob

Schedule                : Manual
DiscoverInformationTypes: PolicyOnly
RecommendedAsAutomatic  : False
EnableDlp               : 
Enforce                 : 
LabelFilesByContent     : 
RelabelFiles            : 
AllowLabelDowngrade     : 
EnforceDefaultLabel     : 
DefaultLabelType        : PolicyDefault
DefaultLabelId          :
DefaultOwner            : 
RepositoryOwner         :
PreserveFileDetails     : 
IncludeFileTypes        :
ExcludeFileTypes        : 
Repositories:
c:\repoToScan1
```

This example shows a sample command and response when the content scan job has been configured by importing a file, or using the Azure portal. In this case, the individual content scan job parameters are not applicable, and do not return values.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object
## NOTES

## RELATED LINKS

- [Add-MIPScannerRepository](Add-MIPScannerRepository.md)

- [Get-MIPScannerRepository](Get-MIPScannerRepository.md)

- [Remove-MIPScannerContentScanJob](Remove-MIPScannerContentScanJob.md)

- [Remove-MIPScannerRepository](Remove-MIPScannerRepository.md)

- [Set-MIPScannerContentScanJob](Set-MIPScannerContentScanJob.md)

- [Set-MIPScannerRepository](Set-MIPScannerRepository.md)