---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=858208
schema: 2.0.0
---

# Remove-AIPScannerRepository

## SYNOPSIS
Removes a data repository from a list of scanned repositories. 

## SYNTAX

```
Remove-AIPScannerRepository [-Path] <String>
```

## DESCRIPTION
The Remove-AIPScannerRepository cmdlet removes a data repository from the list of data repositories that the Azure Information Protection scanner is configured to scan. These data repositories are specified by using the [Add-AIPScannerRepository](./Add-AIPScannerRepository) cmdlet.

Tip: You can use this cmdlet with [Get-AIPScannerRepository](./Get-AIPScannerRepository.md) to quickly remove all data repositories that the scanner is currently configured to scan.


## EXAMPLES

### Example 1: Remove a file share from the data repositories list
```
PS C:\> Remove-AIPScannerRepository -Path \\server1\HR 

The repository \\server1\HR was removed successfully.
```

This command removes the file share named \\\server1\HR from the list of data repositories that the scanner is configured to scan.

### Example 2: Remove all data repositories that are currently specified
```
PS C:\> Get-AIPScannerRepository | Remove-AIPScannerRepository 

The repository http://sp2016.res.local/Shared Documents/Folder was removed successfully.
The repository http://sp2013/Documents was removed successfully.
The repository d:\data\Finance was removed successfully.
```

This command first gets all the data repositories that are currently specified for the scanner and then removes them. In this example, three data repositories are found and removed from the scanner's configuration.


## PARAMETERS

### -Path
Specifies a local path, network path, or SharePoint Server URL for the data repository that you no longer want to scan. Wildcards are not supported.

For SharePoint paths: SharePoint Server 2013 and SharePoint Server 2016 are supported.

Examples include C:\Folder\, C:\Folder\Filename, \\\Server\Folder, http://sharepoint.contoso.com/Shared%20Documents/Folder. Paths can include spaces when you enclose the path value with quotes.
 

```yaml
Type: String
Parameter Sets: (All)
Aliases: FullName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

## INPUTS

### System.String


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)
