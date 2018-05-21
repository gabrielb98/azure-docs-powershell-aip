---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=872604
schema: 2.0.0
---

# Add-AIPScannerScannedFileType

## SYNOPSIS
Adds new file types to a configured list of file types to scan or exclude from scanning by the Azure Information Protection scanner

## SYNTAX

```
Add-AIPScannerScannedFileType [[-Repository] <String>] -ScannedFileType <String[]>
```

## DESCRIPTION
The Add-AIPScannerScannedFileType cmdlet adds new file types to a list that you have already configured by using [Set-AIPScannerScannedFileTypes](./Set-AIPScannerScannedFileTypes.md). The list specifies which file types to scan or exclude from scanning by the Azure Information Protection scanner. 

To add a new file type to scan, specify `*.<file name extension>`. To exclude a new file type from being scanned, specify `-*.<file name extension>`.

Note: This cmdlet is available only with the current preview version of the scanner.


## EXAMPLES

### Example 1: Add .docx files to the list of file types to be scanned

```powershell
PS C:\> Add-AIPScannerScannedFileType  -ScannedFileType *.docx

The operation was completed successfully
```

This command adds the file name extension of .docx to the configured list of file types to be scanned for all data repositories that do not have their own file types list.

### Example 2: Add .docx, .txt, and .csv files to the list of file types to be scanned for a file share

```powershell
PS C:\> Add-AIPScannerScannedFileType -Repository \\server\share1 -ScannedFileType @("*.docx","*.txt","*.csv")

The operation was completed successfully
```

This command adds the file name extensions of .docx, .txt, and .csv to the configured list of files to be scanned for the file share named \\\server\\share1.

### Example 3: Add .dll and .lnk files to the list of file types to be excluded from being scanned

```powershell
PS C:\> Add-AIPScannerScannedFileType  -ScannedFileType @("-*.dll","-*.lnk")
The operation was completed successfully
```

This command adds the .dll and .lnk file types to the configured list of file types to be excluded from scanning for all data repositories that do not have their own file types list.


## PARAMETERS

### -Repository
Specifies a data repository that you have configured for the scanner by using [Add-AIPScannerRepository](./Add-AIPScannerRepository.md). This parameter identifies a local path, network path, or SharePoint Server URL for the data repository to apply the file types list to include or exclude. Wildcards are not supported.

If no data repository is specified, the command adds file types to the list that applies to all data repositories that do not have their own file types list.

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
Specifies the file type or array of file types to be added to the configured list of file types.

- If your file types list specifies file types to scan, specify `*.<file name extension>` to add a new file type to the list. For example, \*.docx.
- If your file types list specifies file types to exclude from scanning, specify `-*.<file name extension>` to remove a file type from the list. For example, \-*.docx.


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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameter](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Remove-AIPScannerRepository](Remove-AIPScannerRepository.md)

[Remove-AIPScannerScannedFileType](Remove-AIPScannerScannedFileType.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Set-AIPScannerRepository](./Set-AIPScannerRepository.md)

[Set-AIPScannerScannedFileTypes](./Set-AIPScannerScannedFileTypes.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

