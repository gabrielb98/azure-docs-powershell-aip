---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2004363
schema: 2.0.0
author: cabailey
---

# Get-AIPScannerStatus

## SYNOPSIS
**Relevant for:** AIP unified labeling and classic clients

Gets the current status of the service for the Azure Information Protection scanner.

## SYNTAX

```
Get-AIPScannerStatus [<CommonParameters>]
```

## DESCRIPTION

The **Get-AIPScannerStatus** returns the current status of the scanner service for Azure Information Protection. 

Possible values:

- **Offline:** The service is not started.
- **Idle:** The service is running but not currently scanning. 
- **Scanning:** The service is running and currently scanning files.
- **Error:** The scanner service is running but it has encountered an error that prevents it from scanning files. 

    For example, the service cannot access the database for the scanner configuration.

> [!NOTE]
> To provide a unified and streamlined customer experience, the **Azure Information Protection classic client** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021.** 
> 
> This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).
>

## EXAMPLES

### Example 1: Get the current status of the scanner service
```
PS C:\> Get-AIPScannerStatus

NodeName       ScannerStatus    LastTimeStamp
--------       -------------    -------------
AIPSCANNODE1            Idle    7/2/2018 10:04:07 AM

```

The output shows the scanner service to be running but not currently scanning. This status was reported 7/2/2018 at 10:04:07 AM.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.
For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Start-AIPScan](./Start-AIPScan.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Update-AIPScanner](./Update-AIPScanner.md)