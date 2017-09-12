---
external help file: AIP.dll-Help.xml
online version: 
schema: 2.0.0
---

# Add-AIPScannerRepository

## SYNOPSIS
Adds a repository to a list of scanned repositories. 

## SYNTAX

```
Add-AIPScannerRepository [-Path] <String>
```

## DESCRIPTION
The Add-AIPScannerRepository cmdlet adds a repository to a list of scanned repositories. Local folders, UNC paths and SharePoint sites and libraries can be added. 

Note that for SharePoint in order to scan all documents under "Shared Documents" path http://servername/Documents should be specified.
In case only specific subfolders under Shared Documents should be scanned path "http://servername/Shared Documents/Folder" should be used.

## EXAMPLES

### Example 1: Scan local D:\Data\Finance
```
PS C:\> Add-AIPScannerRepository -Path 
```
The repository was added successfully.
```

### Example 2: Scan NAS fileshare \\NAS\HR
```
PS C:\> Add-AIPScannerRepository -Path 
```
The repository was added successfully.
```

### Example 3: Scan all shared documents in http://sp2013/Documents
```
PS C:\> Add-AIPScannerRepository -Path http://sp2013/Documents
```
The repository was added successfully.
```

### Example 4: Scan fodler named HR under Shared Documetns in SharePoint server named SP2016.res.local in http://sp2016.res.local/Shared Documents/HR
```
PS C:\> Add-AIPScannerRepository -Path http://sp2016.res.local/Shared Documents/
```
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

