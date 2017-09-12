---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=841548
schema: 2.0.0
---

# Remove-AIPScannerRepository

## SYNOPSIS
Removes a repository from a list of scanned repositories. 

## SYNTAX

```
Remove-AIPScannerRepository [-Path] <String>
```

## DESCRIPTION
The Remove-AIPScannerRepository cmdlet removes a repository from a list of scanned repositories. The cmdlet can be used in conjunction with Get-AIPScannerRepository in order to remove all defined repositories

## EXAMPLES

### Example 1: Remove \\server1\HR from the repositories list
```
PS C:\> Remove-AIPScannerRepository -Path \\server1\HR 
```
The repository \\server1\HR was removed successfully.
```

### Example 2: Empty list of repositories
```
PS C:\> Get-AIPScannerRepository | Remove-AIPScannerRepository 
```
The repository http://sp2016.res.local/Shared Documents/Folder was removed successfully.
The repository http://sp2013/Documents was removed successfully.
The repository d:\data\Finance was removed successfully.
```

## PARAMETERS

### -Path
Local path, UNC path or SharePoint 2013/2016 site or library. 

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

