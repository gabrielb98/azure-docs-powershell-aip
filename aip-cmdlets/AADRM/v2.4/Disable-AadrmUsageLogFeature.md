---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400600
schema: 2.0.0
---

# Disable-AadrmUsageLogFeature

## SYNOPSIS
Disables the usage log for Rights Management.

## SYNTAX

```
Disable-AadrmUsageLogFeature [<CommonParameters>]
```

## DESCRIPTION
The Disable-AadrmUsageLogFeature cmdlet disables usage logging for Azure Rights Management.
If you disable this logging, the cmdlet does not delete existing logs.
If you enable usage logging again, logging begins at the point in the log where logging previously stopped.

Note: This cmdlet is not needed and will not run successfully after the usage logging change in February 2016.
After this date, usage logging is automatically enabled and cannot be disabled; the only Windows PowerShell cmdlet that you need for Azure RMS usage logging is Get-AadrmUserLog.

For more information about usage logging, see Logging and analyzing Azure Rights Management usage (https://docs.microsoft.com/rights-management/deploy-use/log-analyze-usage) on the Microsoft documentation site.

## EXAMPLES

### Example 1: Disable usage logging
```
PS C:\>Disable-AadrmUsageLogFeature
```

This command disables the usage log for your organization.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Enable-AadrmUsageLogFeature]()

[Get-AadrmUsageLogFeature]()

