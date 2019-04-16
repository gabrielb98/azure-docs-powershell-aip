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
Update-AIPScanner [-Profile <String>] [<CommonParameters>]
```

## DESCRIPTION
The Update-AIPScanner cmdlet updates the database schema for the Azure Information Protection scanner and if required, the scanner service account is also granted delete permissions for the scanner database.

For more information about upgrading the scanner, see [Upgrading the Azure Information Protection scanner](https://docs.microsoft.com/azure/information-protection/rms-client/client-admin-guide#upgrading-the-azure-information-protection-scanner) from the admin guide.

Run this cmdlet with an account that has the database-level role of db_owner for the database that the scanner is using (named AzInfoProtectionScanner).

After the upgrade, the scanner changes how it gets its configuration settings. Instead of using PowerShell to configure the scanner locally, the scanner is now configured from the Azure Information Protection service, by using the Azure portal.

The scanner is not currently supported for the Azure Information Protection unified labeling client.

## EXAMPLES

### Example 1: Update the scanner after the Azure Information Protection client has been upgraded, and set a scanner profile name
```
PS C:\> Update-AIPScanner –profile USWEST
```

This command updates the database schema for the Azure Information Protection scanner, and sets the profile name to USWEST rather than use the default name of the computer. You are prompted to continue and if you confirm, the scanner then gets is configuration from the USWEST scanner profile that you configure by using the Azure portal.

The Azure Information Protection scanner is updated successfully, the scanner database is renamed to AIPScanner_USWEST, and the scanner now gets its configuration from the Azure Information Protection service. 

For reference purposes, a backup of your old configuration is stored in %localappdata%\Microsoft\MSIP\ScannerConfiguration.bak. 


## PARAMETERS

### -Profile 
Specifies the scanner profile name that contains the scanner configuration from the Azure Information Protection service. The scanner configuration database is updated to reflect the profile name that you specify. If you do not specify this parameter, the computer name is used as the profile name. 

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
For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

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