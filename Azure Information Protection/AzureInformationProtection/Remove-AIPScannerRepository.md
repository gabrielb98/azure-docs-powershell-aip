---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2144637
schema: 2.0.0
---

# Remove-AIPScannerRepository

## SYNOPSIS
**Relevant for:** Unified labeling client only. Deprecated for the classic client.

Removes a repository from an Azure Information Protection content scan job.

## SYNTAX

```
Remove-AIPScannerRepository
 [-Repositories] <System.Collections.Generic.List`1[Microsoft.InformationProtection.Powershell.AIP.Commandlets.Scanner.MoonCake.RepositoryInfo]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
Deletes any repositories described by the **Repositories** parameter, or returned by a piped [Get-AIPScannerRepository](Get-AIPScannerRepository.md) cmdlet.

For more information about content scan jobs, see the [Azure Information Protection on-premises scanner documentation](/information-protection/deploy-aip-scanner-configure-install#create-a-content-scan-job).

[!INCLUDE [This classic client cmdlet is deprecated](../includes/classic-client-deprecated-cmdlet.md)]

## EXAMPLES

### Example 1 Remove all repositories configured for your content scan job
```powershell
PS C:\WINDOWS\system32> Get-AIPScannerRepository | Remove-AIPScannerRepository
```

This example shows a fully piped cmdlet, where the repositories are first returned, and then deleted.

### Example 2 Remove a specific repository from your content scan job
```powershell
PS C:\WINDOWS\system32> Get-AIPScannerRepository -Path 'c:\repoToScan1' | Remove-AIPScannerRepository
```

This example shows a fully piped cmdlet, where the repository is first returned, and then deleted.

### Example 3 Remove any repositories that match a specific wildcard pattern from your content scan job
```powershell
PS C:\WINDOWS\system32> Get-AIPScannerRepository -Path 'c:\repo*' | Remove-AIPScannerRepository
```

This example shows a fully piped cmdlet, where the repositories are first returned, and then deleted.

### Example 4 Remove a specific repository from your content scan job without piping
```powershell
PS C:\WINDOWS\system32> $repos = Get-AIPScannerRepository -Path 'c:\repoToScan1'
PS C:\WINDOWS\system32> Remove-AIPScannerRepository $repos
```

This example shows a fully piped cmdlet, where the repositories are first returned, and then deleted.

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

### -Repositories
Describes the repositories you want to delete. For example, see [Example 4 Remove a specific repository from your content scan job without piping](#example-4-remove-a-specific-repository-from-your-content-scan-job-without-piping).

```yaml
Type: System.Collections.Generic.List`1[Microsoft.InformationProtection.Powershell.AIP.Commandlets.Scanner.MoonCake.RepositoryInfo]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. 

For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

### System.Collections.Generic.List`1[[Microsoft.InformationProtection.Powershell.AIP.Commandlets.Scanner.MoonCake.RepositoryInfo, AIP, Version=2.9.0.0, Culture=neutral, PublicKeyToken=null]]

## OUTPUTS

### System.Object
## NOTES

## RELATED LINKS

- [Add-AIPScannerRepository](Add-AIPScannerRepository.md)

- [Get-AIPScannerContentScanJob](Get-AIPScannerContentScanJob.md)

- [Get-AIPScannerRepository](Get-AIPScannerRepository.md)

- [Remove-AIPScannerContentScanJob](Remove-AIPScannerContentScanJob.md)

- [Set-AIPScannerContentScanJob](Set-AIPScannerContentScanJob.md)

- [Set-AIPScannerRepository](Set-AIPScannerRepository.md)