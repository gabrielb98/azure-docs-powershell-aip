---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2053104
schema: 2.0.0
---

# Import-AIPScannerConfiguration

## SYNOPSIS
**Relevant for:** AIP unified labeling and classic clients

Imports local configuration for the Azure Information Protection scanner.

## SYNTAX

```
Import-AIPScannerConfiguration -FileName <String> [<CommonParameters>]
```

## DESCRIPTION
The **Import-AIPScannerConfiguration** cmdlet imports local configuration settings for the Azure Information Protection scanner, and automatically configures the scanner to use offline configuration. 

Use this cmdlet after you've configured the following in the Azure portal:

- Configured a cluster (unified labeling client only) or a profile
- Configured a content scan job for the scanner
- Exported the settings to a file instead of having the scanner connect to the Azure Information Protection service.

For example use this cmdlet when the computer running the scanner doesn't have Internet connectivity.

If you need to make configuration changes to the scanner after you have run this cmdlet, make those changes in the Azure portal, export the content scan job again, and rerun this cmdlet.

If you want to change the scanner to use online configuration after you have run this cmdlet, use the [Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md) and set the *OnlineConfiguration* parameter to **On**.

Any changes will be used the next time the scanner runs. If you need the changes to take effect immediately, restart the Azure Information Protection Scanner service on the Windows server computer.

> [!NOTE]
> To provide a unified and streamlined customer experience, the **Azure Information Protection classic client** and **Label Management** in the Azure Portal are being **deprecated** as of **March 31, 2021.** 
> 
> This time-frame allows all current Azure Information Protection customers to transition to our unified labeling solution using the Microsoft Information Protection Unified Labeling platform. Learn more in the official [deprecation notice](https://aka.ms/aipclassicsunset).
>


## EXAMPLES

### Example 1: Import local configuration settings for the Azure Information Protection scanner
```PowerShell
PS C:\> Import-AIPScannerConfiguration -FileName "C:\Scannerconfig\Eu-set.json"
Configuration was imported successfully.

```

The scanner is configured to prevent getting its configuration directly from the Azure Information Protection service, and the configuration settings are imported from a file named C:\Scannerconfig\Eu-set.json.

## PARAMETERS

### -FileName
Specifies a file that contains scanner configuration settings. To create this file, export your content scan job from the Azure portal.

The file is used to do a one-time import of configuration settings into the scanner configuration database.


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

[Update-AIPScanner](./Update-AIPScanner.md)