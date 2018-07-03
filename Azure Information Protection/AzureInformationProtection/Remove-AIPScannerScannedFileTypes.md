---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=872605
schema: 2.0.0
---

# Remove-AIPScannerScannedFileTypes

## SYNOPSIS
Removes file types from a configured list of file types to scan or exclude from scanning by the Azure Information Protection scanner.

## SYNTAX

```
Remove-AIPScannerScannedFileTypes [-Repository <String>] -ScannedFileTypes <String[]> [<CommonParameters>]
```

## DESCRIPTION
The Remove-AIPScannerScannedFileTypes cmdlet removes file types from a list that you have already configured by using [Set-AIPScannerScannedFileTypes](./Set-AIPScannerScannedFileTypes.md). The list specifies which file types to scan or exclude from scanning by the Azure Information Protection scanner. 

To remove a specific file types, specify \` .\<file name extension\>\`.

When you specify this list and do not specify a data repository, the list applies to all data repositories that do not have their own list specified.

If you try to remove an extension that doesn't exist on the list the command is ignored.
## EXAMPLES


### Example 1: Remove .docx files from the list of file types to be scanned

```powershell
PS C:\> Remove-AIPScannerScannedFileTypes -ScannedFileTypes ".docx"

The operation was completed successfully
```

This command removes extension of .docx from the list of files to be scanned. 
Note that command doesn't add the extension to the exclusion list, and if the scanner is set to scan all files (extension *) .docx file will still be scanned. If you want .docx files to be explicitly exlcuded from scan use Add-AIPScannerScannedFileType cmdlet to add "-.docx" to the exclusion list.

### Example 2: Remove .lnk files from the exclusion list of files to scan
```powershell
PS C:\> Remove-AIPScannerScannedFileTypes -ScannedFileTypes "-.lnk"

The operation was completed successfully
```

This command removes extension of .lnk from the exclusion list of files to be scanned. 



## PARAMETERS

### -Repository
Specifies a data repository that you have configured for the scanner by using [Add-AIPScannerRepository](./Add-AIPScannerRepository.md). This parameter identifies a local path, network path, or SharePoint Server URL for the data repository to apply the file types list. Wildcards are not supported.

If no data repository is specified, the command removes file types from the list that applies to all data repositories that do not have their own file types list.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ScannedFileTypes
Specifies the file type or array of file types to be included or excluded from scanning.

- To scan all file types, specify \`*\`.
- To scan only specific file types, specify \` .\<file name extension\>\`. For example, \ .docx. - To exclude specific file types from being scanned, specify \`- .\<file name extension\>\`.For example, \- .docx. - To reset the list back to defaults, specify \`@()\`.


```yaml
Type: String[]
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
For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Add-AIPScannerScannedFileTypes](Add-AIPScannerScannedFileTypes.md)

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Remove-AIPScannerRepository](Remove-AIPScannerRepository.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Set-AIPScannerRepository](./Set-AIPScannerRepository.md)

[Set-AIPScannerScannedFileTypes](./Set-AIPScannerScannedFileTypes.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)
