---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=858208
schema: 2.0.0
---

# Remove-AIPScannerScannedFileType

## SYNOPSIS
Removes file type(s) to the white list or black list of file types scanned by AIP scanner

## SYNTAX

```
Remove-AIPScannerScannedFileType [[-Repository] <String>] -ScannedFileType <String> [<CommonParameters>]
```

## DESCRIPTION
The Remove-AIPScannerScannedFileType cmdlet removes existing file type from being included or excluded from the scan by AIP scanner. 

The cmdlet can specify setting on the service level or specific setting per repository. Setting defined on the repository takes precedence over service level setting.

## EXAMPLES


### Example 1: Removes *.docx files from the the explicit list of files to be scanned
```powershell
PS C:\> Remove-AIPScannerScannedFileType  -ScannedFileType *.docx
The operation was completed successfully
```

Removes *.docx files to be scanned by AIP Scanner for all repositories that do not have repository specific list.

### Example 2: Removes *.docx, *.txt and *.csv files from the the explicit list of files to be scanned on \\server\share1 repository
```powershell
PS C:\> Remove-AIPScannerScannedFileType -Repository \\server\share1 -ScannedFileType @("*.docx","*.txt","*.csv")
The operation was completed successfully
```

Removes docx, txt and csv files from the the explicit list of files to be scanned on \\server\share1 repository

### Example 3: Remove *.dll and *.lnk from exclusion list
```powershell
PS C:\> Remove-AIPScannerScannedFileType  -ScannedFileType @("-*.dll","-*.lnk")
The operation was completed successfully
```

Removes the exclusion for dll and lnk files from the black list of file types not scanned by the scanner

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

### -ScannedFileType
File type or array of file types to be removed from white list or black list scanned by AIP scanner

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
