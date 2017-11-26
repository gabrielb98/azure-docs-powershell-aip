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
The Set-AIPScannerConfiguration cmdlet sets optional configuration settings for the Azure Information Protection scanner. When the scanner is installed, these settings are configured for you with their default values. Use this cmdlet to change the settings, which will be used the next time the scanner runs. If you need the changes to take effect immediately, restart the Azure Information Protection Scanner service on the Windows server computer.

The configuration settings include whether the scanner is in discovery mode only or applies labels, whether a file will be relabeled, whether file attributes are changed, what is logged in the reports, whether the scanner runs once or continuously, what justification message to use when required, and the Rights Management owner for protected files.

## EXAMPLES

### Example 1: Configure the Azure Information Protection scanner to run a one-time discovery and create a report for files that would be labeled
```
PS C:\> Set-AIPScannerConfiguration -ScanMode Discover -Schedule OneTime -ReportLevel Info

Configuration was set successfully.
```

This command configures the scanner to run a one-time discovery for files in the specified data repositories, and then create a report that lists the files that meet the conditions to be labeled.

Note that because these parameters specify the values that are set by default when the scanner is installed, you need to specify them only if you previously specified other values.

### Example 2: Configure the Azure Information Protection scanner to continuously discover and label files
 
```
PS C:\> Set-AIPScannerConfiguration -ScanMode Enforce -Schedule Continuous

Configuration was set successfully.
```

This command configures the scanner to continuously discover files in the specified data repositories and label the files that meet the conditions in the Azure Information Protection policy. 

For these files, they are classified and protected (or have protection removed), according to the label configuration.  

### Example 3: Configure the Azure Information Protection scanner to run a one time discovery to label files, set the Owner custom property and Rights Management owner, and log all files

```
PS C:\> Set-AIPScannerConfiguration -ScanMode Enforce -Schedule OneTime -ReportLevel Debug -DefaultOwner admin@contoso.com.

Configuration was set successfully.
```

This command configures the scanner for a one-time discovery of files in the specified data repositories and label the files that meet the conditions in the Azure Information Protection policy. 

For these files, they are classified and protected (or have protection removed), according to the label configuration. For files that are protected, the Owner custom property and the Rights Management owner is set to admin@contoso.com. 

Every discovered file and the resulting action is logged in the reports. 


### Example 4: Configure the Azure Information Protection scanner to scan and label all files one time, remove the Owner custom property and Rights Management owner, and log all files

```
PS C:\> Set-AIPScannerConfiguration -ScanMode Enforce -Schedule OneTime -ReportLevel Debug -Type Full -DefaultOwner ""

Configuration was set successfully.
```

This command configures the scanner to do a one-time discovery of all files in the specified data repositories and label the files that meet the conditions in the Azure Information Protection policy. 

For these files, they are classified and protected (or have protection removed), according to the label configuration. The existing value for the Owner custom property and Rights Management owner is removed, and the default value will be used instead. 

Every discovered file and the resulting action is logged in the reports. 

### Example 5: Configure the Azure Information Protection scanner to set the Owner custom property and Rights Management owner to an administrator's account

```
PS C:\> Set-AIPScannerConfiguration -DefaultOwner "admin@contoso.com"

Configuration was set successfully.
```

This command keeps the current scanner configuration, except that it sets the Owner custom property and the Rights Management owner to the administrator's account for all scanned files. The exception is for files on SharePoint that have an author value in a valid email format. For these files, the author value is used to set the Owner custom property and the Rights Management owner.

## PARAMETERS

### -DefaultOwner

Specify the email address for the Owner custom property when a file is classified, and for the Rights Management owner when a file is protected. For more information about the Rights Management owner, see [Rights Management issuer and Rights Management owner](https://docs.microsoft.com/information-protection/deploy-use/configure-usage-rights#rights-management-issuer-and-rights-management-owner).

If you specify this parameter, it is applied to all scanned files except for files on SharePoint that have an author value in a valid email format. For these files, the author value is always used to set the Owner custom property and the Rights Management owner.

If you do not specify this parameter, default values are used for the Owner custom property and the Rights Management owner:

- For files on SharePoint Server, the SharePoint author is used. 

- For files on SharePoint Server that do not have the author property set and for files that are stored on file shares or local folders, the scanner's account is used.

To remove the currently set Owner custom property and Rights Management owner, and use the default values instead, specify "". 


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
Specify the justification reason for lowering the classification label or removing protection, if the Azure Information Protection policy requires users to supply this information.

If setting a label triggers the justification and this reason is not supplied, the label is not applied. In this case, the status displayed in the error log and debug log is "Skipped" with the comment "Justification required".

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
Specify whether to apply a different label to a file that's already labeled. By default, the scanner relabels these files only when they have been labeled by the current scanner account. 

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
Define the level of logging for the scanner reports. When the scanner is first installed, by default, only files that are successfully labeled by the scanner are included in the log file.

Log files are stored in %localappdata%\Microsoft\MSIP\Scanner\Reports and have a .csv file format. They include the time taken to scan, the number of scanned files, and statistics of how many files were classified and protected. This folder stores up to 60 reports for each scanning cycle and all but the latest report is compressed to help minimize the required disk space.

- Debug: Logs every file that was discovered and the resulting action. This level of logging is useful for troubleshooting but slows down the Azure Information Protection scanner.

- Info: Logs only the files that were successfully labeled by the scanner, or would be labeled if the scanner is in discovery mode.

- Error: Logs only the files that the scanner attempted to label but could not. For example, a justification reason was required but not specified. Or, a file was in use, or the scanner service did not have write access to the file.

- Off: Disables reporting, which results in the best performance for the scanner.

The local Windows **Applications and Services** event log, **Azure Information Protection** contains additional logging information. The events include the start and end times for each scanning cycle, when a scanned file has a label applied, and when protection is applied or removed. For more information, see [Event log IDs and descriptions](https://docs.microsoft.com/information-protection/deploy-use/deploy-aip-scanner#event-log-ids-and-descriptions).


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
Specifies whether the scanner only logs the files that meet the conditions in the Azure Information Protection policy without applying the corresponding label (the default setting), or applies the label: 

- Discover: Scans the data repositories in the "what if" mode, to log results only, without setting the classification or protection that the corresponding label would apply.

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
Specifies how often the scanner runs on the specified data repositories:

- OneTime: A single scan, after which the Azure Information Protection Scanner service is stopped and the schedule is then automatically set to Never. To run a new scan, you must change the schedule back to OneTime, or Continuous.
    
    This option is useful when the *ScanMode* is set to Discover, so that the scanner runs one time and you can check the results in the report. 

- Continuous: The specified data repositories are repeatedly scanned in sequence and the Azure Information Protection Scanner service is not stopped. Use this option to scan for files that are modified or added to the data repositories. This option is most useful when the *ScanMode* is set to Enforce because it ensures all files will be scanned.
    
    Every hour, the policy is checked for changes and if necessary, downloaded. The new policy is used for the next scan cycle. You can also download the latest changes by restarting the service.

- Never: The service is stopped and does not scan, even if you try to manually start the Azure Information Protection Scanner service. This value is automatically set after a single scan is complete. To run a new scan, you must set the schedule to OneTime or Continuous.


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
Specifies whether the scanner maintains a list of previously scanned files so it can scan only new or modified files since the service started. This is the default behavior. 

If this list is not maintained, all files in the specified data repositories are scanned with each scanning cycle.

- Incremental: The scanner maintains a list of previously scanned files so it can scan only new or modified files. 
- Full: Each time the cycle finishes, all files in the specified data repositories are scanned again.


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

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

