---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2004271
schema: 2.0.0
---

# Update-AIPScanner

## SYNOPSIS
Updates the database schema for the Azure Information Protection scanner.

**Relevant for:** AIP unified labeling and classic clients

## SYNTAX

```
Update-AIPScanner [-Cluster | -Profile <String>] [-Force] [<CommonParameters>]
```

## DESCRIPTION
The **Update-AIPScanner** cmdlet updates the database schema for the Azure Information Protection scanner and if required, the scanner service account is also granted delete permissions for the scanner database. 

Run this cmdlet after upgrading your Azure Information Protection client.

**Unified labeling client support**
   
The current version of the unified labeling client includes a preview version of the scanner that you can install for testing. 

For more information, see [Installing the Azure Information Protection scanner](/azure/information-protection/rms-client/clientv2-admin-guide#installing-the-azure-information-protection-scanner.md) from the admin guide for the unified labeling client.
    
Run this cmdlet with an account that has the database-level role of **db_owner** for the configuration database that the scanner is using, named **AIPScannerUL_\<cluster_name>.**

**Classic client support**

For more information about upgrading the scanner for the Azure Information Protection classic client, see [Upgrading the Azure Information Protection scanner](/azure/information-protection/rms-client/client-admin-guide#upgrading-the-azure-information-protection-scanner) from the admin guide.
    
Run this cmdlet with an account that has the database-level role of **db_owner** for the configuration database that the scanner is using:

- **For version 1.41.51.0:** This database is named **AzInfoProtectionScanner.**
- **For version 1.48.204.0:** This database is named **AIPScanner_\<profile_name>.**
    
If you are upgrading from versions before 1.48.204.0, after the upgrade, the scanner changes how it gets its configuration settings. Instead of using PowerShell to configure the scanner locally, the scanner is now configured from the Azure Information Protection service, by using the Azure portal.

> [!NOTE]
> To provide a unified and streamlined customer experience, the **Azure Information Protection classic client** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021.** 
> 
> This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).

## EXAMPLES

### Example 1: Update the scanner after the Azure Information Protection classic client has been upgraded, and set a scanner cluster  name
```
PS C:\> Update-AIPScanner –cluster USWEST
```

This command updates the database schema for the Azure Information Protection scanner, and sets the cluster name to **USWEST** rather than use the default name of the computer. 

You are prompted to continue and if you confirm, the scanner then gets is configuration from the **USWEST** scanner cluster that you configure by using the Azure portal.

The Azure Information Protection scanner is updated successfully, the scanner database is renamed to **AIPScanner_USWEST,** and the scanner now gets its configuration from the Azure Information Protection service. 

For reference purposes, a backup of your old configuration is stored in **%localappdata%\Microsoft\MSIP\ScannerConfiguration.bak.** 


## PARAMETERS


### -Cluster
**Relevant for**: Unified labeling client only.

Specifies the configured name of the scanner's database, used to identify the scanner you want to update.

Use the following syntax: **AIPScannerUL_<cluster_name>.** 

Using either this parameter or the **Profile** parameter is mandatory. Starting in version 2.7.0.0 of the unified labeling client, we recommend using this parameter instead of the **Profile** parameter.


```yaml 
Type: String 
Parameter Sets: (All) 
Position: Named 
Default value: None 
Accept pipeline input: False 
Accept wildcard characters: False 
```

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
Specifies the configured name of the scanner's database, used to identify the scanner you want to update.

- **Unified labeling client**: Using either this parameter or the **Cluster** parameter is mandatory. Starting in version 2.7.0.0 of the unified labeling client, we recommend using the **Cluster** parameter instead of the this parameter.

    The database name for the scanner is **AIPScannerUL_\<profile_name>.** 

- **Classic client**: This parameter is optional. 

    - If it's not specified, the default database is used, which is **AIPScanner_\<computer_name>.** 

    - When you specify a profile name with this parameter, the database name for the scanner has the following syntax: **AIPScanner_\<profile_name>.**


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