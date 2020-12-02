---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2144636
schema: 2.0.0
---

# Remove-AIPScannerContentScanJob

## SYNOPSIS
Delete a content scan job.

## SYNTAX

```
Remove-AIPScannerContentScanJob [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
Deletes an entire Azure Information Protection content scan job.

> [!CAUTION]
> Deleting the content scan job means that the configured repositories may not be scanned again, unless they are configured for a different content scan job.
> 

For more information about content scan jobs, see the [Azure Information Protection on-premises scanner documentation](/information-protection/deploy-aip-scanner-configure-install#create-a-content-scan-job).

> [!IMPORTANT]
> If you are using the AIP classic client, this cmdlet is deprecated. Instead, use the [Azure portal to configure the scanner](/information-protection/deploy-aip-scanner-classic).
> 

## EXAMPLES

### Example 1
```powershell
PS C:\> {{ Add example code here }}
```

{{ Add example description here }}

## PARAMETERS

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object
## NOTES

## RELATED LINKS

- [Add-AIPScannerRepository](Add-AIPScannerRepository.md)

- [Get-AIPScannerContentScanJob](Get-AIPScannerContentScanJob.md)

- [Get-AIPScannerRepository](Get-AIPScannerRepository.md)

- [Remove-AIPScannerRepository](Remove-AIPScannerRepository.md)

- [Set-AIPScannerContentScanJob](Set-AIPScannerContentScanJob.md)

- [Set-AIPScannerRepository](Set-AIPScannerRepository.md)