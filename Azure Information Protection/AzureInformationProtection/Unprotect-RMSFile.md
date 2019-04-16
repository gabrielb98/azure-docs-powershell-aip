---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
ms.assetid: 3A19FD31-4FAF-4B6F-B470-5054FCF05F9C
online version: https://go.microsoft.com/fwlink/?linkid=841550
schema: 2.0.0
---

# Unprotect-RMSFile

## SYNOPSIS
Unprotects a file that is currently protected by RMS.

## SYNTAX

```
Unprotect-RMSFile [-File <String>] [-Folder <String>] [-InPlace] [-Recurse] [-OutputFolder <String>]
 [-SupressUI] [-LogFile <String>] [-ProcessContainers] [<CommonParameters>]
```

## DESCRIPTION
The **Unprotect-RMSFile** cmdlet removes Rights Management (RMS) protection from one or more files in a specified folder if those files were previously protected by AD RMS or Azure RMS. 

You must have sufficient usage rights or be a super user for your organization to unprotect files. For more information, see [Configuring super users for Azure Rights Management and discovery services or data recovery](https://docs.microsoft.com/azure/information-protection/configure-super-users).

If you're unprotecting a container file, each child is recursively extracted, unprotected, and repackaged. Supported container file types are .zip, .rar, .7z, .msg, and .pst.

For .pst files, 5 GB is the maximum file size supported with this cmdlet.

When you run this cmdlet, you have the following options:

- The file is unprotected in the same folder so that the original protected file and the new unprotected file coexist.

- The original file remains protected and an unprotected version of the file is created in another location.

- All files in the specified folder are unprotected in the current location, replacing the original files that were protected.

- All files in the specified folder remain protected and an unprotected version of each file is created in another location.

You can run this command concurrently when you specify a different path for the *LogFile* parameter for each command that runs in parallel. If you don't specify a different log file path and the previous command hasn't finished, the new command will fail.

This cmdlet is not supported for the Azure Information Protection unified labeling client.

## EXAMPLES

### Example 1: Unprotect a single file, replacing the original file
```
PS C:\>Unprotect-RMSFile -File "C:\Test.ptxt" -InPlace
InputFile         DecryptedFile
---------         -------------
C:\Test.ptxt      C:\ Test.txt
```

This command unprotects a single file named Test.ptxt, replacing this protected version of the file with an unprotected version in the same location. When an output directory is not provided and the *InPlace* parameter is specified, the source file is replaced.

### Example 2: Unprotect a single file, retaining the original file
```
PS C:\>Unprotect-RMSFile -File "C:\Test.ptxt" -OutputFolder "C:\Temp"
InputFile       DecryptedFile
---------       -------------
C:\Test.ptxt    C:\Temp\Test.txt
```

This command unprotects a single file but retains the original protected file by creating the unprotected version in the folder location named C:\Temp. When an output folder is provided, a unique file name is created for the unprotected file. If a file of the same name exists, the new file name is made unique in the same way that File Explorer makes a unique copy of the same file name. For example, if Test.txt  exists, Test Copy.txt is created, then Test Copy(2).txt.

### Example 3: Unprotect a folder
```
PS C:\>Unprotect-RMSFile -Folder "C:\Protected" -OutputFolder "C:\Temp"
InputFile                  DecryptedFile
---------                  -------------
C:\Protected\Test.ptxt     C:\Temp\Protected\Test.txt

C:\Protected\Word.docx     C:\Temp\Protected\Word.docx
```

This command unprotects a folder, retaining the original protected files and creating the unprotected versions in the folder location named C:\Temp and creates a corresponding subfolder of "Protected". This command can also be used with the Recurse parameter, which determines whether to include the processing of subfolders.

### Example 4: Unprotect a .PST file
```
PS C:\>Unprotect-RMSFile -File "C:\Test.pst" -OutputFolder "C:\Temp"
InputFile     DecryptedFile
---------     -------------
C:\Test.pst   C:\Temp\Test.pst
```

This command unprotects a .pst (Personal Storage Table) file. The .pst files are container files that can hold Microsoft Outlook .msg files. In turn, these .msg files can be containers that hold attachments. Because the .pst file is a container, every child file and nested container are also unprotected by this operation.

### Example 5: Unprotect a .RAR file
```
PS C:\>Unprotect-RMSFile -File "C:\Test.rar" -OutputFolder "C:\Temp"
InputFile     DecryptedFile
---------     -------------
C:\Test.rar   C:\Temp\Test.zip
```

This command unprotects a .rar archive file. Because .rar files are container files that hold nested files, these nested files can also be archives. Every child file and nested container are also unprotected by this operation. 

Notice that for a .rar input file, the unprotected file is a .zip file.

## PARAMETERS

### -File
Specifies the path and file to unprotect. For the path, you can specify a drive letter or UNC.

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
Specifies the path and folder to unprotect. All the files in the specified folder will be unprotected.

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

### -InPlace
The file or the files in the specified folder are unprotected in the current location, replacing the original protected file or files. This parameter is ignored if the *OutputFolder* parameter is specified.

If neither *InPlace* nor *OutputFolder* is specified, the new file is created in the current directory with "-Copy" appended to the file name, using the same naming convention that File Explorer uses when a file is copied and pasted into the same folder. For example, if a file with Document.docx is protected, the unprotected version is named Document-Copy.docx. If a file named Document-Copy.docx already exists, Document-Copy(2).docx is created, and so on.

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

### -LogFile
Specifies the path and base file name, with optional file name extension for log files. These log files list the files that are successfully or unsuccessfully unprotected. The following three log files are created for success, failure, and debug respectively: 

- **\<file name>.\<file name extension>**

- **\<file name>-failure.\<file name extension>**

- **\<file name>-debug.\<file name extension>**

For container files, these log files also include nested files.

For example, if you specify "C:\Users\Administrator\Unprotect-RMSFile.txt" for this parameter, the following log files are created:

- For files that were successfully unprotected: **C:\Users\Administrator\Unprotect-RMSFile.txt**

- For any files that couldn't be unprotected: **C:\Users\Administrator\Unprotect-RMSFile-failure.txt**

- For debug information: **C:\Users\Administrator\Unprotect-RMSFile-debug.txt**

For the path, you can specify a drive letter or UNC. 

If you do not specify this parameter, the log files **Success.log**, **Failure.log**, and **Debug.log** are written to the default log file location of %localappdata%\Microsoft\MSIPC\pscmdlet\Logs\[GUID].

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
Specifies the output folder for unprotected versions of the protected files. The original folder structure is maintained, which means that subfolders might be created for your specified value.

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
