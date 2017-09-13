---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=858202
schema: 2.0.0
---

# Add-AIPScannerRepository

## SYNOPSIS
Adds a data repository to a list of repositories for the Azure Information Protection scanner. 

## SYNTAX

```
Add-AIPScannerRepository [-Path] <String>
```

## DESCRIPTION
The Add-AIPScannerRepository cmdlet adds a data repository to a list of scanned repositories for the Azure Information Protection scanner to scan. You can specify local folders, UNC paths, and SharePoint Server sites and libraries. 

When you specify a data repository for SharePoint Server:

- You can scan all documents and subfolders when you specify (includes documents in subfolders) under "Shared Documents": Specify the path "http://servername/Documents".

- To scan just specific subfolders under Shared Documents should be scanned path "http://servername/Shared Documents/Folder" should be used.

## EXAMPLES

### Example 1: Scan local D:\Data\Finance

```
PS C:\> Add-AIPScannerRepository -Path 

The repository was added successfully.
```

### Example 2: Scan NAS fileshare \\NAS\HR

```
PS C:\> Add-AIPScannerRepository -Path 

The repository was added successfully.
```

### Example 3: Scan all shared documents in http://sp2013/Documents

```
PS C:\> Add-AIPScannerRepository -Path http://sp2013/Documents

The repository was added successfully.
```

### Example 4: Scan fodler named HR under Shared Documetns in SharePoint server named SP2016.res.local in http://sp2016.res.local/Shared Documents/HR

```
PS C:\> Add-AIPScannerRepository -Path http://sp2016.res.local/Shared Documents/

The repository was added successfully.
```

## PARAMETERS

### -Path
Local path, UNC path or SharePoint 2013/2016 site or library. SharePoint Online repositories are not supported.

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

[Install-AIPScanner](./Install-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)
