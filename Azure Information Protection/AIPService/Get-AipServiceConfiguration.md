---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 57CD3929-8922-43C2-9056-B5543F1FD0BB
online version: https://go.microsoft.com/fwlink/?linkid=2044949
schema: 2.0.0
---

# Get-AipServiceConfiguration

## SYNOPSIS
Gets the Azure Information Protection configuration of your tenant.

## SYNTAX

```
Get-AipServiceConfiguration [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceConfiguration** cmdlet gets the current Azure Information Protection configuration of your tenant for the protection service.

You must use PowerShell to see a full list of protection configuration values for your tenant; you cannot get this configuration by using a management portal.

## EXAMPLES

### Example 1: Display Azure Information Protection configuration for the protection service
```
PS C:\>Get-AipServiceConfiguration
BPOSId                                    : 9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a

AzureInformationProtectionServiceId                 : 5c6bb73b-1038-4eec-863d-49bded473437

LicensingIntranetDistributionPointUrl     : https://5c6bb73b-1038-4eec-863d-49bded473437.aipservice.na.aadrm.com/_wmcs/licensing

LicensingExtranetDistributionPointUrl     : https://5c6bb73b-1038-4eec-863d-49bded473437.aipservice.na.aadrm.com/_wmcs/licensing

CertificationIntranetDistributionPointUrl : https://5c6bb73b-1038-4eec-863d-49bded473437.aipservice.na.aadrm.com/_wmcs/certification

CertificationExtranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.aipservice.na.aadrm.com/_wmcs/certification

AdminConnectionUrl                        : https://admin.na.aadrm.com/admin/admin.svc/Tenants/5c6bb73b-1038-4eec-863d-49bded473437

AdminV2ConnectionUrl                      : https://admin.na.aadrm.com/adminV2/admin.svc/Tenants/5c6bb73b-1038-4eec-863d-49bded473437

OnPremiseDomainName                       :

Keys                                      : {c46b5d49-1c4c-4a79-83d1-ec12a25f3134}

CurrentLicensorCertificateGuid            : c46b5d49-1c4c-4a79-83d1-ec12a25f3134

Templates                                 : { c46b5d49-1c4c-4a79-83d1-ec12a25f3134,

                                            5c6d36g9-c24e-4222-7786e-b1a8a1ecab60}

FunctionalState                           : Enabled

SuperUsersEnabled                         : Disabled

SuperUsers                                : {admin3@contoso.com, admin4@contoso.com}

AdminRoleMembers                          : {Global Administrator -> 5834f4d6-35d2-455b-a134-75d4cdc82172,

                                            ConnectorAdministrator -> 5834f4d6-35d2-455b-a134-75d4cdc82172}

KeyRolloverCount                          : 0

ProvisioningDate                          : 1/30/2014 9:01:31 PM

IPCv3FunctionalState               		  : Enabled

DevicePlatformState                       : {Windows -> True, WindowsStore -> True, WindowsPhone -> True, Mac ->

FciEnabledForConnectorAuthorization       : True

DocumentTrackingFeatureState              : Enabled
```

This command displays the current protection configuration for your tenant.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS
