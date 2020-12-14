---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 1D21A18B-1E3D-434C-A283-E65B810EF1B4
online version: https://go.microsoft.com/fwlink/?linkid=2044865
schema: 2.0.0
---

# Enable-AipServiceDevicePlatform

## SYNOPSIS
Enables protection support from Azure Information Protection for device platforms.

## SYNTAX

### AllPlatforms
```
Enable-AipServiceDevicePlatform [-All] [<CommonParameters>]
```

### Platforms
```
Enable-AipServiceDevicePlatform [-Windows] [-WindowsStore] [-WindowsPhone] [-Mac] [-iOS] [-Android] [-Web]
 [<CommonParameters>]
```

## DESCRIPTION
The **Enable-AipServiceDevicePlatform** cmdlet enables protection support from Azure Information Protection for device platforms. Your tenant can support any combination of the following device platforms:
- Android
- iOS
- Macintosh operating system
- Web
- Windows operating system
- Windows Phone
- Windows Store

To support all platforms, specify the **All** parameter.

You must use PowerShell to do this configuration; you cannot do this configuration by using a management portal.

## EXAMPLES

### Example 1: Enable protection support for device platforms
```
PS C:\>Enable-AipServiceDevicePlatform -WindowsPhone -WindowStore
```

This command enables protection support for device platforms for Windows Phone and Windows Store device platforms.

### Example 2: Enable protection support for all device platforms
```
PS C:\>Enable-AipServiceDevicePlatform -All
```

This command enables protection support for all device platforms.

## PARAMETERS

### -All
Indicates that the cmdlet specifies all device platforms. The cmdlet enables protection support for all device platforms.

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
Indicates that the cmdlet specifies the Android device platform. The cmdlet enables protection support for the specified device platform.

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
Indicates that the cmdlet specifies the Macintosh operating system device platform. The cmdlet enables protection support for the specified device platform.

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
Indicates that the cmdlet specifies the web device platform. The cmdlet enables protection support for the specified device platform.

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
Indicates that the cmdlet specifies the Windows operating system device platform. The cmdlet enables protection support for the specified device platform.

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
Indicates that the cmdlet specifies the Windows Phone device platform. The cmdlet enables protection support for the specified device platform.

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
Indicates that the cmdlet specifies the Windows Store device platform. The cmdlet enables protection support for the specified device platform.

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
Indicates that the cmdlet specifies the iOS device platform. The cmdlet enables protection support for the specified device platform.

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

[Get-AipServiceDevicePlatform](./Get-AipServiceDevicePlatform.md)