---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=872606
schema: 2.0.0
---

# Set-AIPScannerScannedFileTypes

## SYNOPSIS
Sets a list of file types to scan or exclude from scanning by the Azure Information Protection scanner

## SYNTAX

```
Set-AIPScannerScannedFileTypes [[-Repository] <String>] -ScannedFileType <String[]> [<CommonParameters>]
```

## DESCRIPTION
The Set-AIPScannerScannedFileType cmdlet sets a list of file types to scan or exclude from scanning by the Azure Information Protection scanner. To scan all file types, use `*`. To scan only specific file types, specify `*.<file name extension>`. To exclude specific file types from being scanned, specify `-*.<file name extension>`.

When you specify this list and do not specify a data repository, the list applies to all data repositories that do not have their own list specified. 

After you have specified your file types list, you can verify the contents by running [Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)and [Get-AIPScannerRepository](./Get-AIPScannerRepository.md). To change your list of file types:

- To add a new file type to the list, use [Add-AIPScannerScannedFileType](Add-AIPScannerScannedFileType.md).

- To remove a file type from the list, use [Remove-AIPScannerScannedFileType](Remove-AIPScannerScannedFileType.md).

## EXAMPLES

### Example 1: Configure the scanner to scan only .docx files

```powershell
PS C:\> Set-AIPScannerScannedFileType  -ScannedFileType *.docx

The operation was completed successfully
```

This command configures the scanner to scan only files that have a file name extension of .docx. Only this file type will be scanned unless a data repository has its own list of file types.

### Example 2: Configure the scanner to scan only .docx, .txt and .csv files on a server share

```powershell
PS C:\> Add-AIPScannerScannedFileType -Repository \\server\share1 -ScannedFileType @("*.docx","*.txt","*.csv")

The operation was completed successfully
```

This command configures the scanner to scan only files that have a file name extension of .docx, .txt or .csv on the server share named \\\server\\share1.


### Example 3: Configure the scanner to scan all files except those that have a .dll or .lnk file name extension

```powershell
PS C:\> Add-AIPScannerScannedFileType  -ScannedFileType @("*","-*.dll","-*.lnk")

The operation was completed successfully
```

This command configures the scanner to scan all files except those that have a .dll or .lnk file name extension, and the data repository doesn't have its own file types list.

### Example 4: Remove the file types list that was set for a data repository 

```powershell
PS C:\> Add-AIPScannerScannedFileType -Repository \\server\share1 -ScannedFileType ""

The operation was completed successfully
```

This command removes any previously included or excluded file types for the server share named \\\server\\share1. If the scanner has a list of included or excluded file types that applies to all data repositories, those settings apply instead. 


## PARAMETERS

### -Repository
Specifies a data repository that you have configured for the scanner by using [Add-AIPScannerRepository](./Add-AIPScannerRepository.md). This parameter identifies a local path, network path, or SharePoint Server URL for the data repository to apply the file types list. Wildcards are not supported.

If no data repository is specified, the list applies to all data repositories that do not have their own file types list.

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
Specifies the file type or array of file types to be included or excluded from scanning.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

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

[Remove-AIPScannerScannedFileType](Remove-AIPScannerScannedFileType.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Set-AIPScannerRepository](./Set-AIPScannerRepository.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)