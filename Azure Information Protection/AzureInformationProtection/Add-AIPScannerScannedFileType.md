---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=858202
schema: 2.0.0
---

# Add-AIPScannerScannedFileType

## SYNOPSIS
Adds new file type(s) to the white list or black list of file types scanned by AIP scanner

## SYNTAX

```
Add-AIPScannerScannedFileType [[-Repository] <String>] -ScannedFileType <String[]>
```

## DESCRIPTION
The Add-AIPScannerScannedFileType cmdlet add new file type to be included or excluded from the scan by AIP scanner. In order to scan all file types add "*" to the list. In case the scanner is not set to scan all file types, you can use this command to add specific file type(s) to be scanned by specifying the file extension. If the scanner is set to scan all file types, you can use this command to exclude specific file types by specifying the extension with "-" character before it.

The cmdlet can specify setting on the service level or specific setting per repository. Setting defined on the repository takes precedence over service level setting.

## EXAMPLES

### Example 1: Adds *.docx files to be scanned AIP scanner
```powershell
PS C:\> Add-AIPScannerScannedFileType  -ScannedFileType *.docx
The operation was completed successfully
```

Adds *.docx files to be scanned by AIP Scanner for all repositories that do not have repository specific list.

### Example 2: Adds *.docx, *.txt and *.csv files to be scanned AIP scanner on \\server\share1 repository
```powershell
PS C:\> Add-AIPScannerScannedFileType -Repository \\server\share1 -ScannedFileType @("*.docx","*.txt","*.csv")
The operation was completed successfully
```

Adds doc, txt and csv files to be scanned by AIP Scanner on \\server\share1 repository

### Example 3: Exclude *.dll and *.lnk from being scanned by AIP scanner
```powershell
PS C:\> Add-AIPScannerScannedFileType  -ScannedFileType @("-*.dll","-*.lnk")
The operation was completed successfully
```

Excludes dll and lnk files from being scanned by AIP scanner for all repositories that do not have repository specific list.

## PARAMETERS

### -Repository
Repository name addaed by Add-AIPScannerRepository cmdlet. The repository should be added before you can set this setting.

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

### -ScannedFileType
File type or array of file types to be added white list or black list scanned by AIP scanner

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
