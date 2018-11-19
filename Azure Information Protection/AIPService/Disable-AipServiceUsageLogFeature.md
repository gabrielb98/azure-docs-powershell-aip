---
external help file: AIPService.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400600
schema: 2.0.0
ms.assetid: 469B8EE7-0EE9-4BD7-BC24-A3AD74111FB0
---

# Disable-AipServiceUsageLogFeature

## SYNOPSIS
Disables the protection usage log for Azure Information Protection.

## SYNTAX

```
Disable-AipServiceUsageLogFeature [<CommonParameters>]
```

## DESCRIPTION
The **Disable-AipServiceUsageLogFeature** cmdlet disables protection usage log for Azure Information Protection. If you disable this logging, the cmdlet does not delete existing logs. If you enable usage logging again, logging begins at the point in the log where logging previously stopped.

Note: This cmdlet is not needed and will not run successfully after the usage logging change in February 2016. After this date, usage logging for the protection service is automatically enabled and cannot be disabled; the only PowerShell cmdlet that you need for usage logging for protection is [Get-AipServiceUserLog](./Get-AipServiceUserLog.md).

For more information about usage logging for protection, see [Logging and analyzing usage of the Azure Information Protection protection service](https://docs.microsoft.com/information-protection/deploy-use/log-analyze-usage).

## EXAMPLES

### Example 1: Disable usage logging
```
PS C:\>Disable-AipServiceUsageLogFeature
```

This command disables the usage log for the protection service.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Enable-AipServiceUsageLogFeature](./Enable-AipServiceUsageLogFeature.md)

[Get-AipServiceUsageLogFeature](./Get-AipServiceUsageLogFeature.md)

[Logging and analyzing usage of the Azure Information Protection protection service](https://docs.microsoft.com/information-protection/deploy-use/log-analyze-usage)
