---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 56F5DDA0-7EFE-4B9B-BE34-4052DC5968B2
online version: https://go.microsoft.com/fwlink/?linkid=2045122
schema: 2.0.0
---

# Disable-AipServiceDevicePlatform

## SYNOPSIS
Disables protection support from Azure Information Protection for device platforms.

## SYNTAX

### AllPlatforms
```
Disable-AipServiceDevicePlatform [-All] [<CommonParameters>]
```

### Platforms
```
Disable-AipServiceDevicePlatform [-Windows] [-WindowsStore] [-WindowsPhone] [-Mac] [-iOS] [-Android] [-Web]
 [<CommonParameters>]
```

## DESCRIPTION
The **Disable-AipServiceDevicePlatform** cmdlet disables protection support from Azure Information Protection for device platforms. For information about supported device platforms, see the [Enable-AipServiceDevicePlatform](./Enable-AipServiceDevicePlatform.md) cmdlet.

You must use PowerShell to do this configuration; you cannot do this configuration by using a management portal.

## EXAMPLES

### Example 1: Disable protection support for device platforms
```
PS C:\>Disable-AipServiceDevicePlatform -WindowsPhone -WindowStore
```

This command disables protection support for Windows Phone and Windows Store device platforms.

### Example 2: Disable protection support for all device platforms
```
PS C:\>Disable-AipServiceDevicePlatform -All
```

This command disables protection support for all device platforms.

## PARAMETERS

### -All
Indicates that the cmdlet specifies all device platforms. The cmdlet disables protection support for all device platforms.

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
Indicates that the cmdlet specifies the Android device platform. The cmdlet disables protection support for the specified device platform.

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
Indicates that the cmdlet specifies the Macintosh operating system device platform. The cmdlet disables protection support for the specified device platform.

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
Indicates that the cmdlet specifies the web device platform. The cmdlet disables protection support for the specified device platform.

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
Indicates that the cmdlet specifies the Windows operating system device platform. The cmdlet disables protection support for the specified device platform.

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
Indicates that the cmdlet specifies the Windows Phone device platform. The cmdlet disables protection support for the specified device platform.

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
Indicates that the cmdlet specifies the Windows Store device platform. The cmdlet disables protection support for the specified device platform.

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
Indicates that the cmdlet specifies the iOS device platform. The cmdlet disables protection support for the specified device platform.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Enable-AipServiceDevicePlatform](./Enable-AipServiceDevicePlatform.md)

[Get-AipServiceDevicePlatform](./Get-AipServiceDevicePlatform.md)
