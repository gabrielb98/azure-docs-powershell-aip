---
external help file: AIPService.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=2045236
schema: 2.0.0
ms.assetid: AC10D692-604D-40A3-94BE-AAA5008BF9D8
---

# Set-AipServiceOnboardingControlPolicy

## SYNOPSIS
Sets the user on-boarding control policy for Azure Information Protection.

## SYNTAX

```
Set-AipServiceOnboardingControlPolicy [-Force] -UseAIPServiceUserLicense <Boolean> [-SecurityGroupObjectId <Guid>]
 [-Scope <OnboardingControlPolicyScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Set-AipServiceOnboardingControlPolicy** cmdlet sets the policy that controls user on-boarding for Azure Information Protection. This cmdlet supports a gradual deployment by controlling which users in your organization can protect content by using Azure Information Protection.

You must use PowerShell to set this configuration; you cannot do this configuration by using a management portal.

This control can be based on assigned user licenses for the service or membership in a designated security group. You can also define whether the policy applies to just mobile devices, just Windows clients, or mobile devices and Windows clients.

If you use the assigned license option, you can assign licenses to users by using the Office 365 admin center or by using Azure PowerShell and the [Set-MsolUserLicense](https://docs.microsoft.com/en-us/powershell/module/msonline/set-msoluserlicense?view=azureadps-1.0) cmdlet from the Azure AD PowerShell administration module. You can also use the [Get-MsolAccountSku](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolaccountsku?view=azureadps-1.0) cmdlet to obtain the different types of licenses that you can assign in your organization.

If you use the group membership option, you must specify a security group, which does not have to be mail-enabled and it can contain other groups. To specify the group, use the group GUID. For more information about the user and group requirements and how to find the group GUID, see [Preparing users and groups for Azure Information Protection](https://docs.microsoft.com/information-protection/plan-design/prepare).

For more information about the Azure AD PowerShell cmdlets, see [Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azure/overview?view=azureadps-2.0).

Note: This cmdlet does not stop users from consuming protected content or prevent administrators from configuring services for Azure Information Protection (for example, Exchange Online mail flow rules or SharePoint protected libraries). Instead, it is designed for user applications such as Office, so that users do not see the options or templates to use Azure Information Protection.

## EXAMPLES

### Example 1: Restrict Azure Information Protection to users who have a license and are members of a specified group
```
PS C:\> Set-AipServiceOnboardingControlPolicy -UseAIPServiceUserLicense $True -SecurityGroupObjectId "fba99fed-32a0-44e0-b032-37b419009501" -Scope All
```

This command configures Azure Information Protection to allow only users who have an Azure Rights Management license to use Azure Information Protection to protect content. Further, the command requires users to be members of the security group with the specified object ID. The restriction applies to Windows clients and mobile devices.

### Example 2: Restrict Azure Information Protection to users who are members of a specified group
```
PS C:\> Set-AipServiceOnboardingControlPolicy -UseAIPServiceUserLicense $False -SecurityGroupObjectId "fba99fed-32a0-44e0-b032-37b419009501" -Scope All
```

This command allows only users that are members of the security group with the specified object ID to protect content by using Azure Information Protection. The command applies to Windows clients and mobile devices.

### Example 3: Restrict Azure Information Protection to users who have an Azure Rights Management license
```
PS C:\> Set-AipServiceOnboardingControlPolicy -UseAIPServiceUserLicense $True -Scope All
```

This command allows only users who have an Azure Rights Management license assigned to protect content by using Azure Information Protection. The command applies to Windows clients and mobile devices.

### Example 4: Do not restrict Azure Information Protection for users
```
PS C:\> Set-AipServiceOnboardingControlPolicy -UseAIPServiceUserLicense $False -Scope All
```

This command allows all users to protect content by using Azure Information Protection. The command applies to Windows clients and mobile devices.

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

The specified group restricts which users can protect content by using Azure Information Protection. If you also enable license enforcement, only users that have an Azure Rights Management license assigned and are members of this specified group can protect content by using Azure Information Protection.

You can use this parameter to implement a phased deployment of Azure Information Protection even if all users have an Azure Rights Management license assigned to them.

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

### -UseAIPServiceUserLicense
Specifies whether users without an Azure Rights Management license assigned to them can use Azure Information Protection to protect content. Users can always use Azure Information Protection to consume protected content regardless of this setting and their license assignment.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-AipServiceOnboardingControlPolicy](./Get-AipServiceOnboardingControlPolicy.md)
