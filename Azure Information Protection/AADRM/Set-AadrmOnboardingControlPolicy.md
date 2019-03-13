---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=521419
schema: 2.0.0
ms.assetid: AC10D692-604D-40A3-94BE-AAA5008BF9D8
---

# Set-AadrmOnboardingControlPolicy

## SYNOPSIS
Sets the user on-boarding control policy for Rights Management.

## SYNTAX

```
Set-AadrmOnboardingControlPolicy [-Force] -UseRmsUserLicense <Boolean> [-SecurityGroupObjectId <Guid>]
 [-Scope <OnboardingControlPolicyScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Set-AadrmOnboardingControlPolicy** cmdlet sets the policy that controls user on-boarding for Azure Rights Management. This cmdlet supports a gradual deployment by controlling which users in your organization can protect content by using Azure Rights Management.

You must use PowerShell to set this configuration; you cannot do this configuration by using a management portal.

This control can be based on assigned user licenses for the service or membership in a designated security group. You can also define whether the policy applies to just mobile devices, just Windows clients, or mobile devices and Windows clients.

If you use the assigned license option, you can assign licenses to users by using the Microsoft 365 admin center or by using Azure PowerShell and the [Set-MsolUserLicense](https://docs.microsoft.com/en-us/powershell/module/msonline/set-msoluserlicense?view=azureadps-1.0) cmdlet from the Azure AD PowerShell administration module. You can also use the [Get-MsolAccountSku](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolaccountsku?view=azureadps-1.0) cmdlet to obtain the different types of licenses that you can assign in your organization.

If you use the group membership option, you must specify a security group, which does not have to be mail-enabled and it can contain other groups. To specify the group, use the group GUID. For more information about the user and group requirements and how to find the group GUID, see [Preparing users and groups for Azure Information Protection](https://docs.microsoft.com/information-protection/plan-design/prepare).

For more information about the Azure AD PowerShell cmdlets, see [Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azure/overview?view=azureadps-2.0).

Note: This cmdlet does not stop users from consuming protected content or prevent administrators from configuring services for Azure Rights Management (for example, Exchange Online transport rules, SharePoint protected libraries, Windows Server FCI). Instead, it is designed for user applications such as Office, so that users do not see the options or templates to use Azure Rights Management protection.

## EXAMPLES

### Example 1: Restrict Azure Rights Management to users who have a license and are members of a specified group
```
PS C:\> Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $True -SecurityGroupObjectId "fba99fed-32a0-44e0-b032-37b419009501" -Scope All
```

This command configures the Azure Rights Management service to allow only users who have a license to use Azure Rights Management to protect content. Further, the command requires users to be members of the security group with the specified object ID. The restriction applies to Windows clients and mobile devices.

### Example 2: Restrict Azure Rights Management to users who are members of a specified group
```
PS C:\> Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False -SecurityGroupObjectId "fba99fed-32a0-44e0-b032-37b419009501" -Scope All
```

This command allows only users that are members of the security group with the specified object ID to protect content by using Azure Rights Management. The command applies to Windows clients and mobile devices.

### Example 3: Restrict Azure Rights Management to users who have a license
```
PS C:\> Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $True -Scope All
```

This command allows only users who have a license assigned to protect content by using Azure Rights Management. The command applies to Windows clients and mobile devices.

### Example 4: Do not restrict Azure Rights Management for users
```
PS C:\> Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False -Scope All
```

This command allows all users to protect content by using Azure Rights Management. The command applies to Windows clients and mobile devices.

## PARAMETERS

### -Force
Indicates that this cmdlet configures the on-boarding control policy even if there is already an on-boarding control policy for the organization.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scope
Specifies the types of applications to which the on-boarding policy applies.

Valid values are:

- All
- WindowsApp
- MobileApp

```yaml
Type: OnboardingControlPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: All, WindowsApp, MobileApp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SecurityGroupObjectId
Specifies the object ID of a security group in Azure AD. If you try to specify the object ID of a distribution group, you will see an error.

The specified group restricts which users can protect content by using Rights Management. If you also enable license enforcement, only users that have a license assigned and are members of this specified group can protect content by using Azure Rights Management.

You can use this parameter to implement a phased deployment of Azure Rights Management even if all users have a license assigned to them.

```yaml
Type: Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseRmsUserLicense
Specifies whether users without a license assigned to them can use Azure Rights Management to protect content. Users can always use Azure Rights Management to consume protected content regardless of this setting and their license assignment.

```yaml
Type: Boolean
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
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
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-AadrmOnboardingControlPolicy](./Get-AadrmOnboardingControlPolicy.md)
