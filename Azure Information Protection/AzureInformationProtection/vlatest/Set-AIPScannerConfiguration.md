---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=858205
schema: 2.0.0
---

# Set-AIPScannerConfiguration

## SYNOPSIS
Sets optional configuration for the Azure Information Protection scanner.

## SYNTAX

```
Set-AIPScannerConfiguration [-ScanMode <ScanMode>] [-OverrideLabel <OverrideLabel>]
 [-PreserveFileDetails <PreserveFileDetails>] [-ReportLevel <ReportLevel>] [-Schedule <Schedule>]
 [-JustificationMessage <String>] [-DefaultOwner <String>] [-Type <ScanType>]
```

## DESCRIPTION
The Set-AIPScannerConfiguration cmdlet sets optional configuration for the Azure Information Protection scanner, which will be used the next time the scanner runs. If you need the changes to take effect immediately, restart the Azure Information Protection Scanner service on the Windows server computer.

The optional configuration that you can set is the scan mode, the schedule, label override settings, the justification message, preserve file details, the report level, and the default owner.

## EXAMPLES

### Example 1: Configure the Azure Information Protection scanner to run a one time discovery and create a report for files that would be labeled
```
PS C:\> Set-AIPScannerConfiguration -ScanMode Discover -Schedule OneTime -ReportLevel Info

Configuration was set successfully.
```

This command configures the scanner to run a one-time discovery for files in the specified data repositories, to create a report that lists the files that meet the conditions to be labeled.

Note that because these parameters specify the default values, you need to specify them only if you previously specified them with values other than the defaults.

### Example 2: Configure the Azure Information Protection scanner to continuously discover and label files
 
```
PS C:\> Set-AIPScannerConfiguration -ScanMode Enforce -Schedule Continuous

Configuration was set successfully.
```

This command configures the scanner to continuously discover files in the specified data repositories and label the files that meet the conditions in the Azure Information Protection policy. For these files, they are classified and protected (or have protection removed), according to the label's configuration.  

### Example 3: Configure the Azure Information Protection scanner to run a one time discovery to label files and set the Rights Management owner, and log changed and skipped files

```
PS C:\> Set-AIPScannerConfiguration -ScanMode Enforce -Schedule OneTime -ReportLevel Debug -DefaultOwner admin@contoso.com.

Configuration was set successfully.
```

This command configures the scanner for a one-time discovery of files in the specified data repositories and label the files that meet the conditions in the Azure Information Protection policy. For these files, they are classified and protected (or have protection removed), according to the label's configuration. For files that are protected, the Rights Management owner is set to admin@contoso.com. Actions for changed and skipped files are logged in the report. 


### Example 4: Configure the Azure Information Protection scanner to scan and label all files one time, using the latest Azure Information Protection policy, and log changed and skipped files

```
PS C:\> Set-AIPScannerConfiguration -ScanMode Enforce -Schedule OneTime -ReportLevel Debug -Type Full

Configuration was set successfully.
```

This command configures the scanner to check for any changes to the Azure Information Protection policy and then do a one-time discovery of all files in the specified data repositories and label the files that meet the conditions in the Azure Information Protection policy. For these files, they are classified and protected (or have protection removed), according to the label's configuration. Actions for changed and skipped files are logged in the report. 


## PARAMETERS

### -DefaultOwner
Specifies the Rights Management owner by email address when the scanner protects files. For more information about the Rights Management owner, see [Rights Management issuer and Rights Management owner](https://docs.microsoft.com/information-protection/deploy-use/configure-usage-rights#rights-management-issuer-and-rights-management-owner).

If you do not specify this parameter, default values are used for the Rights Management owner:

- For files on SharePoint Server, the SharePoint author is used to set the Rights Management owner. 

- For files on SharePoint Server that do not have the author property set and for files that are stored on file shares or local folders, the scanner's account is used to set the Rights Management owner.

To remove the currently set Rights Management owner, specify "".


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

### -JustificationMessage
Specifies the justification reason for lowering the classification label or removing protection, if the Azure Information Protection policy requires users to supply this information.

If setting a label triggers the justification and this reason is not supplied, the label is not applied.

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

### -OverrideLabel
Specifies whether to apply a different label to a file that's already labeled. By default, the scanner relabels these files only when they have been labeled by the current scanner account. 

To prevent this relabeling, set this parameter to Off. To relabel files that have been labeled by another account (for example, manually by a user or by another labeling solution), set this parameter to On. 


```yaml
Type: OverrideLabel
Parameter Sets: (All)
Aliases: 
Accepted values: Off, AppliedByScanner, On

Required: False
Position: Named
Default value: AppliedByScanner
Accept pipeline input: False
Accept wildcard characters: False
```

### -PreserveFileDetails
Specify whether to keep the following file attributes when a file is labeled (the default value), or overwrite them: The archive flag, Date Modified, and Owner.

Set this parameter to On to preserve these file attributes and Off to overwrite them.

```yaml
Type: PreserveFileDetails
Parameter Sets: (All)
Aliases: 
Accepted values: On, Off

Required: False
Position: Named
Default value: On
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReportLevel
Defines the level of logging for the scanner reports. By default, only files that are successfully labeled by the scanner are included in the log file.

Log files are stored in %localappdata%\Microsoft\MSIP\Scanner\Reports and have a .csv file format. They include the time taken to scan, the number of scanned files, and statistics of how many files were classified and protected. This folder stores up to 60 reports for each scanning cycle and all but the latest report is compressed to help minimize the required disk space.

- Debug: Includes the skipped files. This level of logging is useful for troubleshooting, but has a performance impact on the Azure Information Protection scanner.

- Info: Logs only the files that were successfully labeled by the scanner.

- Error: Logs only the files that the scanner attempted to label but could not. For example, a justification reason was required but not specified.

Off: Disables reporting, which results in the best performance for the scanner.

Windows Application event logs contain additional logging information, which includes the start and end times for each scanning cycle, when a scanned file has a label applied, and when protection is applied or removed.



```yaml
Type: ReportLevel
Parameter Sets: (All)
Aliases: 
Accepted values: Off, Debug, Info, Error

Required: False
Position: Named
Default value: Info
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScanMode
Specifies whether the scanner only logs the files that meet the conditions in the Azure Information Protection policy without applying the corresponding label (the default action), or applies the label: 

- Discover: Scans the data repositories in the "what if" mode, to log results only without setting the classification or protection that the corresponding label would apply.

- Enforce: Scans the data repositories, and for files that meet the conditions, apply the corresponding label to set the classification and optionally, protection.

```yaml
Type: ScanMode
Parameter Sets: (All)
Aliases: 
Accepted values: Enforce, Discover

Required: False
Position: Named
Default value: Discover
Accept pipeline input: False
Accept wildcard characters: False
```

### -Schedule
Specifies when and how often the scanner runs on the specified data repositories:

- OneTime: A single scan, after which the Azure Information Protection Scanner service is stopped. This option is useful when the *ScanMode* is set to Discover, so that the scanner runs one time and you can check the results in the report. 

- Continuous: The specified data repositories are repeatedly scanned in sequence and the Azure Information Protection Scanner service is not stopped. Use this option to scan for files that are modified or added to the data repositories. However, for files that are modified, check the configuration of the *OverrideLabel* parameter. This option is most useful when the the *ScanMode* is set to Enforce because it ensures all files will be scanned.


```yaml
Type: Schedule
Parameter Sets: (All)
Aliases: 
Accepted values: OneTime, Continuous, Never

Required: False
Position: Named
Default value: OneTime
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type
Specifies whether the scanner maintains a list of previously scanned files so it can scan only new or modified files since the service started, using the same Azure Information Protection policy that was downloaded when the service started. This is the default behavior. 

If this list is not maintained, all files in the specified data repositories are scanned with each scanning cycle. In this case, before the scanner repeats the cycle, it first checks whether there are any changes to the Azure Information Protection policy and downloads any changes.

- Incremental: The scanner maintains a list of previously scanned files so it can scan only new or modified files. The Azure Information Protection policy is not checked for changes. 

- Full: Each time the cycle finishes, the scanner checks for changes in the Azure Information Protection policy and downloads these if necessary. Then, all files in the specified data repositories are scanned again.


```yaml
Type: ScanType
Parameter Sets: (All)
Aliases: 
Accepted values: Incremental, Full

Required: False
Position: Named
Default value: Incremental
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)

