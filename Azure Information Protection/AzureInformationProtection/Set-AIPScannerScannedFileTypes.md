---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=866449
schema: 2.0.0
---

# Set-AIPScannerScannedFileTypes

## SYNOPSIS
Sets the white list and black list of file types scanned by AIP scanner

## SYNTAX

```
Set-AIPScannerScannedFileTypes [[-Repository] <String>] -ScannedFileType <String[]> [<CommonParameters>]
```

## DESCRIPTION
The Set-AIPScannerScannedFileType cmdlet sets file types list to be included or excluded from the scan by AIP scanner. In order to scan all file types use "*". In case the scanner is not set to scan all file types, you can use this command to set specific file type(s) to be scanned by specifying the file extension. You can use this command to exclude specific file types by specifying the extension with "-" character before it.

The cmdlet can specify setting on the service level or specific setting per repository. Setting defined on the repository takes precedence over service level setting.

## EXAMPLES

### Example 1: Set AIP scanner to scan only *.docx files
```powershell
PS C:\> Set-AIPScannerScannedFileType  -ScannedFileType *.docx
The operation was completed successfully
```

Sets *.docx file type as the only file type scanned by AIP Scanner for all repositories that do not have repository specific list.

### Example 2: Set AIP scanner to scan docx, txt and csv files on \\server\share1 repository
```powershell
PS C:\> Add-AIPScannerScannedFileType -Repository \\server\share1 -ScannedFileType @("*.docx","*.txt","*.csv")
The operation was completed successfully
```

Set AIP scanner to scan docx, txt and csv files on \\server\share1 repository

### Example 3: Scan all files except *.dll and *.lnk from being scanned by AIP scanner
```powershell
PS C:\> Add-AIPScannerScannedFileType  -ScannedFileType @("*","-*.dll","-*.lnk")
The operation was completed successfully
```

Scan all file types, excluding dll and lnk files from being scanned by AIP scanner for all repositories that do not have repository specific list.

### Example 4: Remove repository level setting for file types for \\server\share1  repository and set it to use service level settings
```powershell
PS C:\> Add-AIPScannerScannedFileType -Repository \\server\share1 -ScannedFileType ""
The operation was completed successfully
```

Use service level setting for file types white list and black list for \\server\share1 repository

## PARAMETERS

### -Repository
{{Fill Repository Description}}

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ScannedFileTypes
File type or array of file types to be set as white list or black list scanned by AIP scanner

```yaml
Type: <String[]>
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.
For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS
