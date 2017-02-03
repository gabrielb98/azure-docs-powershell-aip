---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=841548
schema: 2.0.0
ms.assetid: 0F28BB73-D550-416D-BA5D-9ECE1E92E5D9
---

# Protect-RMSFile

## SYNOPSIS
Protects a specified file or the files in a specified folder by using RMS.

## SYNTAX

```
Protect-RMSFile [-File <String>] [-Folder <String>] [-Recurse] [-TemplateID <String>]
 [-License <SafeInformationProtectionLicenseHandle>] [-DoNotPersistEncryptionKey <String>]
 [-OutputFolder <String>] [-OwnerEmail <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Protect-RMSFile** cmdlet protects a file or all files in a specified folder by using Azure RMS or AD RMS. If the file was previously protected, it will be protected again, to apply any changes such as those that might be made to the template that is being used to protect the file.

All file types can be protected in the same way that the RMS sharing application can protect all files. However, different levels of protection will be  automatically applied (native or generic), depending on the file type. You can change the level of protection by editing the registry. In addition, some files change their file name extension after they are protected by Rights Management. For more information, see [File API configuration](https://docs.microsoft.com/information-protection/develop/file-api-configuration) (https://docs.microsoft.com/information-protection/develop/file-api-configuration) on the Microsoft documentation site.

When you run this cmdlet, you have the following options:

- The file is protected in the current location, replacing the original file that was unprotected.
- The original file remains unprotected and a protected version of the file is created in another location.
- - All files in the specified folder are protected in the current location, replacing the original files that were unprotected.
- All files in the specified folder remains unprotected and a protected version of each file is created in another location.

Tip: For step-by-step instructions to use this cmdlet to protect files on a Windows Server file share, using File Resource Manager and File Classification Infrastructure, see [RMS Protection with Windows Server File Classification Infrastructure (FCI)](https://docs.microsoft.com/information-protection/rms-client/configure-fci)  (https://docs.microsoft.com/information-protection/rms-client/configure-fci) on the Microsoft documentation site.

## EXAMPLES

### Example 1: Protect and replace a single file by using a template
```
PS C:\>Protect-RMSFile -File "C:\Test.docx" -InPlace -TemplateID 82bf3474-6efe-4fa1-8827-d1bd93339119 -OwnerEmail "IT@Contoso.com"
InputFile             EncryptedFile
---------             -------------
C:\Test.docx          C:\Test.docx
```

This command protects a single file named Test.docx by using a template, and replaces the original unprotected file. The Rights Management owner of the file, and the email address that might be displayed to users when they access the protected file, is for the IT department.

### Example 2: Create a protected copy of a single file by using a template
```
PS C:\>Protect-RMSFile -File "Test.docx" -TemplateID 82bf3474-6efe-4fa1-8827-d1bd93339119 -OwnerEmail "IT@Contoso.com"
InputFile             EncryptedFile
---------             -------------
C:\Test.docx          C:\Test-Copy.docx
```

This command is the same as the previous example, except that it doesn't use the InPlace parameter. Because it also doesn't use the OutputFolder parameter, the protected file is created in the current folder with "-Copy" appended to the file name. The original, unprotected file remains in the current folder.

### Example 3: Create a protected version of a file by using a template
```
PS C:\>Protect-RMSFile -File "C:\Test.docx" -OutputFolder "C:\Temp" -TemplateID e6ee2481-26b9-45e5-b34a-f744eacd53b0 -OwnerEmail "admin@Contoso.com"

InputFile             EncryptedFile
---------             -------------
C:\Test.txt           C:\Temp\Test.ptxt
```

This command protects a single file named Test.docx by using a template and places this protected version of the file in C:\Temp, leaving the original file unprotected in the root of the C: drive. The Rights Management owner of the file, and the email address that might be displayed to users when they access the protected file, is for the administrator.

### Example 4: Protected all files in a folder by using a template
```
PS C:\>Protect-RMSFile -Folder "\\server1\Docs" -InPlace -TemplateID e6ee2481-26b9-45e5-b34a-f744eacd53b0 -OwnerEmail "IT@Contoso.com"

InputFile                        EncryptedFile

----------                       -------------
\\server1\Docs\Feb2015.docx      \\server1\Docs\Feb2015.docx

\\server1\Docs\Feb2015.txt       \\server1\Docs\Feb2015.ptxt

\\server1\Docs\Jan2015.docx      \\server1\Docs\Jan2015.docx

\\server1\Docs\Jan2015.txt       \\server1\Docs\Jan2015.ptxt
```

This command protects all files in a server share (single folder only, not subfolders), replacing the unprotected files. The Rights Management owner of the file, and the email address that might be displayed to users when they access the protected file, is for the IT department.

### Example 5: Protected files with a specific file name extension in a folder by using a template
```
PS C:\>foreach ($file in (Get-ChildItem -Path \\server1\Docs -Recurse -Force | where {!$_.PSIsContainer} | Where-Object {$_.Extension -eq ".docx"})) {Protect-RMSFile -File $file.PSPath -InPlace -TemplateID "e6ee2481-26b9-45e5-b34a-f744eacd53b0" -OwnerEmail "IT@Contoso.com"}


InputFile                                   EncryptedFile

---------                                   -------------
\\server1\Docs\Feb2015.docx                 \\server1\Docs\Feb2015.docx

\\server1\Docs\Jan2015.docx                 \\server1\Docs\Jan2015.docx

\\server1\Docs\Reports\Feb2015.docx         \\server1\Docs\Reports\Feb2015.docx

\\server1\Docs\Reports\Jan2015.docx         \\server1\Docs\Reports\Jan2015.docx
```

This command protects only files that have a .docx file name extension in a folder (and all subfolders) on a server share, replacing the unprotected files. The Rights Management owner of the file, and the email address that might be displayed to users when they access the protected file, is for the IT department.

Although the [Protect-RMSFile](./Protect-RMSFile.md) command does not natively support wildcards, you can use Windows PowerShell to achieve this, and change the file name extension in the example, as required.

### Example 6: Protect a single file by using an ad-hoc rights policy
```
PS C:\>$License = New-RMSProtectionLicense -UserEmail 'user1@contoso.com' -Permission EDIT
PS C:\> Protect-RMSFile -License $License -File "C:\Test.txt" -InPlace
InputFile             EncryptedFile
---------             -------------
C:\Test.txt           C:\Test.ptxt
```

The first command creates an ad-hoc rights policy that grants Edit rights to user1@contoso.com.

The second command protects a single file named Test.txt by using this ad-hoc rights policy just created, and replaces the original unprotected file.

Note that unless your email address is user1@contoso.com, you will not be able to unprotect this file after the command completes because you do not have any rights to it and you are not the Rights Management owner. If you need to be able to unprotect this file later, you can add your name and grant the user and yourself either the EXTRACT or OWNER right in the ad-hoc rights policy in the first command. Or if you do not want the user to be able to unprotect the file, add *-OwnerEmail \<your email address\>* to the end of the second command.

## PARAMETERS

### -DoNotPersistEncryptionKey
Specifies that the content key for the file or files this cmdlet protects does not persist, which means that the protected file or files cannot be accessed offline. This is a more secure setting, because the user must be authenticated each time the file is accessed and the policy is checked for any changes. However, it is also less flexible for users who might not have the network connectivity to authenticate. 

The acceptable values for this parameter:

- Disk:  The content key is prevented from being cached locally in the license store.
For example, on Windows computers, the license store is %localappdata%\Microsoft\MSIPC.
- License:  The content key is prevented from being inserted within the serialized publishing license.
- All:  The content key is prevented from being cached locally in the license store and being inserted within the serialized publishing license.

```yaml
Type: String
Parameter Sets: (All)
Aliases:
Accepted values: all, disk, license

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -File
Specifies the path and file name to be protected. For the path, you can use a drive letter or UNC.

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
Specifies the path and folder to be protected. For the path, you can use a drive letter or UNC.

All the files currently in the specified folder will be protected. New files added to the folder will not be automatically protected.

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

### -License
Specifies the variable name that stores an ad hoc rights policy that was created by using the [New-RMSProtectionLicense](./New-RMSProtectionLicense.md) cmdlet. This ad-hoc rights policy is used instead of a template to protect the file or files.

```yaml
Type: SafeInformationProtectionLicenseHandle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputFolder
Specifies the path and folder to place protected versions of the original files that remain unprotected. The original folder structure is maintained, which means that subfolders might be created for your specified value.

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

### -OwnerEmail
Specifies the Rights Management owner of the protected file or files by email address.

The Rights Management owner has all rights (Full Control) for the file. The  Rights Management owner is independent from the Windows file system owner. 

You can use this parameter to set an owner other than yourself. If you don't specify a value, the cmdlet will use the email address of your authenticated session to identify the Rights Management owner of the protected file or files. If you use AD RMS, or Azure RMS with a user account to protect files, this will be your email address. If you use Azure RMS with a service principal account, this email address will be long string of numbers and letters.

If you become the Rights Management owner of the protected file, make sure that the rights you apply to the file do not restrict the original file owner from making changes to the file and using it as intended.

Because users see this email address when they open generically protected files and if they try to access protected files that do not grant them access permissions, consider specifying a group email address such as your help desk or IT department. However, do not specify a group name if members of that group should not have full control rights for the file.

Important: Although this parameter is optional, if you do not specify it when you protect files by using Azure RMS and a service principal, the email address that users see in these messages from the Rights Management sharing application will not be helpful.Because of this, we recommend that you always specify this parameter when you protect files by using Azure RMS and a service principal rather than your user account.

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

### -Recurse
When used with the *Folder* parameter, indicates that all the current files in the subfolders will be protected.

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

### -TemplateID
Specifies the ID of the template to use to protect the specified file or files if you do not use the *License* parameter for an ad-hoc policy. If you do not know the ID of the template that you want to use, use the [Get-RMSTemplate](./Get-RMSTemplate.md) cmdlet.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-RMSTemplate](./Get-RMSTemplate.md)

[Get-RMSFileStatus](./Get-RMSFileStatus.md)

[New-RMSProtectionLicense](./New-RMSProtectionLicense.md)

[Unprotect-RMSFile](./Unprotect-RMSFile.md)
