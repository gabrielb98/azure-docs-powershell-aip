---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400597
schema: 2.0.0
ms.assetid: 56F5DDA0-7EFE-4B9B-BE34-4052DC5968B2
---

# Disable-AadrmDevicePlatform

## SYNOPSIS
Disables Rights Management support for device platforms.

## SYNTAX

### AllPlatforms
```
Disable-AadrmDevicePlatform [-All] [<CommonParameters>]
```

### Platforms
```
Disable-AadrmDevicePlatform [-Windows] [-WindowsStore] [-WindowsPhone] [-Mac] [-iOS] [-Android] [-Web]
 [<CommonParameters>]
```

## DESCRIPTION
The **Disable-AadrmDevicePlatform** cmdlet disables Azure Rights Management support for device platforms.
For information about supported device platforms, see the Enable-AadrmDevicePlatform cmdlet.

## EXAMPLES

### Example 1: Disable Rights Management support for device platforms
```
PS C:\>Disable-AadrmDevicePlatform -WindowsPhone -WindowStore
```

This command disables Rights Management support for Windows Phone and Windows Store device platforms.

### Example 2: Disable Rights Management support for all device platforms
```
PS C:\>Disable-AadrmDevicePlatform -All
```

This command disables Rights Management support for all device platforms.

## PARAMETERS

### -All
Indicates that the cmdlet specifies all device platforms.
The cmdlet disables Rights Management support for all device platforms.

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
Indicates that the cmdlet specifies the Android device platform.
The cmdlet disables Rights Management support for the specified device platform.

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
Indicates that the cmdlet specifies the iOS device platform.
The cmdlet disables Rights Management support for the specified device platform.

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
Indicates that the cmdlet specifies the Macintosh operating system device platform.
The cmdlet disables Rights Management support for the specified device platform.

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
Indicates that the cmdlet specifies the web device platform.
The cmdlet disables Rights Management support for the specified device platform.

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
Indicates that the cmdlet specifies the Windows operating system device platform.
The cmdlet disables Rights Management support for the specified device platform.

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
Indicates that the cmdlet specifies the Windows Phone device platform.
The cmdlet disables Rights Management support for the specified device platform.

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
Indicates that the cmdlet specifies the Windows Store device platform.
The cmdlet disables Rights Management support for the specified device platform.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Enable-AadrmDevicePlatform](.\Enable-AadrmDevicePlatform.md)

[Get-AadrmDevicePlatform](.\Get-AadrmDevicePlatform.md)


