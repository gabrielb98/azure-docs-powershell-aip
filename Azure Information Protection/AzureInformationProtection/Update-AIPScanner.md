---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2004271
schema: 2.0.0
---

# Update-AIPScanner

## SYNOPSIS
Updates the database schema for the Azure Information Protection scanner.

## SYNTAX

```
Update-AIPScanner [-Profile | -Cluster <String>] [<CommonParameters>]
```

## DESCRIPTION
The Update-AIPScanner cmdlet updates the database schema for the Azure Information Protection scanner and if required, the scanner service account is also granted delete permissions for the scanner database. Run this cmdlet after upgrading your Azure Information Protection client.

- To run this cmdlet for the Azure Information Protection client (classic):
    
    For more information about upgrading the scanner for the Azure Information Protection client (classic), see [Upgrading the Azure Information Protection scanner](/azure/information-protection/rms-client/client-admin-guide#upgrading-the-azure-information-protection-scanner) from the admin guide.
    
    Run this cmdlet with an account that has the database-level role of db_owner for the configuration database that the scanner is using:
    - For version 1.41.51.0: This database is named AzInfoProtectionScanner.
    - For version 1.48.204.0: This database is named AIPScanner_\<cluster_name (profile_name)>.
    
    If you are upgrading from versions before 1.48.204.0, after the upgrade, the scanner changes how it gets its configuration settings. Instead of using PowerShell to configure the scanner locally, the scanner is now configured from the Azure Information Protection service, by using the Azure portal.

- To run this cmdlet for the Azure Information Protection unified labeling client:
    
    The current version of this client includes a preview version of the scanner that you can install for testing. For more information, see [Installing the Azure Information Protection scanner](/azure/information-protection/rms-client/clientv2-admin-guide#installing-the-azure-information-protection-scanner.md) from the admin guide for the unified labeling client.
    
    Run this cmdlet with an account that has the database-level role of db_owner for the configuration database that the scanner is using, named AIPScannerUL_\<cluster_name(profile_name)>.

## EXAMPLES

### Example 1: Update the scanner after the Azure Information Protection client (classic) has been upgraded, and set a scanner cluster (profile) name
```
PS C:\> Update-AIPScanner –profile USWEST
```

This command updates the database schema for the Azure Information Protection scanner, and sets the cluster (profile) name to USWEST rather than use the default name of the computer. You are prompted to continue and if you confirm, the scanner then gets is configuration from the USWEST scanner cluster (profile) that you configure by using the Azure portal.

The Azure Information Protection scanner is updated successfully, the scanner database is renamed to AIPScanner_USWEST, and the scanner now gets its configuration from the Azure Information Protection service. 

For reference purposes, a backup of your old configuration is stored in %localappdata%\Microsoft\MSIP\ScannerConfiguration.bak. 


## PARAMETERS

### -Cluster

> [!NOTE]
>  This parameter is required for the scanner from the unified labeling client. From version 2.7.0.0, we recommend using Cluster switch instead of Profile switch.

Specifies the scanner cluster (profile) name that contains the scanner configuration of the Azure Information Protection service. The scanner configuration database is updated to reflect the cluster (profile) name that you specify. 

If you do not specify this parameter for the Azure Information Protection client (classic), the computer name is used as the cluster (profile) name.

### -Force
Forces the command to run without asking for user confirmation.

When used, the command first verifies that all nodes under the same cluster are offline. If any nodes are found to be online, a warning is displayed with the node details.

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
### -Profile 
Note: This parameter is required for the scanner from the unified labeling client. From version 2.7.0.0, we recommend using Cluster switch instead of Profile switch.

Specifies the scanner profile name that contains the scanner configuration from the Azure Information Protection service. The scanner configuration database is updated to reflect the profile name that you specify. If you do not specify this parameter for the Azure Information Protection client (classic), the computer name is used as the profile name. 

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

```yaml 
Type: String 
Parameter Sets: (All) 
Position: Named 
Default value: None 
Accept pipeline input: False 
Accept wildcard characters: False 
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.
For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Get-AIPScannerStatus](./Get-AIPScannerStatus.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Set-AIPScanner](./Set-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Start-AIPScan](./Start-AIPScan.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)