---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=858210
schema: 2.0.0
---

# Get-AIPScannerStatus

## SYNOPSIS
Gets current status of AIPscanner service

## SYNTAX

```
Get-AIPScannerStatus [<CommonParameters>]
```

## DESCRIPTION
The Get-AIPScannerStatus returns current status of AIPscanner service. Possible values:
Offline	 -	service is down
Idle 	 - 	service is running but not executing any active scanning 
Running  -	service is running and executing active scanning
Finished -	service is running and scanning cycle just finished. In the next service status check the service will pass to Idle (for Manual schedule) or Running (for Always schedule)
Error	 -	scanner service is running but it has encountered a fatal error that prevents it from scannig files, for example DB is down


## EXAMPLES

### Example 1: Get current AIPscanner service status
```powershell
PS C:\> Get-AIPScannerStatus
NodeName       ScannerStatus 	LastTimeStamp
--------       ------------- 	-------------
AIPSCANNODE1            Idle 	7/2/2018 10:04:07 AM

The service is running but is not executing any active scan. Last status polling was done on 7/2/2018 at 10:04:07 AM

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.
For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS
