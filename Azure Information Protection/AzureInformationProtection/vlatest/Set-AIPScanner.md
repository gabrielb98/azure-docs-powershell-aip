---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=858209
schema: 2.0.0
---

# Set-AIPScanner

## SYNOPSIS
Sets Azure Information Protection Scanner service account and DB instance

## SYNTAX

```
Set-AIPScanner [[-SqlServerInstance] <String>] [-ServiceUserCredentials] <PSCredential>
```

## DESCRIPTION
The Set-AIPScanner cmdlet updates Azure Information Protection Scanner service account and DB instance. The command is used to change Azure Information Protection Scanner service account and DB instance used by the service.

## EXAMPLES

### Example 1: Changes Azure Information Protection Scanner DB to SERVER1\AIPSCANNER
```
PS C:\> Set-AIPScanner -SqlServerInstance SERVER1\AIPSCANNER
```
Azure Information Protection Scanner service configuration change completed successfully.

## PARAMETERS

### -ServiceUserCredentials
Credential object for a user name and password used to run Azure Information Protection Scanner service. Domain\Username format should be used when prompted for user credentials.

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases: 

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SqlServerInstance
SQL Instance details used by Azure Information Protection Scanner as DB. Local or remote instance can be used to host Azure Information Protection Scanner DB. Supported version: SQL Express, Standard or Enterprise, version 2012 R2 and above. For local default instance use servername. For named instance use servername\sqlinstance_name. For SQL express instance use servername\SQLEXPRESS.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Add-AIPScannerRepository](./Add-AIPScannerRepository.md)

[Install-AIPScanner](./Install-AIPScanner.md)

[Set-AIPScannerConfiguration](./Set-AIPScannerConfiguration.md)

[Get-AIPScannerConfiguration](./Get-AIPScannerConfiguration.md)

[Uninstall-AIPScanner](./Uninstall-AIPScanner.md)

[Remove-AIPScannerRepository](./Remove-AIPScannerRepository.md)

[Get-AIPScannerRepository](./Get-AIPScannerRepository.md)
