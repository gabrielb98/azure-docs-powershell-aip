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
 [-JustificationMessage <String>] [-DiscoverInformationTypes <DiscoverInformationTypes>] [<CommonParameters>]
```

## DESCRIPTION
The Set-AIPScannerConfiguration cmdlet sets optional configuration settings for the Azure Information Protection scanner. 

**For the general availability version:**

When you install the scanner, these settings are configured for you with their default installation values. Use this cmdlet to change the settings, which will be used the next time the scanner runs. If you need the changes to take effect immediately, restart the Azure Information Protection Scanner service on the Windows server computer.

The configuration settings include whether the scanner is in discovery mode only or applies labels, whether a file will be relabeled, whether file attributes are changed, what is logged in the reports, whether the scanner runs once or continuously, what justification message to use when required, and the Rights Management owner for protected files.

**For the preview version:**

The Set-AIPScannerConfiguration cmdlet sets local configuration settings for the Azure Information Protection scanner. You configure most of the scanner configuration settings in the Azure portal, but must use this cmdlet if you need to import configuration settings from a file because the scanner cannot support online configuration, or if you need to change the report level for the locally created reports.

Any changes will be used the next time the scanner runs. If you need the changes to take effect immediately, restart the Azure Information Protection Scanner service on the Windows server computer

## EXAMPLES

### Example 1: Configure the Azure Information Protection scanner for a manual schedule and create a report for files that would be labeled - general availability version
```
PS C:\> Set-AIPScannerConfiguration -Enforce Off -Schedule Manual -ReportLevel Info

Configuration was set successfully.
```

This command configures the scanner to run a one-time discovery for files in the specified data repositories, and then create a report that lists the files that meet the conditions to be labeled. The schedule is set to manual, so that you must manually start the service. For example, by running [Start-AIPScan](./Start-AIPScan.md).

Note that because these parameters specify the values that are set by the scanner installation, you need to specify them only if you previously specified other values.

### Example 2: Configure the Azure Information Protection scanner to continuously discover and label files - general availability version
```
PS C:\> Set-AIPScannerConfiguration -Enforce On -Schedule Always

Configuration was set successfully.
```

This command configures the scanner to continuously discover files in the specified data repositories and label the files that meet the conditions in the Azure Information Protection policy.

For these files, they are classified and protected (or have protection removed), according to the label configuration.

### Example 3: Configure the Azure Information Protection scanner to scan and label all files by using a manual schedule, and log all files - general availability version
```
PS C:\> Set-AIPScannerConfiguration -Enforce On -Schedule Manual -ReportLevel Debug

Configuration was set successfully.
```

This command configures the scanner to do a one-time discovery of all files in the specified data repositories and label the files that meet the conditions in the Azure Information Protection policy. The schedule is set to manual, so that you must manually start the service. For example, by running [Start-AIPScan](./Start-AIPScan.md).

For the files that are discovered, they are classified and protected (or have protection removed), according to the label configuration.

Every discovered file and the resulting action is logged in the reports.

### Example 4: Configure the Azure Information Protection scanner to scan all files and discover all known sensitive information types and custom conditions - general availability version

```
PS C:\> Set-AIPScannerConfiguration -Enforce Off -Schedule Manual -DiscoverInformationTypes All

Configuration was set successfully.
```

This command configures the scanner to do a one-time discovery of all files in the specified data repositories and detect all known sensitive information types that are recognized by the scanner as a result of custom conditions that you configure in the Azure Information Protection policy. The schedule is set to manual, so that you must manually start the service. For example, by running [Start-AIPScan](./Start-AIPScan.md).

Every file with a discovered information type or a matching custom condition is logged in the reports.

### Example 5: Set the Azure Information Protection scanner to use online configuration - preview version

```
PS C:\> Set-AIPScannerConfiguration -OnlineConfiguration On

Configuration was set successfully.
```

This command sets the scanner to get its configuration directly from the Azure Information Protection service.


## PARAMETERS

### -JustificationMessage
Note: This parameter is not available in the preview version of the scanner. Instead, use the [Azure portal to configure the scanner](/information-protection/deploy-aip-scanner-preview), and set **Relabel files** to **On**.

For the general availability version: Specify the justification reason for lowering the classification label or removing protection, if the Azure Information Protection policy requires users to supply this information.

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
Define the level of logging for the scanner reports. When the scanner is first installed, by default, only files that are successfully labeled by the scanner are included in the log file.

Log files are stored in the %localappdata%\Microsoft\MSIP\Scanner\Reports folder. A summary report (.txt) includes the time taken to scan, the number of scanned files, and statistics of how many files were classified and protected. Detailed reports (.csv) has details for each file. The folder stores up to 60 reports for each scanning cycle and all but the latest report is compressed to help minimize the required disk space.

- Debug: Logs every file that was discovered and the resulting action. This level of logging is useful for troubleshooting but slows down the Azure Information Protection scanner. This category includes files that don't meet any of the conditions and files that are skipped because of an unsupported file type. For example, trying to label a file for classification-only when the file type doesn't support this action, and trying to label files that are automatically excluded. For more information, see [File types supported by the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-file-types) from the admin guide.
- Info: Logs only the files that were successfully labeled by the scanner, or would be labeled when the scanner is in discovery mode.
- Error: Logs only the files that the scanner attempted to label but could not. For example, a file was in use, or the scanner service did not have write access to the file.
- Off: Disables reporting, which results in the best performance for the scanner.

The local Windows **Applications and Services** event log, **Azure Information Protection** contains additional logging information. The events include the start and end times for each scanning cycle, when a scanned file has a label applied, and when protection is applied or removed. For more information:

For the general availability version:

- [Event log IDs and descriptions for the scanner](https://docs.microsoft.com/information-protection/deploy-aip-scanner#event-log-ids-and-descriptions-for-the-scanner).

For the preview version:

- [Event log IDs and descriptions for the scanner](https://docs.microsoft.com/information-protection/deploy-aip-scanner-preview#event-log-ids-and-descriptions-for-the-scanner).

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
Note: This parameter is not available in the preview version of the scanner. Instead, use the [Azure portal to configure the scanner](https://docs.microsoft.com/information-protection/deploy-aip-scanner-preview).

For the general availability version: Specifies how often the scanner runs on the specified data repositories:

- Manual: A single scan, started manually. For example, by running [Start-AIPScan](./Start-AIPScan.md). When the schedule is set to manual and you want to run a new scan, you must rerun the Start-AIPScan cmdlet. This manual schedule option is useful when the *Enforce* parameter is set to Off, so that the scanner runs one time and you can check the results in the report.
- Always: The specified data repositories are repeatedly scanned in sequence and the Azure Information Protection Scanner service is not stopped. Use this option to scan for files that are modified or added to the data repositories. This option is most useful when the *Enforce* parameter is set to On because it ensures all files will be scanned. Every hour, the policy is checked for changes and if necessary, downloaded. The new policy is used for the next scan cycle. You can also download the latest changes by restarting the service.


```yaml
Type: Schedule
Parameter Sets: (All)
Aliases:
Accepted values: Manual, Always

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### -DiscoverInformationTypes
Note: This parameter is not available in the preview version of the scanner. Instead, use the [Azure portal to configure the scanner](https://docs.microsoft.com/information-protection/deploy-aip-scanner-preview).

For the general availability version: Specifies what patterns are detected by the scanner:

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
Note: This parameter is not available in the preview version of the scanner. Instead, use the [Azure portal to configure the scanner](/information-protection/deploy-aip-scanner-preview).

For the general availability version: Specifies whether the scanner only logs the files that meet the conditions in the Azure Information Protection policy without applying the corresponding label (the installation default setting), or applies the label:

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

### -OnlineConfiguration 
Note: This parameter is available only in the preview version of the scanner.

Specifies whether the scanner gets its configuration settings directly from the Azure Information Protection service (the default), or uses an offline configuration file.

- On: The default setting. The scanner gets its configuration settings directly from the Azure Information Protection service.

- Off: The scanner is prevented from getting its configuration settings directly from the Azure Information Protection service. Instead, the scanner is configured by settings that you import from a file. 

If the scanner cannot support online configuration, you must still configure the scanner in the Azure portal. Then, export the scanner configuration from the portal to a .json file and import this file by using the [Import-AIPScannerConfiguration](./Import-AIPScannerConfiguration.md) cmdlet.

```yaml
Type: OnlineConfiguration
Parameter Sets: (All)
Aliases:
```


### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.
For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Add-AIPScannerScannedFileTypes](Add-AIPScannerScannedFileTypes.md)

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)

[Get-AIPScannerStatus](./Get-AIPScannerStatus.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Remove-AIPScannerScannedFileTypes](./Remove-AIPScannerScannedFileTypes.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerRepository](./Set-AIPScannerRepository.md)

[Set-AIPScannerScannedFileTypes](./Set-AIPScannerRepository.md)

[Start-AIPScan](./Start-AIPScan.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Update-AIPScanner](./Update-AIPScanner.md)

