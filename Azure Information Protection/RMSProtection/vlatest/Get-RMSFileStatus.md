---
external help file: RMSProtection.dll-Help.xml
ms.assetid: 074F42BF-D30C-45C4-88F9-E445A7DFEA41
online version: https://go.microsoft.com/fwlink/?LinkID=623199
schema: 2.0.0
---

# Get-RMSFileStatus

## SYNOPSIS
Gets the RMS protection status of a specified file.

## SYNTAX

```
Get-RMSFileStatus -File <String> [<CommonParameters>]
```

## DESCRIPTION
The **Get-RMSFileStatus** cmdlet returns the protection status (whether the file is protected by Rights Management or not) of a specified file.

A protected file has a status of **Protected (Native)** or **Protected (Generic)**, and an unprotected file has a status of **Unprotected**.

Note that a natively protected container file, such as an Outlook data file (.PST) always returns the protection status of Unprotected.

## EXAMPLES

### Example 1: List the protection status for a specified file
```
PS C:\>Get-RMSFileStatus -File "C:\Test.docx"
FileName             Status
--------             ------
C:\Test.docx         Unprotected
```

This command lists the Rights Management protection status for the specified file C:\Test.docx.
Because a file with a .docx file name extension supports native protection, the status returns "Protected (Native)" or "Unprotected".

### Example 2: List the protection status for all files in a folder and any subfolders
```
PS C:\>foreach ($file in (Get-ChildItem -Path C:\Documents -Recurse -Force | where {!$_.PSIsContainer})) {Get-RMSFileStatus -f $file.PSPath}
```

Although the **Get-RMSFileStatus** cmdlet works for one file at a time, you can use the following Windows PowerShell command to get the status of all files in a folder (in our example, named C:\Documents) and its subfolders.
The same command can be used with a UNC path instead of a drive and path.

### Example 3: Create a .CSV file with the protection status for all files in a folder and any subfolders
```
PS C:\>$(foreach ($file in (Get-ChildItem -Path C:\Documents\ -Recurse -Force | where {!$_.PSIsContainer})) {Get-RMSFileStatus -f $file.PSPath}) | Export-Csv -Path C:\Temp\ProtectedFilesList.csv -Encoding ascii -NoTypeInformation
```

You can further extend the previous example by outputting the results to a .CSV file, so that you can sort and order the information.

In this example, the .CSV file is named ProtectedFilesList.csv and saved to the C:\Temp folder.
If the file already exists, it will be overwritten.

## PARAMETERS

### -File
Specifies the fully qualified path to the file to verify whether it is protected by Rights Management.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Protect-RMSFile](./Protect-RMSFile.md)

[Unprotect-RMSFile](./Unprotect-RMSFile.md)
