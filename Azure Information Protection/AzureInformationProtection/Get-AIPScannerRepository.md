---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=858210
schema: 2.0.0
---

# Get-AIPScannerRepository

## SYNOPSIS
Gets a list of data repositories that the Azure Information Protection scanner is configured to scan.

## SYNTAX

```
Get-AIPScannerRepository [<CommonParameters>]
```

## DESCRIPTION
The Get-AIPScannerRepository cmdlet gets the list of data repositories that the Azure Information Protection scanner is configured to scan. These data repositories are specified by using the [Add-AIPScannerRepository](./Add-AIPScannerRepository.md) cmdlet. 

Tip: You can use the output of this cmdlet with [Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md) to clean up the list of the data repositories for the scanner. For example: Get-AIPScannerRepository | Remove-AIPScannerRepository

## EXAMPLES

### Example 1: Get the list of the current data repositories
```
PS C:\> Get-AIPScannerRepository

Repository          : http://sp2016.res.local/Shared Documents/Folder
OverrideLabel       : On
PreserveFileDetails : On
DefaultOwner        : "admin@contoso.msft"  
DefaultLabel        : PolicyDefaultLabel

Repository          : http://sp2013/Documents
OverrideLabel       : Off
PreserveFileDetails : On
DefaultOwner        :
DefaultLabel        : f018e9e7-0cfc-4c69-b27a-ac3cb7df43cc

Repository          : \\server1\HR
OverrideLabel       : Off
PreserveFileDetails : On
DefaultOwner        :
DefaultLabel        : None

Repository          : d:\Data\Finance
OverrideLabel       : Off
PreserveFileDetails : On
DefaultOwner        :
DefaultLabel        : None
ScannedFileTypes    :"*.docx"
```

This command gets the list of the data repositories that the Azure Information Protection scanner is currently configured to scan. The list displays two paths from SharePoint Server, a file server share, and a local disk and folder.

In the example, the last repository is configured to scan only files that have a file name extension of .docx, by using the [Set-AIPScannerScannedFileTypes](./Set-AIPScannerScannedFileTypes.md) cmdlet. If a repository has not been configured for a file types list, this parameter is not included in the output.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Set-AIPScannerRepository](./Set-AIPScannerRepository.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)
