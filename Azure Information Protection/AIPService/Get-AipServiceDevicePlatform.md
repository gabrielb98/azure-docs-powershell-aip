---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 6E60214B-4051-48B3-A59C-5E4587A0025B
online version: https://go.microsoft.com/fwlink/?linkid=2045055
schema: 2.0.0
---

# Get-AipServiceDevicePlatform

## SYNOPSIS
Gets the device platforms in your organization that support the protection service from Azure Information Protection.

## SYNTAX

### AllPlatforms
```
Get-AipServiceDevicePlatform [-All] [<CommonParameters>]
```

### Platforms
```
Get-AipServiceDevicePlatform [-Windows] [-WindowsStore] [-WindowsPhone] [-Mac] [-iOS] [-Android] [-Web]
 [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceDevicePlatform** cmdlet gets the device platforms in your organization that support the protection service from Azure Information Protection. For information about supported device platforms, see the [Enable-AipServiceDevicePlatform](./Enable-AipServiceDevicePlatform.md) cmdlet.

You must use PowerShell to view this configuration; you cannot view this configuration by using a management portal.

## EXAMPLES

### Example 1: Get specific device platforms that support the protection service
```
PS C:\>Get-AipServiceDevicePlatform -WindowsPhone -WindowStore
       Key                                                       Value
       -----                                                     ------
       WindowsStore                                              True
       WindowsPhone                                              True
```

This command determines whether Windows Phone and Windows Store device platforms in your organization support the protection service from Azure Information Protection.

### Example 2: Get all device platforms that support the protection service
```
PS C:\>Get-AipServiceDevicePlatform -All
```

This command determines which of all device platforms in your tenant support the protection service from Azure Information Protection.

## PARAMETERS

### -All
Indicates that the cmdlet specifies all device platforms. The cmdlet gets the protection support status of all device platforms.

```yaml
Type: SwitchParameter
Parameter Sets: AllPlatforms
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Android
Indicates that the cmdlet specifies the Android device platform. The cmdlet gets the protection support status for the specified device platform.

```yaml
Type: SwitchParameter
Parameter Sets: Platforms
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Mac
Indicates that the cmdlet specifies the Macintosh operating system device platform. The cmdlet gets the protection support status for the specified device platform.

```yaml
Type: SwitchParameter
Parameter Sets: Platforms
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Web
Indicates that the cmdlet specifies the web device platform. The cmdlet gets the protection support status for the specified device platform.

```yaml
Type: SwitchParameter
Parameter Sets: Platforms
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Windows
Indicates that the cmdlet specifies the Windows operating system device platform. The cmdlet gets the protection support status for the specified device platform.

```yaml
Type: SwitchParameter
Parameter Sets: Platforms
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WindowsPhone
Indicates that the cmdlet specifies the Windows Phone device platform. The cmdlet gets the protection support status for the specified device platform.

```yaml
Type: SwitchParameter
Parameter Sets: Platforms
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WindowsStore
Indicates that the cmdlet specifies the Windows Store device platform. The cmdlet gets the protection support status for the specified device platform.

```yaml
Type: SwitchParameter
Parameter Sets: Platforms
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -iOS
Indicates that the cmdlet specifies the iOS device platform. The cmdlet gets the protection support status for the specified device platform.

```yaml
Type: SwitchParameter
Parameter Sets: Platforms
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

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AipServiceDevicePlatform](./Disable-AipServiceDevicePlatform.md)

[Enable-AipServiceDevicePlatform](./Enable-AipServiceDevicePlatform.md)