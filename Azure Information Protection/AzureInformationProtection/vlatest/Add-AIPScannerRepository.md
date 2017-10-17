---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=858202
schema: 2.0.0
---

# Add-AIPScannerRepository

## SYNOPSIS
Adds a data repository to be scanned by the Azure Information Protection scanner. 

## SYNTAX

```
Add-AIPScannerRepository [-Path] <String>
```

## DESCRIPTION
The Add-AIPScannerRepository cmdlet adds a data repository to be scanned by the Azure Information Protection scanner. You can specify local folders, UNC paths, and SharePoint Server URLs for SharePoint sites and libraries. 

When you add a SharePoint path for "Shared Documents":

- Specify "Shared Documents" in the path when you want to scan all documents and all folders from Shared Documents. For example: "http://sp2013/Shared Documents"

- Specify "Documents" in the path when you want to scan all documents and all folders from a subfolder under Shared Documents. For example: "http://sp2013/Documents/Sales Reports"

If you later need to remove a data repository that you added, use the [Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md) cmdlet.


## EXAMPLES

### Example 1: Configure a local folder to be scanned

```
PS C:\> Add-AIPScannerRepository -Path D:\Data\Finance

The repository was added successfully.
```

This command adds the local folder named Data\Finance on the D drive to be scanned.

### Example 2: Configure a network-attached storage (NAS) file share to be scanned

```
PS C:\> Add-AIPScannerRepository -Path \\NAS\HR

The repository was added successfully.
```

This command adds the file share named HR on the network-attached storage device named NAS to be scanned.

### Example 3: Scan all documents and folders from the SharePoint Server "Shared Documents" library

```
PS C:\> Add-AIPScannerRepository -Path "http://sp2013/Shared Documents"

The repository was added successfully.
```

This command adds the SharePoint Server "Shared Documents" library to be scanned.

### Example 4: Scan a specific folder in the SharePoint Server "Shared Documents" library

```
PS C:\> Add-AIPScannerRepository -Path http://sp2016.res.local/Documents/HR

The repository was added successfully.
```

This command adds the SharePoint Server folder named HR, from the "Shared Documents" library. 

Note that the path syntax for this scenario uses "Documents" rather than "Shared Documents".

## PARAMETERS

### -Path
Specifies a local path, network path, or SharePoint Server URL for the data repository that you want to scan. Wildcards are not supported.

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

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

