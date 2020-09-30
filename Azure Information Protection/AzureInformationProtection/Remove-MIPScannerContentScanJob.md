---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version:
schema: 2.0.0
---

# Remove-MIPScannerContentScanJob

## SYNOPSIS
Delete a content scan job.

## SYNTAX

```
Remove-MIPScannerContentScanJob [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
Deletes an entire Azure Information Protection content scan job.

> [!CAUTION]
> Deleting the content scan job means that the configured repositories may not be scanned again, unless they are configured for a different content scan job.
> 

For more information about content scan jobs, see the [Azure Information Protection on-premises scanner documentation](/information-protection/deploy-aip-scanner-configure-install#create-a-content-scan-job).

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

- [Add-MIPScannerRepository](Add-MIPScannerRepository.md)

- [Get-MIPScannerContentScanJob](Get-MIPScannerContentScanJob.md)

- [Get-MIPScannerRepository](Get-MIPScannerRepository.md)

- [Remove-MIPScannerRepository](Remove-MIPScannerRepository.md)

- [Set-MIPScannerContentScanJob](Set-MIPScannerContentScanJob.md)

- [Set-MIPScannerRepository](Set-MIPScannerRepository.md)