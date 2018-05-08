---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=858205
schema: 2.0.0
---

# Set-AIPScannerConfiguration

## SYNOPSIS
Sets optional configuration for the Azure Information Protection scanner.

## SYNTAX

```
Set-AIPScannerConfiguration [-Enforce <EnforceMode>] [-ReportLevel <ReportLevel>] [-Schedule <Schedule>]
 [-JustificationMessage <String>] [-Type <ScanType>] [-DiscoverInformationTypes <DiscoverInformationTypes>]
 [<CommonParameters>]
```

## DESCRIPTION
The Set-AIPScannerConfiguration cmdlet sets optional configuration settings for the Azure Information Protection scanner. When you install the scanner, these settings are configured for you with their default installation values. Use this cmdlet to change the settings, which will be used the next time the scanner runs. If you need the changes to take effect immediately, restart the Azure Information Protection Scanner service on the Windows server computer.

The configuration settings include whether the scanner is in discovery mode only or applies labels, whether a file will be relabeled, whether file attributes are changed, what is logged in the reports, whether the scanner runs once or continuously, what justification message to use when required, and the Rights Management owner for protected files.

## EXAMPLES

### Example 1: Configure the Azure Information Protection scanner to run a one-time discovery and create a report for files that would be labeled
```
PS C:\> Set-AIPScannerConfiguration -Enforce Off -Schedule OneTime -ReportLevel Info

Configuration was set successfully.
```

This command configures the scanner to run a one-time discovery for files in the specified data repositories, and then create a report that lists the files that meet the conditions to be labeled.

Note that because these parameters specify the values that are set by the scanner installation, you need to specify them only if you previously specified other values.

### Example 2: Configure the Azure Information Protection scanner to continuously discover and label files
```
PS C:\> Set-AIPScannerConfiguration -Enforce On -Schedule Continuous

Configuration was set successfully.
```

This command configures the scanner to continuously discover files in the specified data repositories and label the files that meet the conditions in the Azure Information Protection policy.

For these files, they are classified and protected (or have protection removed), according to the label configuration.

### Example 3: Configure the Azure Information Protection scanner to scan and label all files one time, and log all files
```
PS C:\> Set-AIPScannerConfiguration -Enforce On -Schedule OneTime -ReportLevel Debug -Type Full

Configuration was set successfully.
```

This command configures the scanner to do a one-time discovery of all files in the specified data repositories and label the files that meet the conditions in the Azure Information Protection policy.

For these files, they are classified and protected (or have protection removed), according to the label configuration.

Every discovered file and the resulting action is logged in the reports.

### Example 4: Configure the Azure Information Protection scanner to scan all files one time and discover all known sensitive information types and custom conditions
```
PS C:\> Set-AIPScannerConfiguration -Enforce Off -Schedule OneTime  -Type Full -DiscoverInformationTypes All

Configuration was set successfully.
```

This command configures the scanner to do a one-time discovery of all files in the specified data repositories and detect all known sensitive information types that are recognized by the scanner as a result of custom conditions that you configure in the Azure Information Protection policy.

Every file with discovered information type or a matching custom condition is logged in the reports.

## PARAMETERS

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

### -ReportLevel
Define the level of logging for the scanner reports.
When the scanner is first installed, by default, only files that are successfully labeled by the scanner are included in the log file.

Log files are stored in %localappdata%\Microsoft\MSIP\Scanner\Reports and have a .csv file format. They include the time taken to scan, the number of scanned files, and statistics of how many files were classified and protected. This folder stores up to 60 reports for each scanning cycle and all but the latest report is compressed to help minimize the required disk space.

- Debug: Logs every file that was discovered and the resulting action. This level of logging is useful for troubleshooting but slows down the Azure Information Protection scanner. This category includes files that don't meet any of the conditions and files that are skipped because of an unsupported file type. For example, trying to label a file for classification-only when the file type doesn't support this action, and trying to label files that are automatically excluded. [File types supported by the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-file-types) from the admin guide.
- Info: Logs only the files that were successfully labeled by the scanner, or would be labeled when the scanner is in discovery mode.
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
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Schedule
Specifies how often the scanner runs on the specified data repositories:

- OneTime: A single scan, after which the Azure Information Protection Scanner service is stopped and the schedule is then automatically set to Never. To run a new scan, you must change the schedule back to OneTime, or Continuous. This option is useful when the ScanMode is set to Discover, so that the scanner runs one time and you can check the results in the report.
- Continuous: The specified data repositories are repeatedly scanned in sequence and the Azure Information Protection Scanner service is not stopped. Use this option to scan for files that are modified or added to the data repositories. This option is most useful when the ScanMode is set to Enforce because it ensures all files will be scanned.Every hour, the policy is checked for changes and if necessary, downloaded. The new policy is used for the next scan cycle. You can also download the latest changes by restarting the service.
- Never: The service is stopped and does not scan, even if you try to manually start the Azure Information Protection Scanner service. This value is automatically set after a single scan is complete. To run a new scan, you must set the schedule to OneTime or Continuous.

```yaml
Type: Schedule
Parameter Sets: (All)
Aliases:
Accepted values: OneTime, Continuous, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type
Specifies whether the scanner maintains a list of previously scanned files so it can scan only new or modified files since the service started. This is the default installation behavior and offers the best performance.

If this list is not maintained, all files in the specified data repositories are scanned with each scanning cycle.

- Incremental: The scanner maintains a list of previously scanned files so it can scan only new or modified files.
- Full: All files in the specified data repositories are scanned, after which this parameter is automatically set to Incremental. To scan all files again, you must change this parameter to Full. This setting is most useful when you want all files to be listed in the reports.


### -DiscoverInformationTypes
Specifies what patterns are detected by the scanner:
 
- PolicyOnly: The scanner uses the conditions (predefined information types and custom) that you have specified for labels in the Azure Information Protection policy. 
- All: The scanner uses any custom conditions that you have specified for labels in the Azure Information Protection policy, and the list of information types that are available to specify for labels in the Azure Information Protection policy. When you use this option, labels do not need to be configured for any conditions.

Use PolicyOnly for better performance and you known what patterns to detect. For this option, you must define conditions for your Azure Information Protection labels that apply for automatic classification.

Use All if you want to detect all known patterns. However, this setting can result in slower performance and longer scanning times for the scanner.

yaml
Type: DiscoverInformationTypes
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False


### -Enforce
Specifies whether the scanner only logs the files that meet the conditions in the Azure Information Protection policy without applying the corresponding label (the installation default setting), or applies the label:

- Off: Scans the data repositories in the "what if" mode, to log results only, without setting the classification or protection that the corresponding label would apply.

- On: Scans the data repositories, and for files that meet the conditions, apply the corresponding label to set the classification and optionally, protection.

yaml
Type: EnforceMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
``````yaml
Type: ScanType
Parameter Sets: (All)
Aliases:
Accepted values: Incremental, Full

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DiscoverInformationTypes
Specifies what patterns are detected by the scanner: 

- PolicyOnly: The scanner uses the conditions (predefined information types and custom) that you have specified for labels in the Azure Information Protection policy. 
- All: The scanner uses any custom conditions that you have specified for labels in the Azure Information Protection policy, and the list of information types that are available to specify for labels in the Azure Information Protection policy. When you use this option, labels do not need to be configured for any conditions.

Use PolicyOnly for better performance and you known what patterns to detect. For this option, you must define conditions for your Azure Information Protection labels that apply for automatic classification.

Use All if you want to detect all known patterns. However, this setting can result in slower performance and longer scanning times for the scanner. 

```yaml
Type: DiscoverInformationTypes
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Enforce
Specifies whether the scanner only logs the files that meet the conditions in the Azure Information Protection policy without applying the corresponding label (the installation default setting), or applies the label: 

- Off: Scans the data repositories in the "what if" mode, to log results only, without setting the classification or protection that the corresponding label would apply.

- On: Scans the data repositories, and for files that meet the conditions, apply the corresponding label to set the classification and optionally, protection.


```yaml
Type: EnforceMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

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

[Set-AIPScannerRepository](./Set-AIPScannerRepository.md) 

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md) 

