---
external help file: AIP.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=841546
schema: 2.0.0
ms.assetid: 835E47FE-7E1F-418D-843C-3B2FB2F7FF96
---

# Get-RMSTemplate

## SYNOPSIS
Gets a list of RMS templates.

## SYNTAX

```
Get-RMSTemplate [-RmsServer <String>] [-Force] [-Culture <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Get-RMSTemplate** cmdlet gets a list of templates from your Rights Management deployment (AD RMS or Azure RMS), which can then be used to protect files. Use this cmdlet to identify the template ID of the template that you want to use.

## EXAMPLES

### Example 1: Get a list of templates
```
PS C:\>Get-RMSTemplate
TemplateId        : {0e36001f-a341-49f2-aad5-be4937cd391d}

CultureInfo       : en-US
Description       : This content is proprietary information intended for internal users only. This content cannot be modified.

Name              : Contoso, Ltd - Confidential View Only

IssuerDisplayName : Contoso, Ltd

FromTemplate      : True



TemplateId        : {e6ee2481-26b9-45e5-b34a-f744eacd53b0}

CultureInfo       : en-US

Description       : This content is proprietary information intended for internal users only. This content can be modified but cannot be copied and printed.

Name              : Contoso, Ltd - Confidential

IssuerDisplayName : Contoso, Ltd

FromTemplate      : True

TemplateId        : {1e9f7d73-51f8-4e5b-93b5-696d252697c3}

CultureInfo       : en-US

Description       : This content is restricted to the Sales & Marketing department, read and print

Name              : Sales and Marketing - Read and Print Only

IssuerDisplayName : Contoso, Ltd

FromTemplate      : True
```

This command gets a list of templates that your computer previously downloaded from Azure RMS or your default AD RMS deployment.
From the output, copy the TemplateId value for the template that you want to use to protect files.

### Example 2: Get a list of templates for a specific locale (French)
```
PS C:\>Get-RMSTemplate -Culture "fr-fr"
TemplateId        : {e6ee2481-26b9-45e5-b34a-f744eacd53b0}
CultureInfo       : fr-FR
Description       : Ce document contient des informations confidentielles destinees a un usage interne uniquement. Il
                    peut etre modifie, mais ne peut etre ni copie ni imprime.
Name              : Contoso, Ltd - Confidentiel
IssuerDisplayName : Contoso, Ltd
FromTemplate      : True

TemplateId        : {1e9f7d73-51f8-4e5b-93b5-696d252697c }
CultureInfo       : fr-FR
Description       : Ce document contient des informations confidentielles destinees a un usage interne uniquement. Il
                    ne peut pas etre modifie.
Name              : Contoso, Ltd - Affichage confidentiel uniquement
IssuerDisplayName : Contoso, Ltd
FromTemplate      : True
```

This command gets a list of templates for the French locale.

## PARAMETERS

### -Culture
Specifies the templates to load by locale by using a language-region code-pair, where language is an ISO-639 language code and region is an ISO 3166-1 country or region identifier (for instance, en-us, fr-fr, or es-es). If you do not specify this parameter, or you specify this parameter without a value, all available language versions for the same template are returned.

To load templates for a different locale, specify it as a value with this parameter by using the language-region code-pair. For example, if you are in Canada and your current system locale is set to English but you want to see the template names and description in French, specify `-Culture "fr-fr"`.

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

### -Force
Indicates that this cmdlet downloads the templates directly from the Azure RMS service or from the AD RMS server, instead of using the cached templates on your computer that might be out of date.

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

### -RmsServer
Specifies the name of the RMS server or cluster to get the templates if you are running AD RMS. 

This parameter is not applicable to Azure RMS.

If you don't specify a server, the cmdlet gets the list of templates from your computer's default Rights Management deployment by using service discovery. Typically, you need to specify this parameter only if you have multiple deployments of AD RMS or service discovery cannot find an AD RMS server. If you are not sure what server name to specify, use the [Get-RMSServer](./Get-RMSServer.md) cmdlet. 


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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## RELATED LINKS

[Get-RMSServer](./Get-RMSServer.md)

[Set-AIPFileLabel](./Set-AIPFileLabel.md)

[Protect-RMSFile](./Protect-RMSFile.md)
