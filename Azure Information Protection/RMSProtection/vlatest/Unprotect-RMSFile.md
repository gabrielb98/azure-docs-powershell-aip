---
external help file: RMSProtection.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkID=623209
schema: 2.0.0
ms.assetid: C07C0831-92B3-43CE-B18F-F2A12F3283DC
---

# Unprotect-RMSFile

## SYNOPSIS
Unprotects a file that is currently protected by RMS.

## SYNTAX

```
Unprotect-RMSFile [-File <String>] [-Folder <String>] [-Recurse] [-OutputFolder <String>] [-SupressUI]
 [-LogFile <String>] [-ProcessContainers] [<CommonParameters>]
```

## DESCRIPTION
The **Unprotect-RMSFile** cmdlet removes Rights Management (RMS) protection from one or more files in a specified folder if those files were previously protected by AD RMS or Azure RMS.
When you run this cmdlet, you have the following options:

- The file is unprotected in the same folder so that the original protected file and the new unprotected file co-exist.
- The original file remains protected and an unprotected version of the file is created in another location.
- All files in the specified folder are unprotected in the current location, replacing the original files that were protected.
- All files in the specified folder remains protected and an unprotected version of each file is created in another location.

If you are unprotecting a container file, each child is recursively extracted, unprotected, and repackaged.
Supported container file types are .zip, .rar, .7z, .msg, and .pst.

## EXAMPLES

### Example 1: Unprotect a single file, replacing the original file
```
PS C:\>Unprotect-RMSFile -File "C:\Test.ptxt" -InPlace
InputFile         DecryptedFile
---------         -------------
C:\Test.ptxt      C:\ Test.txt
```

This command unprotects a single file named Test.ptxt, replacing this protected version of the file with an unprotected version in the same location.
When an output directory is not provided and the *InPlace* parameter is specified, the source file is replaced.

### Example 2: Unprotect a single file, retaining the original file
```
PS C:\>Unprotect-RMSFile -File "C:\Test.ptxt" -OutputFolder "C:\Temp"
InputFile       DecryptedFile
---------       -------------
C:\Test.ptxt    C:\Temp\Test.txt
```

This command unprotects a single file but retains the original protected file by creating the unprotected version in the folder location named C:\Temp.
When an output folder is provided, a unique file name is created for the unprotected file.
If a file of the same name exists, the new file name is made unique in the same way that File Explorer makes a unique copy of the same file name.
For example, if Test.txt  exists, Test Copy.txt is created, then Test Copy(2).txt.

### Example 3: Unprotect a folder
```
PS C:\>Unprotect-RMSFile -Folder "C:\Protected" -OutputFolder "C:\Temp"
InputFile                  DecryptedFile
---------                  -------------
C:\Protected\Test.ptxt     C:\Temp\Protected\Test.txt

C:\Protected\Word.docx     C:\Temp\Protected\Word.docx
```

This command unprotects a folder, retaining the original protected files and creating the unprotected versions in the folder location named C:\Temp and creates a corresponding subfolder of "Protected".
This command can also be used with the *Recurse* parameter, which determines whether to include the processing of subfolders.

### Example 4: Unprotect a .PST file
```
PS C:\>Unprotect-RMSFile -File "C:\Test.pst" -OutputFolder "C:\Temp"
InputFile     DecryptedFile
---------     -------------
C:\Test.pst   C:\Temp\Test.pst
```

This command unprotects a .pst (Personal Storage Table) file.
The .pst files are container files that can hold Microsoft Outlook .msg files.
In turn, these .msg files can be containers that hold attachments.
Because the .pst file is a container, every child file and nested container is also unprotected by this operation.

### Example 5: Unprotect a .RAR file
```
PS C:\>Unprotect-RMSFile -File "C:\Test.rar" -OutputFolder "C:\Temp"
InputFile     DecryptedFile
---------     -------------
C:\Test.rar   C:\Temp\Test.zip
```

This command unprotects a .rar archive file.
Because .rar files are container files that hold nested files, these nested files can also be archives.
Every child file and nested container is also unprotected by this operation.
Notice that for a .rar input file, the unprotected file is a .zip file.

## PARAMETERS

### -File
Specifies the path and file to unprotect.
For the path, you can specify a drive letter or UNC.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Folder
Specifies the path and folder to unprotect.
For the path, you can specify a drive letter or UNC.
All of the files in the specified folder will be unprotected.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogFile
Specifies the path for log files that list the files that are successfully or unsuccessfully unprotected.
Three log files are created: 

- Success
- Failure
- Debug

For container files, these log files also include nested files.

For the path, you can specify a drive letter or UNC.
If the log file location is specified, success and failure files are written to that path as separate files.
Debug log files are always written to the default location.

The default log file location is %localappdata%\RMSProtection\Logging.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputFolder
Specifies the output folder for unprotected versions of the protected files.
The original folder structure is maintained, which means that subfolders might be created for your specified value.
For the path, you can use a drive letter or UNC.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProcessContainers
This parameter is not currently implemented.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Recurse
Indicates that this operation unprotects all files in all subfolders.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupressUI
This parameter is not implemented; there is no UI for this cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
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
