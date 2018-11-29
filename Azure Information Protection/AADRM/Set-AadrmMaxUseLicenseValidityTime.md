---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkID=529559
schema: 2.0.0
ms.assetid: E04D855C-C9AF-42DA-A1B4-9D51FE4045D9
---

# Set-AadrmMaxUseLicenseValidityTime

## SYNOPSIS
Sets the maximum validity time for Rights Management use licenses.

## SYNTAX

```
Set-AadrmMaxUseLicenseValidityTime [-MaxUseLicenseValidityTime] <UInt16> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
[!INCLUDE [AADRM is deprecated](../includes/aadrm-deprecated.md)]

The **Set-AadrmMaxUseLicenseValidityTime** cmdlet sets the maximum validity time for use licenses that Azure Rights Management grants for your organization when it protects files and email messages. The default value is 30 days.

You must use PowerShell to set this configuration at the organization level; you cannot do this configuration by using a management portal.

A use license is a per-document certificate that is granted to a user who opens a protected file or email message. This certificate contains that user's rights for the file or email message and the encryption key that was used to encrypt the content, as well as additional access restrictions defined in the document's policy.

When the validity period of the use license is expired for a file or email message, the user credentials must be submitted to Azure RMS again to open that content. If the credentials are cached, the user is not prompted, and this happens in the background but an Internet connection is still required to send the cached credentials. 

For example, if a user shares a protected file by email and the protected file has the default use license validity period of 30 days:

- Anna opens the file immediately, authenticates to Azure RMS, and reads the file. The following day, she reads the file again but does not have an Internet connection. Because the use license validity period has not expired, she can read the file. She accesses the file again 30 days later when she has an Internet connection and re-authenticates with Azure RMS, so she could now continue to read the file without authenticating again for a further 30 days.

- John does not open the file for 31 days. When he does, he has Internet access that lets him authenticates to Azure RMS, and he can then open and read the file. John can continue to re-open and read the file even if he does not have an Internet connection again for a further 30 days.

- Amelia opens the file a week after it arrives, and then does not open it again for two months. When she tries to open it this second time, she does not have Internet access and so she cannot open the file.

This setting at the tenant level can be overridden by a more restrictive setting in a Rights Management template because of the *LicenseValidityDuration* parameter in the [Set-AadrmTemplateProperty](./Set-AadrmTemplateProperty.md) and [Add-AadrmTemplate](./Add-AadrmTemplate.md) cmdlets, which administrators can also set in the Azure portal by configuring the offline access option, Number of days the content is available without an Internet connection.

This setting can also be overridden by a user for a document when they use the RMS sharing application, and select the "Allow me to instantly revoke access to these documents" option, which effectively sets the use license validity time to 0. There is no equivalent setting for Azure Information Protection client. When there are different values like this, Azure RMS uses the most restrictive value.

Because the use license validity time can be overridden with more restrictive values, when you change the default value by using this cmdlet, choose a maximum value that best suits your organization. 

Decide on the best compromise between security and offline access for longer periods:

- The lower the value, the more often users will be authenticated (which requires an Internet connection) but is a more secure setting because users will more quickly pick up changes such as the document has been revoked or the usage rights have changed for the protected document.

- The higher the value, the less frequently users will be authenticated (and can continue to access protected documents even without an Internet connection) and is less secure because it will take longer for users to pick up changes such as the document has been revoked or the usage rights have changed for the protected document.

## EXAMPLES

### Example 1: Set the maximum validity time
```
PS C:\>Set-AadrmMaxUseLicenseValidityTime 60
```

This command sets the maximum validity time for use licenses to be 60 days.

## PARAMETERS

### -Force
Indicates that this cmdlet sets the value for the maximum validity time for use licenses without prompting you for confirmation.

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

### -MaxUseLicenseValidityTime
Specifies the maximum validity time (0 - 65535) for use licenses in days.

```yaml
Type: UInt16
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
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
Shows what would happen if the cmdlet runs. The cmdlet is not run.

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

[Get-AadrmMaxUseLicenseValidityTime](./Get-AadrmMaxUseLicenseValidityTime.md)
