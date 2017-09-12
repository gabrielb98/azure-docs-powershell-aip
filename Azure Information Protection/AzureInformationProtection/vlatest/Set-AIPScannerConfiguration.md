---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=838766
schema: 2.0.0
---

# Set-AIPScannerConfiguration

## SYNOPSIS
Sets Azure Information Protection Scanner service optional configuration. The configuration will be used in next scanner cycle. Restart the Azure Information Protection Scanner service in order to apply changes immediately.

## SYNTAX

```
Set-AIPScannerConfiguration [-ScanMode <ScanMode>] [-OverrideLabel <OverrideLabel>]
 [-PreserveFileDetails <PreserveFileDetails>] [-ReportLevel <ReportLevel>] [-Schedule <Schedule>]
 [-JustificationMessage <String>] [-DefaultOwner <String>] [-Type <ScanType>]
```

## DESCRIPTION
The Set-AIPScannerConfiguration cmdlet sets optional Azure Information Protection Scanner configuration: scan mode, schedule, label override settings, reclassificaion justification message, fiel details preservation settings, report level and default owner.

## EXAMPLES

### Example 1: Sets Azure Information Protection Scanner to run one time discovery of configured repositories and create a report for newly discovered files since last run (Info repoting level)
```
PS C:\> Set-AIPScannerConfiguration -ScanMode Discover -Schedule OneTime -ReportLevel Info
```
Configuration was set successfully.
```

### Example 2: Sets Azure Information Protection Scanner to label and protect files (Enforce policy mode) and run on continous mode. 
```
PS C:\> Set-AIPScannerConfiguration -ScanMode Enforce -Schedule Continuous
```
Configuration was set successfully.
```

### Example 3: Sets Azure Information Protection Scanner to run scanning cycle in order to label and protect files using AIP policy and create detailed reports of changed and skipped files (Debug reporting level), and set  owner to admin@contoso.msft.
```
PS C:\> Set-AIPScannerConfiguration -ScanMode Enforce -Schedule OneTime -ReportLevel Debug -DefaultOwner admin@contoso.msft.
```
Configuration was set successfully.
```

### Example 4: Sets Azure Information Protection Scanner to run one time discovery of configured repositories and create a report for all files (full rescan)
```
PS C:\> Set-AIPScannerConfiguration -ScanMode Enforce -Schedule OneTime -ReportLevel Debug -Type Full
```
Configuration was set successfully.
```

## PARAMETERS

### -DefaultOwner
For files stored in SharePoint scanner uses SharePoint author property to set RMS owner of the file. For files without author or for files stored on other repositories (shares or local fodlers) scanner sets service account as an owner if DefaultOwner is not set.
In order to set scanner to use another account as owner for files without author field or for scanned files via CIFS or local files set desired owner’s email using parameter. Use "" in order to remove default owner


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
Azure Information Protection Scanner can downgrade senstivity level of the file. This setting is required in order to enable Azure Information Protection Scanner to be able to lower sensitivity level and if your policy requires justification for this action. The justification specified in this parameter will be logged as a justification message for files that were reclassified by a scaner to a lower sensitivity level.

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
Defines if the scanner reapplies the label and its action on already labeled files.
By default, scanner reclassifies only files that were classified by scanner itself.

In order to enable scanner to reclassify files previously classified by another account set this parameter to On.


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
Set to On in order to preserve file attributes, like archive flag, Date Modified and Owner for the labeled and protected files.

Set to Off if you want to reflect the change of the file in the attributes listed above


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

