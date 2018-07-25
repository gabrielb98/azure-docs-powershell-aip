---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2004363
schema: 2.0.0
---

# Get-AIPScannerStatus

## SYNOPSIS
Gets the current status of the service for the Azure Information Protection scanner.

## SYNTAX

```
Get-AIPScannerStatus [<CommonParameters>]
```

## DESCRIPTION
The Get-AIPScannerStatus returns the current status of the scanner service for Azure Information Protection. Possible values:
- Offline: The service is not started.
- Idle: The service is running but not currently scanning. 
- Running: The service is running and currently scanning files.
- Finished: The service is running and a scanning cycle has just finished. For the next service status, the service will change to Idle (when the schedule is set to Manual) or Running (when the schedule is set to Always).
- Error: The scanner service is running but it has encountered an error that prevents it from scanning files. For example, the service cannot access the database for the scanner configuration.

Note: This cmdlet requires the preview version of the scanner that is included with the current preview version of the Azure Information Protection client.

## EXAMPLES

### Example 1: Get the current status of the scanner service
```
PS C:\> Get-AIPScannerStatus

NodeName       ScannerStatus    LastTimeStamp
--------       -------------    -------------
AIPSCANNODE1            Idle    7/2/2018 10:04:07 AM

The service is running but not currently scanning. This status was reported 7/2/2018 at 10:04:07 AM.
```

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.
For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Add-AIPScannerScannedFileTypes](Add-AIPScannerScannedFileTypes.md)

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Remove-AIPScannerScannedFileTypes](./Remove-AIPScannerScannedFileTypes.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Set-AIPScannerRepository](./Set-AIPScannerRepository.md)

[Set-AIPScannerScannedFileTypes](./Set-AIPScannerRepository.md)

[Start-AIPScan](./Start-AIPScan.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Update-AIPScanner](./Update-AIPScanner.md)