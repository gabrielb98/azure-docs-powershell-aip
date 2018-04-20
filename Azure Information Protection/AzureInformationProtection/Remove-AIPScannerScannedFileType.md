---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=872605
schema: 2.0.0
---

# Remove-AIPScannerScannedFileType

## SYNOPSIS
Removes file types from a configured list of file types to scan or exclude from scanning by the Azure Information Protection scanner

## SYNTAX

```
Remove-AIPScannerScannedFileType [[-Repository] <String>] -ScannedFileType <String> [<CommonParameters>]
```

## DESCRIPTION
The Remove-AIPScannerScannedFileType cmdlet removes file types from a list that you have already configured by using [Set-AIPScannerScannedFileTypes](./Set-AIPScannerScannedFileTypes.md). The list specifies which file types to scan or exclude from scanning by the Azure Information Protection scanner. 

To remove a new file type to scan, specify `*.<file name extension>`. To remove a new file type from being excluded from being scanned, specify `-*.<file name extension>`. 

## EXAMPLES


### Example 1: Remove .docx files from the list of file types to be scanned

```powershell
PS C:\> Remove-AIPScannerScannedFileType  -ScannedFileType *.docx

The operation was completed successfully
```

This command removes *.docx file types from the configured list of file types to be scanned for all data repositories that do not have their own file types list.

### Example 2: Remove .docx, .txt and .csv files from the list of file types to be excluded for a file share

```powershell
PS C:\> Remove-AIPScannerScannedFileType -Repository \\server\share1 -ScannedFileType @("*.docx","*.txt","*.csv")

The operation was completed successfully
```

This command removes the file name extensions of .docx, .txt, and .csv from the configured list of files to be excluded from scanning for the file share named \\\server\\share1.

### Example 3: Remove .dll and *.lnk from the list of file types to be excluded from scanning

```powershell
PS C:\> Remove-AIPScannerScannedFileType  -ScannedFileType @("-*.dll","-*.lnk")

The operation was completed successfully
```

This command removes the file name extensions of .dll and .lnk from the configured list of files to be excluded from scanning for all data repositories that do not have their own list.

## PARAMETERS

### -Repository
Specifies a data repository that you have configured for the scanner by using [Add-AIPScannerRepository](./Add-AIPScannerRepository.md). This parameter identifies a local path, network path, or SharePoint Server URL for the data repository to apply the file types list. Wildcards are not supported.

If no data repository is specified, the command removes file types from the list that applies to all data repositories that do not have their own file types list.

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
Specifies the file type or array of file types to be removed from the configured list of file types.

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
For more information, see [about_CommonParameters[(https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Add-AIPScannerScannedFileType](Add-AIPScannerScannedFileType.md)

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Remove-AIPScannerRepository](Remove-AIPScannerRepository.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Set-AIPScannerRepository](./Set-AIPScannerRepository.md)

[Set-AIPScannerScannedFileTypes](./Set-AIPScannerScannedFileTypes.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)
