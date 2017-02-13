---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
ms.assetid: BE20B1AF-4D47-4182-A46A-2FB0AB504A93
online version: http://go.microsoft.com/fwlink/?LinkID=400629
schema: 2.0.0
---

# New-AadrmRightsDefinition

## SYNOPSIS
Creates a Rights Definition object for Rights Management.

## SYNTAX

```
New-AadrmRightsDefinition [-EmailAddress <String>] [-DomainName <String>]
 -Rights <System.Collections.Generic.List`1[System.String]> [<CommonParameters>]
```

## DESCRIPTION
The **New-AadrmRightsDefinition** cmdlet creates a **Rights Definition** object that you store as a variable and then use to create or update a custom Rights Management template when you use the [Add-AadrmTemplate](./Add-AadrmTemplate.md) or [Set-AadrmTemplateProperty](./Set-AadrmTemplateProperty.md) cmdlet.

A **Rights Definition** object expresses the rights that users have to content that Azure Rights Management protects. You can specify a user, a group, or all users in an organization.

Similar configuration can also be done when you create or configure a custom template in the Azure classic portal, but this cmdlet offers more fine-grained control.

Tip: You can this cmdlet to enable secure collaboration with other organizations. For example, provide an external group VIEW and DOCEDIT rights to collaborate on a joint project. Or, provide VIEW rights to all users in a partner organization.

For more information about custom templates, including how to configure them in the Azure classic portal, see "Configuring custom templates for Azure Rights Management" (https://docs.microsoft.com/rights-management/deploy-use/configure-custom-templates) on the Microsoft documentation site.

## EXAMPLES

### Example 1: Create a rights definition object for a user
```
PS C:\>$R1 = New-AadrmRightsDefinition -EmailAddress "ElisaDaugherty@Contoso.com" -Rights "VIEW","DOCEDIT"
```

This command creates a rights definition object for the specified user and stores this policy in a variable named R1, which can then be used to create or update a custom template. 

The command includes the rights VIEW and DOCEDIT for a user in the Contoso organization.

### Example 2: Create a rights definition object for all members
```
PS C:\>$R2 = New-AadrmRightsDefinition -DomainName "Contoso.com" -Rights "VIEW"
```

This command creates a rights definition object for the Contoso organization and stores this policy in a variable named R2, which can then be used to create or update a custom template. The command includes the VIEW right for all users in the Contoso organization.

## PARAMETERS

### -DomainName
Specifies a domain name for your organization or another organization, to be used for granting rights when you create or update a custom template. When an organization has more than one domain, it does not matter which domain name you specify; users from all verified domains for that organization are automatically included. 

Specify one domain name only for all users in an organization; to grant rights to more than one organization, create another Rights Definition object.


```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EmailAddress
Specifies the email address of a user or group. The user or group can be internal to your organization, or external.

The cmdlet associates the rights that the *Rights* parameter specifies to the user or group that the address specifies.

Tip: If you want to specify all users in your organization or all users in another organization, use the DomainName parameter. 

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Rights
Specifies a list of rights. The list contains one or more of the following:

- **VIEW**: Interpreted by most applications as allowed to present the data on the screen.

- **EDIT**: Interpreted by most applications as allowed to modify content in the document and save it.

- **DOCEDIT**: Interpreted by most applications as allowed to modify the content of the document.

- **EXTRACT**: Interpreted by most applications as allowed to copy the content to the clipboard or otherwise extract the content in unencrypted form.

- **OBJMODEL**: Interpreted by most applications as allowed to access the document programmatically; for example, by using macros.

- **EXPORT**: Interpreted by most applications as allowed to save the file in unencrypted form. For example, this right allows you to save in a different file format that does not support protection.

- **PRINT**: Interpreted by most applications as allowed to print the document.

- **OWNER**: User has all rights on the document, including the ability to remove protection.

- **FORWARD**: Interpreted by most applications as allowed to forward an email message, and to add recipients to the To and Cc lines.

- **REPLY**: Interpreted by most applications as allowed to select reply to an email message, without allowing changes in the To or Cc lines.

- **REPLYALL**: Interpreted by most applications as allowed to reply to all recipients of an email message, but does not allow the user to add recipients to the To or Cc lines.

Note: For clarity, the documentation and display text from the module shows these rights as all upper-case letters. However, the values are not case-sensitive and you can specify them in lower or upper case.

For more information about the usage rights, see [Configuring usage rights for Azure Rights Management](https://docs.microsoft.com/rights-management/deploy-use/configure-usage-rights) (https://docs.microsoft.com/rights-management/deploy-use/configure-usage-rights) on the Microsoft documentation site.

```yaml
Type: System.Collections.Generic.List`1[System.String]
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-AadrmTemplate](./Add-AadrmTemplate.md)

[Set-AadrmTemplateProperty](./Set-AadrmTemplateProperty.md)

[Azure Rights Management](https://docs.microsoft.com/rights-management/deploy-use/configure-usage-rights)
