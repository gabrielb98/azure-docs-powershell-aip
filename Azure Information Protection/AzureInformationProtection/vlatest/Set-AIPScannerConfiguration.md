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

### Example 1: Sets Azure Information Protection Scanner to run one time discovery of configured repositories and create a report for newly discovered files since last run (Info repoting level)
```
PS C:\> Set-AIPScannerConfiguration -ScanMode Discover -Schedule OneTime -ReportLevel Info

Configuration was set successfully.
```

### Example 2: Sets Azure Information Protection Scanner to label and protect files (Enforce policy mode) and run on continous mode. 
```
PS C:\> Set-AIPScannerConfiguration -ScanMode Enforce -Schedule Continuous

Configuration was set successfully.
```

### Example 3: Sets Azure Information Protection Scanner to run scanning cycle in order to label and protect files using AIP policy and create detailed reports of changed and skipped files (Debug reporting level), and set  owner to admin@contoso.msft.
```
PS C:\> Set-AIPScannerConfiguration -ScanMode Enforce -Schedule OneTime -ReportLevel Debug -DefaultOwner admin@contoso.msft.

Configuration was set successfully.
```

### Example 4: Sets Azure Information Protection Scanner to run one time discovery of configured repositories and create a report for all files (full rescan)

```
PS C:\> Set-AIPScannerConfiguration -ScanMode Enforce -Schedule OneTime -ReportLevel Debug -Type Full

Configuration was set successfully.
```

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
Specifies whether to reclassify a file that's already classified. By default, the scanner reclassifies these files only when they have been classified by the current scanner account. 

To prevent this reclassification, set this parameter to Off. To reclassify files that have been classified by another account (for example, another classification solution), set this parameter to On. 


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
Specify whether to keep the following file attributes when a file is labeled, or overwrite them: The archive flag, Date Modified, and Owner.

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
Defines the level of logging for detailed report. 

Debug – includes the skipped items, useful for troubleshooting, but has a performance impact on Azure Information Protection Scanner.
Info – logs only files with applied action.
Error – logs errors only.
Off – disables reporting, best for performance.


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
Set to Discover to instruct Azure Information Protection Scanner to scan the repositories in “whatif” mode. In this mode scanner inspects the files and creates a report for discovered files without changing the files (no labeling or protection is applied).

Set to Enforce to instruct scanner to scan the repositories and apply AIP policy. In this mode scanner inspects the files, classifies them and applies labels and protection according to the defined AIP policy.


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
Set to OneTime for single scan. In this case Azure Information Protection Scanner scans the defined repositories one time and then the service is stopped.
This mode is useful for Discover mode that scans repository one time and prepares the report of discovered data.

Set to Continuous for continuous scan. In this case scanner service runs always and once the scan cycle passed through all files in the defined repositories the scanner starts the new scan cycle of the repositories.
This mode is useful for Enforce mode when continous labeling and protection of newly creatd files is required.


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
By default is set to Incermental, where Azure Information Protection Scanner maintains a list of already scanneed files and evaluates only newly created files or files that were changed since last scan cycle, in case the policy was not changed since last scan cycle. 
In order to initiate full rescan regardless of previuous scan or file timestampt set this paramter to Full.

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

