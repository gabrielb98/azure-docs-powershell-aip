---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
ms.assetid: 104C7431-A41A-4178-AA0B-74FF1A5B51AA
online version: https://go.microsoft.com/fwlink/?linkid=841543
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
**Relevant for:** AIP classic client only

The **Get-RMSFileStatus** cmdlet returns the protection status (whether the file is protected by Rights Management or not) of a specified file.

A protected file has a status of **Protected (Native)** or **Protected (Generic)**, and an unprotected file has a status of **Unprotected**.

Note that a natively protected container file, such as an Outlook data file (.PST) always returns the protection status of Unprotected.

> [!NOTE]
> To provide a unified and streamlined customer experience, the **Azure Information Protection classic client** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021.** 
> 
> This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).
>

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

In this example, the .CSV file is named ProtectedFilesList.csv and saved to the C:\Temp folder. If the file already exists, it will be overwritten.

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

