---
external help file: AIP.dll-Help.xml
Module Name: AzureInformationProtection
online version: https://go.microsoft.com/fwlink/?linkid=2092526
schema: 2.0.0
---

# New-AIPCustomPermissions

## SYNOPSIS
Creates an ad-hoc protection policy for custom permissions.

## SYNTAX

```
New-AIPCustomPermissions -Users <String[]> -Permissions <Permissions> [-ExpirationDate <DateTime>]
 [<CommonParameters>]
```

## DESCRIPTION
**Relevant for:** AIP unified labeling client only

The **New-AIPCustomPermissions** cmdlet creates an ad-hoc protection policy object for custom permissions that you store as a variable and then use to protect a file or files when you run the labeling cmdlet, [Set-AIPFileLabel](./Set-AIPFileLabel.md). If the label that is applied is configured for protection settings, the custom permissions from the ad-hoc protection policy replace the protection settings from the label.

## EXAMPLES

### Example 1 - Create an ad-hoc protection policy object for a single user
```
PS C:\> $permissions = New-AIPCustomPermissions -Users user1@contoso.com -Permissions Viewer
```

This command creates an ad-hoc protection policy object that grants user1 from contoso.com usage rights from the Reviewer permissions and stores this policy in a variable named permissions. This ad-hoc protection policy can then be used to apply protection to a file or files.

There is no output displayed for this command.

### Example 2 - Create an ad-hoc protection policy object for multiple users and that has an expiration date
```
PS C:\> $permissions = New-AIPCustomPermissions -Users user1@contoso.com, user2@vanarsdel.com -Permissions Reviewer -ExpirationDate (Get-Date -Month 1 -Day 1 -Year 2020)
```

This command creates an ad-hoc protection policy object that grants users from different organizations usage rights from the Reviewer permissions, and also applies an expiration date. The ad-hoc protection policy object is stored in a variable named permissions, which can then be used to apply this protection to a file or files.

There is no output displayed for this command.

## PARAMETERS

### -ExpirationDate
Specifies an expiration date for the ad-hoc protection policy.

After this expiry date, the specified users will no longer be able to access the file or files. However, the owner and a super user can always access the file, even after the expiry period is reached.

```yaml
Type: DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Permissions
Specifies a permissions level that groups usage rights that are typically used together. Use this parameter and the *Users* parameter to grant usage rights to specified users.

To see which individual usage rights are included in each of the permissions levels, see [Rights included in permission levels](/azure/information-protection/configure-usage-rights#rights-included-in-permissions-levels).

```yaml
Type: Permissions
Parameter Sets: (All)
Aliases:
Accepted values: Viewer, Reviewer, CoAuthor, CoOwner

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Users
Specifies users who will have rights to use the file or files. Use this parameter and the *Permission* parameter to grant rights to specified users or groups. 

```yaml
Type: String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

### None

## OUTPUTS

### System.Object
## NOTES

## RELATED LINKS

[Set-AIPFileLabel](Set-AIPFileLabel.md)