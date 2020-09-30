---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version:
schema: 2.0.0
---

# Remove-MIPScannerRepository

## SYNOPSIS
Removes a repository from an Azure Information Protection content scan job.

## SYNTAX

```
Remove-MIPScannerRepository
 [-Repositories] <System.Collections.Generic.List`1[Microsoft.InformationProtection.Powershell.AIP.Commandlets.Scanner.MoonCake.RepositoryInfo]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
Deletes any repositories described by the **Repositories** parameter, or returned by a piped [Get-MIPScannerRepository](Get-MIPScannerRepository.md) cmdlet.

For more information about content scan jobs, see the [Azure Information Protection on-premises scanner documentation](/information-protection/deploy-aip-scanner-configure-install#create-a-content-scan-job).

## EXAMPLES

### Example 1 Remove all repositories configured for your content scan job
```PowerShell
PS C:\WINDOWS\system32> Get-MIPScannerRepository | Remove-MIPScannerRepository
```

This example shows a fully piped cmdlet, where the repositories are first returned, and then deleted.

### Example 2 Remove a specific repository from your content scan job
```PowerShell
PS C:\WINDOWS\system32> Get-MIPScannerRepository -Path 'c:\repoToScan1' | Remove-MIPScannerRepository
```

This example shows a fully piped cmdlet, where the repository is first returned, and then deleted.

### Example 3 Remove any repositories that match a specific wildcard pattern from your content scan job
```PowerShell
PS C:\WINDOWS\system32> Get-MIPScannerRepository -Path 'c:\repo*' | Remove-MIPScannerRepository
```

This example shows a fully piped cmdlet, where the repositories are first returned, and then deleted.

### Example 4 Remove a specific repository from your content scan job without piping
```PowerShell
PS C:\WINDOWS\system32> $repos = Get-MIPScannerRepository -Path 'c:\repoToScan1'
PS C:\WINDOWS\system32> Remove-MIPScannerRepository $repos
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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.Collections.Generic.List`1[[Microsoft.InformationProtection.Powershell.AIP.Commandlets.Scanner.MoonCake.RepositoryInfo, AIP, Version=2.9.0.0, Culture=neutral, PublicKeyToken=null]]

## OUTPUTS

### System.Object
## NOTES

## RELATED LINKS

- [Add-MIPScannerRepository](Add-MIPScannerRepository.md)

- [Get-MIPScannerContentScanJob](Get-MIPScannerContentScanJob.md)

- [Get-MIPScannerRepository](Get-MIPScannerRepository.md)

- [Remove-MIPScannerContentScanJob](Remove-MIPScannerContentScanJob.md)

- [Set-MIPScannerContentScanJob](Set-MIPScannerContentScanJob.md)

- [Set-MIPScannerRepository](Set-MIPScannerRepository.md)